# JewelInYou — Aabharan

**A bride-led, family-connected jewellery shopping experience.**

JewelInYou is an early interactive prototype exploring a connected journey between a jewellery buyer, her family and showroom staff.

## Run the prototype

The prototype is a static HTML application. Open `index.html` locally, or deploy the repository to a static host such as Cloudflare Pages or GitHub Pages.

- No build step is required.
- The catalogue uses illustrative SVG artwork and clearly labelled sample prices.
- Create a room, browse categories, add pieces to a look, try the demo outfit preview, create a family-look card, and explore the shop and family views.
- A QR code is generated from the deployed page URL and the room code.

## Important prototype limitations

This is **not yet a production-ready multi-user application**.

- Room state, selections, votes and comments are stored in the current browser's local storage.
- The room QR/link identifies a room, but **does not synchronise activity across different devices** until a shared backend is implemented and configured.
- Sample designs, stock labels and prices are fictional demo content; do not use them for purchasing decisions.
- The try-on canvas is a visual prototype. It does not guarantee accurate product scale, fit, drape or photo-realistic outfit transformation.
- WhatsApp sharing currently opens a prefilled text message. The user may need to attach a saved image separately.
- Do not upload sensitive photographs on shared/public devices.

## Product principles

1. **The bride owns the room.** She decides which looks are shared and controls her shortlist.
2. **Family participates without taking control.** Members can comment and vote; their votes do not automatically change the bride's choices.
3. **Shop staff recommend; they do not commandeer.** Staff can send catalogue designs into the session.
4. **Inventory integrity matters.** A real retailer integration must use retailer-provided SKU, product imagery, purity/metal details, verified current price, branch stock and last-updated time.
5. **Visual honesty.** Keep the original product image and SKU visible alongside generated previews. Clearly label AI-generated outfit previews as illustrative.
6. **Privacy by design.** Real deployment needs room access controls, short-lived invite tokens, consent, participant removal, photo deletion/retention controls and secure transport.

## Recommended next implementation steps

### P0 — Shared backend before a real retailer pilot
- Add a Cloudflare Worker API and D1 schema for rooms, participants, products, pushed designs, looks, votes and comments.
- Use high-entropy invite tokens; do not treat a guessable room code as authentication.
- Add server-side role checks: bride, family and shop staff have different permissions.
- Add room polling or realtime updates so separate devices see the same state.
- Move photo/preview assets to Cloudflare R2 with signed/limited access; avoid storing full-resolution photos in browser or D1 records.
- Add rate limits, input validation, room expiry and deletion endpoints.

### P1 — Retail catalogue and sales workflow
- Import a real catalogue from CSV initially, with duplicate-SKU, missing-image, price and branch-stock validation.
- Display product price and availability timestamps.
- Let staff search by SKU/category/style/budget and send products to the buyer's room.
- Add a showroom-ready shortlist with total estimated price and branch availability.
- Track consented outcomes such as shortlist-to-visit and visit-to-purchase.

### P2 — Higher-fidelity visualisation
- Replace decorative placeholder art with retailer-approved product photographs and transparent assets.
- Calibrate placement by jewellery category and body landmarks.
- Implement outfit transformation as a separate, explicitly illustrative capability; preserve product identity and never silently replace jewellery with AI-invented pieces.
- Add image-quality checks, deletion controls and usability testing across common mobile devices.

## Suggested pilot success measures

- Time taken for staff to send relevant designs.
- Percentage of sessions that create a shortlist.
- Number of family participants and feedback completion.
- Shortlist-to-showroom-visit rate.
- Showroom-visit-to-purchase conversion, compared with a suitable baseline.
- Staff adoption and customer satisfaction.

Do not claim improved conversion until a retailer pilot measures it.

## Hosting

For a static preview, deploy the repository root as a static site. A production multi-device release will need a configured backend and secrets/variables; these are intentionally not included in this repository prototype.
