# claude-ux-marketplace

Personal Claude Code plugin marketplace. It contains no skill files of its own:
each plugin entry in `.claude-plugin/marketplace.json` points at an upstream
GitHub repository, so updates come straight from the upstream author.

## Plugins

| Plugin | Upstream | Skills |
|---|---|---|
| `edenspiekermann-skills` | [edenspiekermann/Skills](https://github.com/edenspiekermann/Skills) | `audit-design-system`, `fix-design-system-finding`, `apply-design-system` |

## Install

```
/plugin marketplace add YOUR-GITHUB-LOGIN/claude-ux-marketplace
/plugin install edenspiekermann-skills@claude-ux-marketplace
```

Then open `/plugin`, go to the Marketplaces tab and turn on auto-update for
this marketplace (it is off by default for third-party marketplaces).

## Notes

- No `ref` or `sha` is set, so the plugin follows the upstream default branch.
  To pin a reviewed version, add `"sha": "<commit>"` to the plugin's `source`
  in `marketplace.json`.
- No `skills` list is set, so skills added or renamed upstream are picked up
  automatically. If you want to disable one, add an explicit `skills` list.
- `fix-design-system-finding` and `apply-design-system` write to Figma. Run
  them on a copy or a branch of the file.
- After installing, check that all three skills show up. If one is missing,
  add an explicit `skills` list with the paths from the upstream repository.

## Adding more plugins

Add another object to the `plugins` array with its own `name` and `source`
(`{ "source": "github", "repo": "owner/repo" }`).
