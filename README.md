# Remote config

`remote-config.json` is fetched by the app at start (raw GitHub first, jsDelivr CDN as fallback) and cached on the device.
Values are numbers, booleans and strings; nested objects become dotted keys (`ads.shopAdDailyCap`). An empty string means "keep the bundled value".
Bump `version` on every change; a lower version is never applied. Published from the app project with `tools/remote-config-push.sh` (also purges the jsDelivr cache).

| Key | Meaning |
|---|---|
| `ads.rewardedEnabled` / `interstitialEnabled` / `bannerEnabled` | Kill switches per ad format |
| `ads.interstitialAfterMatches`, `ads.interstitialEveryMatches`, `ads.interstitialMinIntervalSeconds`, `ads.interstitialSkipFirstMatchOfDay` | Interstitial policy |
| `ads.shopAdDailyCap` | Rewarded "watch ad for coins" per day |
| `ads.android.*`, `ads.ios.*` | Ad unit ids (banner / interstitial / rewarded); test ids still win in debug builds |
| `worldrally.freeAttempts`, `worldrally.maxExtraAttemptsPerDay` | Daily challenge attempts |
