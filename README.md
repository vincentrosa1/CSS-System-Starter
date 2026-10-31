# CSS Architecture Starter

Module 2 practice. I used the CSS
Architecture Starter page and rebuilt
styles.css as a layered, token-based
system.

## Files

- `index.html`: starter page, plus
  utility classes and hidden link text
- `styles.css`: layered CSS system

## Layer order

reset, base, layout, components,
utilities, overrides

- **reset** clears browser defaults.
- **base** holds my tokens and element
  styles (body, headings, links, focus).
- **layout** handles the header, hero,
  sections, card grid, and footer.
- **components** are the eyebrow,
  button, card, callout, form, and nav.
- **utilities** come after components so
  a utility class always wins without
  !important.
- **overrides** has one intentional
  exception: turning off the button's
  press motion for reduced-motion users.

Print styles sit outside the layers on
purpose. Unlayered CSS beats every layer,
so print rules always win.

## Three token decisions

1. **Two-tier colors.** Raw palette
   tokens (`--clay-600`) map to role
   tokens (`--color-action`). Components
   only use role tokens, so recoloring
   the site means changing one mapping.
2. **Split focus tokens.** Focus color,
   width, and offset are separate, so I
   can change just the color in one
   section of the page.
3. **One spacing scale.** Every padding
   and gap uses `--space-2xs` through
   `--space-2xl`, so there are no one-off
   spacing values to hunt down.

## States

- Visible `:focus-visible` outline on
  every focusable element
- Current page: the nav link with
  `aria-current="page"` gets a bold clay
  underline
- Hover and active states on buttons
  and nav links

## Utilities

- `.flow`: even spacing between stacked
  children
- `.measure`: caps line length at 65ch
- `.text-center`: centers short text
- `.visually-hidden`: hides text visually
  but keeps it for screen readers

## Where it got easier to maintain

Clay text on the green hero failed
contrast. Instead of overriding the
eyebrow, links, button, and focus ring
one by one, I remapped five role tokens
inside `.hero`. Every component in the
hero picked up readable colors with no
new selectors.

## Print

Hides the nav, buttons, and form, drops
backgrounds and shadows, switches text
to black, and keeps cards from splitting
across pages.


## AI Usage

No AI was used. 