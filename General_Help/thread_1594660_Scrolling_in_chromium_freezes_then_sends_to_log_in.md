---
title: "Scrolling in chromium freezes then sends to log in screen"
date: 2010-10-12
forum: General Help
---

### Post by EienTatsu on 2010-10-12
Sometimes when I scroll in chromium the computer freezes then brings me to the log in screen.

This is the end of chrome_debug.log
```
[1161:1175:122572297088:INFO:chrome/browser/renderer_host/buffered_resource_handler.cc(140)] Finished buffering http://ads.bluelithium.com/st?ad_type=iframe&ad_size=300x250&section=1208992
[1161:1175:122572299351:INFO:chrome/browser/renderer_host/buffered_resource_handler.cc(178)] To buffer: http://ads.bluelithium.com/st?ad_type=iframe&ad_size=728x90&section=1208992
[1161:1175:122572299452:INFO:chrome/browser/renderer_host/buffered_resource_handler.cc(140)] Finished buffering http://ads.bluelithium.com/st?ad_type=iframe&ad_size=728x90&section=1208992
[26:26:122572378456:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://www.gaiaonline.com/forum/breedable-changing-pets/pokemon-haven-ss-in-july-see-event-post/t.55971123/
[26:26:122572388368:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://ad.doubleclick.net/N5243/adi/gaia.forums.gaiagaming/breedablechangingpets.thread;ag=39;gd=f;dn=0;tile=1;sz=300x250;v=;ord=1286895755
[26:26:122572399737:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://ad.doubleclick.net/N5243/adi/gaia.forums.gaiagaming/breedablechangingpets.thread;ag=39;gd=f;dn=0;tile=2;sz=728x90;v=;ord=1286895755
[1161:1161:122572442705:INFO:CONSOLE(0)] "Being Called," source: chrome-extension://pgphcomnlaojlmmcjmiddhdapjpbgeoc/infopasser.js (8)
[26:26:122572442822:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 1 scripts and 0 css files into http://ads.bluelithium.com/st?ad_type=iframe&ad_size=300x250&section=1208992
[1161:1161:122572446325:INFO:CONSOLE(0)] "Being Called," source: chrome-extension://pgphcomnlaojlmmcjmiddhdapjpbgeoc/infopasser.js (8)
[26:26:122572446560:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 1 scripts and 0 css files into http://ads.bluelithium.com/st?ad_type=iframe&ad_size=728x90&section=1208992
[1161:1161:122572448245:INFO:CONSOLE(0)] "Got message from bg page - https://mail.google.com/mail/?view=cm&fs=1&tf=1," source: chrome-extension://pgphcomnlaojlmmcjmiddhdapjpbgeoc/mailto.js (55)
[1161:1161:122572448375:INFO:CONSOLE(0)] "Starting to rewrite mailtos," source: chrome-extension://pgphcomnlaojlmmcjmiddhdapjpbgeoc/mailto.js (24)
[1161:1175:122573182831:INFO:net/base/cookie_monster.cc(1304)] Not parsing cookie, too large: 4108
[1161:1161:122573185553:INFO:net/base/cookie_monster.cc(1304)] Not parsing cookie, too large: 4108
[1161:1175:122573189766:INFO:net/base/cookie_monster.cc(1304)] Not parsing cookie, too large: 4108
[1161:1161:122573189951:INFO:net/base/cookie_monster.cc(1304)] Not parsing cookie, too large: 4108
[26:26:122573298821:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://ads.bluelithium.com/st?ad_type=iframe&ad_size=728x90&section=1208992
[1292:1292:122573299484:INFO:webkit/glue/plugins/plugin_lib.cc(101)] PluginLib::NP_Initialize(/var/lib/flashplugin-installer/npwrapper.libflashplayer.so): initialized=1
[1161:1161:122573312836:INFO:CONSOLE(0)] "Unsafe JavaScript attempt to access frame with URL http://www.gaiaonline.com/forum/breedable-changing-pets/pokemon-haven-ss-in-july-see-event-post/t.55971123/ from frame with URL http://ads.bluelithium.com/st?ad_type=iframe&ad_size=728x90&section=1208992. Domains, protocols and ports must match.
," source:  (1)
[26:26:122573334826:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://ads.bluelithium.com/st?ad_type=iframe&ad_size=300x250&section=1208992
[1292:1292:122573335789:INFO:webkit/glue/plugins/plugin_lib.cc(101)] PluginLib::NP_Initialize(/var/lib/flashplugin-installer/npwrapper.libflashplayer.so): initialized=1
[1161:1161:122573342169:INFO:CONSOLE(0)] "Unsafe JavaScript attempt to access frame with URL http://www.gaiaonline.com/forum/breedable-changing-pets/pokemon-haven-ss-in-july-see-event-post/t.55971123/ from frame with URL http://ads.bluelithium.com/st?ad_type=iframe&ad_size=300x250&section=1208992. Domains, protocols and ports must match.
," source:  (1)
[26:26:122573361563:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://ads.bluelithium.com/st?ad_type=iframe&ad_size=300x250&section=1208992
[26:26:122573513227:INFO:chrome/renderer/user_script_slave.cc(283)] Injected 4 scripts and 0 css files into http://ads.bluelithium.com/st?ad_type=iframe&ad_size=728x90&section=1208992
[1161:1175:122573572747:INFO:net/socket/ssl_client_socket_nss.cc(768)] The server action.mathtag.com does not support the TLS renegotiation_info extension.
[1161:1161:122591397061:FATAL:app/x11_util.cc(64)] X IO Error detected
[1292:1292:122591397262:FATAL:app/x11_util.cc(64)] X IO Error detected
```

---

