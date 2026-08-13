# redmondlab.org

Static site for the Redmond Lab, Weill Cornell Medicine.
Plain HTML and one CSS file — no build step, no dependencies, no framework.

## Editing

Open any `.html` file and edit it. To preview, just open `index.html` in a browser,
or serve the folder:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000
```

Every page carries its own copy of the header/footer (there is no templating).
If you change a nav link, change it in all five pages.

## Files

| File | Purpose |
|---|---|
| `index.html` | Home — intro and the four research themes |
| `research.html` | Themes in depth |
| `publications.html` | Selected + full publication list by year |
| `people.html` | PI, current/past members, collaborators, recruiting |
| `contact.html` | Contact details, data/code pointers |
| `style.css` | All styling; light and dark via `prefers-color-scheme` |
| `CNAME` | Custom domain for GitHub Pages — must contain `redmondlab.org` |

## Outstanding TODOs

Search the HTML for `TODO` — each marks something deliberately left blank rather
than guessed:

- `people.html` — roles/titles for Ryan Nachman, Jenny Huang, Sean Houghton
- `people.html` — confirm collaborator affiliations, and that each is happy to be listed
- `people.html` — optional PI bio paragraph
- `contact.html` — building/room in the address block
- `contact.html` — GEO accessions and GitHub links for published data

The publication list was compiled from the Weill Cornell VIVO profile and lists
title/journal/year only. If you want full author lists, they need adding by hand or
exporting from Google Scholar.

## Deploying to GitHub Pages

1. Create a **public** repo under the `redmondlab` org (e.g. `redmondlab.org`).
2. Push this folder to it.
3. Repo → Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder `/ (root)`.
4. Settings → Pages → Custom domain: `redmondlab.org`, then tick **Enforce HTTPS**
   once the certificate is issued (can take up to ~24h).

## DNS at GoDaddy

Verified against GitHub's docs on 2026-08-13. In GoDaddy's DNS manager for
`redmondlab.org`, add:

**Four A records**, host `@`:

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```

**Four AAAA records** (optional, for IPv6), host `@`:

```
2606:50c0:8000::153
2606:50c0:8001::153
2606:50c0:8002::153
2606:50c0:8003::153
```

**One CNAME record**, host `www`, pointing to `redmondlab.github.io`.

Delete any GoDaddy "Parked"/forwarding A record for `@` first, or it will conflict.
DNS changes typically propagate in minutes but can take a few hours.

Check propagation with:

```sh
dig +short redmondlab.org
dig +short www.redmondlab.org
```
