# Daylight website

The lightweight landing page for **[Daylight](https://daylightcalendar.com/)**, a collection of calendar tools for Home Assistant.

The site introduces two independent projects:

| Project | Documentation | Source |
| --- | --- | --- |
| Daylight Calendar Card | [card.daylightcalendar.com](https://card.daylightcalendar.com/) | [daylight-calendar-card](https://github.com/superdingo101/daylight-calendar-card) |
| Daylight Calendar Import | [import.daylightcalendar.com](https://import.daylightcalendar.com/) | [daylight-calendar-import](https://github.com/superdingo101/daylight-calendar-import) |

## How it works

This repository is a **static, dependency-free HTML website**. GitHub Pages serves `index.html` directly. No build tooling, JavaScript framework, backend, hosted Daylight account, or paid service is required.

### Preview locally

Open `index.html` in a browser, or run a simple local server:

```sh
python3 -m http.server 8000
```

Then visit [http://localhost:8000](http://localhost:8000).

### Images

The homepage uses the two project screenshots provided for the site:

- Calendar Card: the existing Week View image hosted as an attachment in the [Calendar Card README](https://github.com/superdingo101/daylight-calendar-card).
- Calendar Import: the matching flyer-to-review image in the [Calendar Import documentation PR](https://github.com/superdingo101/daylight-calendar-import/pull/251).

Both are referenced through public, fixed GitHub asset URLs rather than copied into this repository. The Calendar Import image uses a commit-pinned URL. If either source asset moves or becomes unavailable, move an optimized copy into this repository and update its `img src` in `index.html`.

## Deploy with GitHub Pages

1. Merge the homepage pull request into `main`.
2. Open **Settings → Pages** in this repository.
3. Under **Build and deployment**, select **Deploy from a branch**, branch **main**, folder **/(root)**, and save.
4. Verify the preview at **https://superdingo101.github.io/daylight-website/** before making DNS changes. All site asset paths are relative or absolute, so this repository preview works.
5. In **Settings → Pages → Custom domain**, enter **daylightcalendar.com** and save.
6. In Squarespace DNS, remove the existing apex-domain forwarding rule to the old docs site. Point the apex (`@`) to the GitHub Pages A records:

   ```text
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```

7. Add `www` as a CNAME to `superdingo101.github.io` (and ensure any conflicting `www` records/forwarding are removed).
8. Once DNS and the certificate have propagated, enable **Enforce HTTPS** in GitHub Pages. Verify both apex and `www` resolve securely.

**Do not alter** the Mintlify `import` subdomain, unrelated DNS records, or email configuration. For Calendar Card, first configure the new `card.daylightcalendar.com` custom domain in Mintlify and verify it works, then replace the old `docs.daylightcalendar.com` mapping with a permanent path-preserving redirect to `card.daylightcalendar.com`.

Domain and certificate controls live in GitHub and Squarespace, not in this repository; merging alone does **not** switch the production domain.

## Editing

Edit `index.html` for the copy, product links, styling, and screenshot URLs. The inline CSS keeps deployment simple. `favicon.svg` contains a small calendar-and-spark mark.

This website is separate from both products and their Mintlify documentation. It advertises only functionality currently available publicly; hosted Daylight services are not advertised here.

## License

See [LICENSE](LICENSE).
