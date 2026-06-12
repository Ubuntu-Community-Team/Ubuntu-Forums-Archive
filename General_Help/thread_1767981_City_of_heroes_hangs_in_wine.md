---
title: "City of heroes hangs in wine"
date: 2011-05-26
forum: General Help
---

### Post by dmcfarland on 2011-05-26
I would post this on the wine website, however the thread for it is dead. I managed to get city of heroes installed but it hangs at the loading screen. Here's the gibberish in the terminal window.

fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=goingrogue.cityofheroes.com length=27
fixme:wininet:InternetInitializeAutoProxyDll STUB
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=goingrogue.cityofheroes.com length=27
fixme:wininet:InternetInitializeAutoProxyDll STUB
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:GetUrlCacheEntryInfoExW Undocumented flag(s): 100
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=goingrogue.cityofheroes.com length=27
fixme:wininet:InternetInitializeAutoProxyDll STUB
fixme:wininet:IsHostInProxyBypassList STUB: flags=3 host=goingrogue.cityofheroes.com length=27
fixme:wininet:InternetInitializeAutoProxyDll STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_END_BROWSER_SESSION: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RESET_URLCACHE_SESSION: STUB
fixme:ole:Context_CC_ContextCallback (0x694ac38/0x694ac3c)->(0x79f277a5, 0x29dcf14, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x694ac38/0x694ac3c)->(0x79f277a5, 0x29dcea8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:ole:Context_CC_ContextCallback (0x694ac38/0x694ac3c)->(0x79f277a5, 0x29dcea8, {d7174f82-36b8-4aa8-800a-e963ab2dfab9}, 2, (nil))
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub
fixme:advapi:UnregisterTraceGuids 0: stub

I am using the renderthread0 flag when I start it up.

---

