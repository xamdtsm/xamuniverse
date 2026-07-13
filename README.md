# Archive — A Universe of Notes

A single-file, no-build website for cataloguing your Google Drive notes by topic.
Black-and-white, noir/space aesthetic — a starfield background with faint
constellation lines, comic-poster headline type, and typewriter body text.
Every topic is a "case file" card; click it open to reveal the Drive links
filed inside.

## How it works

Everything lives in **one file**: `index.html`. There is no build step,
no framework, no dependencies to install — open it in a browser and it works.

## How to add your own notes

Open `index.html` and search for this comment block near the top of the
`<script>` section:

```
YOUR DATA — THIS IS THE ONLY SECTION YOU NEED TO TOUCH
```

Right below it is the `TOPICS` array. Each topic looks like this:

```js
{
  title: "Topic name shown on the card",
  desc:  "One short line describing this topic (optional, can be '')",
  links: [
    { title: "Name of the note / file", url: "https://drive.google.com/..." },
    { title: "Another note in this topic", url: "https://drive.google.com/..." }
  ]
}
```

**To add a new topic:** copy one whole `{ ... }` block, paste it before the
closing `];`, and edit the `title`, `desc`, and `links`.

**To add a new note inside an existing topic:** copy one line inside that
topic's `links: [ ... ]` array and change the `title` and `url`.

**To get a Drive link:** in Google Drive, right-click the file or folder →
*Get link* → *Copy link*, then paste it as the `url`.

That's the entire workflow — save the file, refresh the page, done.

## Deploying it on GitHub Pages

1. Create a new repository (or use an existing one) and push this file
   as `index.html` at the root (or inside a `/docs` folder).
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to "Deploy from a branch",
   pick your branch (usually `main`) and the folder (`/root` or `/docs`).
4. Save — GitHub will give you a live URL, typically
   `https://<your-username>.github.io/<repo-name>/`.
5. Every time you edit the `TOPICS` array and push, the live site updates
   automatically within a minute or two.

## Customizing the look

Near the top of the `<style>` block there's a `:root { ... }` section with
six named variables (`--void`, `--ink`, `--paper`, `--dim`, `--line`,
`--halo`). Changing these six values re-tones the entire site — no need to
hunt through the rest of the CSS.

## Notes on structure

- The search bar filters by topic name **and** by individual note titles —
  searching a note title auto-expands just that topic and shows the
  matching notes.
- An empty `links: []` array is fine — the card will show "case file empty"
  until you file something in it.
- The starfield is plain `<canvas>` with no external libraries, so it will
  keep working indefinitely with no maintenance.
