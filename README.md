# Betasi Consent Manager

Google Tag Manager tag template that connects [PremiumStay](https://betasi.pl/) cookie consent with Google Consent Mode.

**Requires PremiumStay 2026.11 or newer.** The template reads the `BetasiConsent` cookie and registers through `addBetasiConsentListener`, both provided by PremiumStay; on other sites it only applies the default state from its fields.

## What it does

- **Default state.** If the guest has already decided, the default comes from the `BetasiConsent` cookie: accepted categories are `granted`, the rest `denied`, `functionality_storage` always `granted`. Before the guest decides, the default comes from the template fields, with `wait_for_update`.
- **Updates.** The template registers a callback with `window.addBetasiConsentListener`. PremiumStay calls it on every consent change, before it pushes `client-consent-update` to the data layer, so tags firing on that event already see the new state.
- **Settings.** `url_passthrough` and `ads_data_redaction` are set with `gtag set`.

## Setup

Create one tag from this template and fire it on **Consent Initialization - All Pages**. Tags that need consent declare it in their own consent settings (for example `ad_storage` for advertising pixels).

The full PremiumStay GTM setup is described in the PremiumStay administration instructions, available to PremiumStay clients.

## License

Apache 2.0 — see [LICENSE](LICENSE).
