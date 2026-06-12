---
title: "freezes up"
date: 2011-08-28
forum: General Help
---

### Post by choochoousmc on 2011-08-28
ok have had 11.04 about a week now.
Every three days I have to do a complete reboot.
All internet programs lockup and refuse to reload, change pages etc
firefox, thunderbird, pan  all freeze!
Keeps locking up in CONNECTING mode.  Never had it with 10.10. so is something new.
only thing new is 11.04

Tried just closing the programs, and restarting, no luck. Only a reboot corrects the problem.


any suggestions?

---

### Post by ubudog on 2011-08-28
Does the program freeze completely (for instance, you are presented with a force close dialog)?  If not, it may be that your internet is flaking out.  Have you recently done any updates?

---

### Post by choochoousmc on 2011-08-29
AS Above, updated to 11.04.
That also allowed a Firefox update.
I had to use a Ubuntu software application to force Pan to quit, it was locked completely.

Thunderbird quit when I clicked red / orange X, but would not activate the drop down menu.
Firefox, would not refresh any webpage that was open. Drop down menu would not activate. had to use the X.
Different webpages, different locations, different servers so not something at other end.
Non internet programs already open appeared to be working.
Had fireox on a windows computer it ws not locked up. 

as before never happened under 10.10   So right now the common thing and only change is 11.04

---

### Post by ubudog on 2011-08-29
Could you post the output of dmesg?

```
dmesg
```

---

### Post by choochoousmc on 2011-09-05
here you go   dmesg output     what is this for?


[47763.531800] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[47763.531808] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[47764.739008] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[47764.740976] wlan0: authenticated
[47764.741023] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[47764.745776] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[47764.745787] wlan0: associated
[49203.458250] cfg80211: All devices are disconnected, going to restore regulatory settings
[49203.458266] cfg80211: Restoring regulatory settings
[49203.458277] cfg80211: Calling CRDA to update world regulatory domain
[49203.473456] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[49203.473472] cfg80211: World regulatory domain updated:
[49203.473478] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[49203.473488] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[49203.473497] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[49203.473505] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[49203.473513] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[49203.473521] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[49204.720503] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[49204.722476] wlan0: authenticated
[49204.745922] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[49204.749835] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[49204.749846] wlan0: associated
[50763.465801] cfg80211: All devices are disconnected, going to restore regulatory settings
[50763.465814] cfg80211: Restoring regulatory settings
[50763.465825] cfg80211: Calling CRDA to update world regulatory domain
[50763.482278] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[50763.482295] cfg80211: World regulatory domain updated:
[50763.482300] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[50763.482310] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[50763.482319] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[50763.482327] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[50763.482335] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[50763.482342] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[50764.732893] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[50764.734882] wlan0: authenticated
[50764.760439] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[50764.764434] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[50764.764443] wlan0: associated
[51003.454130] cfg80211: All devices are disconnected, going to restore regulatory settings
[51003.454146] cfg80211: Restoring regulatory settings
[51003.454156] cfg80211: Calling CRDA to update world regulatory domain
[51003.470165] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[51003.470181] cfg80211: World regulatory domain updated:
[51003.470187] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[51003.470196] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51003.470205] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[51003.470213] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[51003.470221] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51003.470229] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[51004.716407] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[51004.718410] wlan0: authenticated
[51004.742520] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[51004.746421] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[51004.746433] wlan0: associated
[52803.456583] cfg80211: All devices are disconnected, going to restore regulatory settings
[52803.456599] cfg80211: Restoring regulatory settings
[52803.456610] cfg80211: Calling CRDA to update world regulatory domain
[52803.471884] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[52803.471901] cfg80211: World regulatory domain updated:
[52803.471907] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[52803.471916] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[52803.471925] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[52803.471933] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[52803.471941] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[52803.471949] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[52804.749927] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[52804.751882] wlan0: authenticated
[52804.784196] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[52804.788206] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[52804.788217] wlan0: associated
[55582.884537] usb 1-2.3: USB disconnect, address 5
[57483.472169] cfg80211: All devices are disconnected, going to restore regulatory settings
[57483.472184] cfg80211: Restoring regulatory settings
[57483.472195] cfg80211: Calling CRDA to update world regulatory domain
[57483.486578] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[57483.486594] cfg80211: World regulatory domain updated:
[57483.486600] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[57483.486610] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[57483.486619] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[57483.486627] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[57483.486635] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[57483.486643] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[57484.762448] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[57484.766879] wlan0: authenticated
[57484.766938] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[57484.770764] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[57484.770773] wlan0: associated
[57963.451415] cfg80211: All devices are disconnected, going to restore regulatory settings
[57963.451423] cfg80211: Restoring regulatory settings
[57963.451429] cfg80211: Calling CRDA to update world regulatory domain
[57963.458606] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[57963.458615] cfg80211: World regulatory domain updated:
[57963.458617] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[57963.458622] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[57963.458627] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[57963.458631] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[57963.458635] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[57963.458638] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[57964.713309] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[57964.715708] wlan0: authenticated
[57964.715762] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[57964.719585] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[57964.719594] wlan0: associated
[65043.461074] cfg80211: All devices are disconnected, going to restore regulatory settings
[65043.461090] cfg80211: Restoring regulatory settings
[65043.461102] cfg80211: Calling CRDA to update world regulatory domain
[65043.477118] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[65043.477135] cfg80211: World regulatory domain updated:
[65043.477141] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[65043.477150] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[65043.477159] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[65043.477167] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[65043.477175] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[65043.477183] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[65044.700564] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[65044.706186] wlan0: authenticated
[65044.706244] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[65044.710056] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[65044.710065] wlan0: associated
[65765.068120] cfg80211: All devices are disconnected, going to restore regulatory settings
[65765.068128] cfg80211: Restoring regulatory settings
[65765.068135] cfg80211: Calling CRDA to update world regulatory domain
[65765.079763] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[65765.079772] cfg80211: World regulatory domain updated:
[65765.079775] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[65765.079780] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[65765.079784] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[65765.079788] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[65765.079792] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[65765.079796] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[65766.325004] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[65766.326935] wlan0: authenticated
[65766.392503] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[65766.396302] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[65766.396308] wlan0: associated
[66843.453703] cfg80211: All devices are disconnected, going to restore regulatory settings
[66843.453718] cfg80211: Restoring regulatory settings
[66843.453730] cfg80211: Calling CRDA to update world regulatory domain
[66843.470653] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[66843.470671] cfg80211: World regulatory domain updated:
[66843.470676] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[66843.470686] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[66843.470695] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[66843.470703] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[66843.470711] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[66843.470719] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[66844.720474] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[66844.722396] wlan0: authenticated
[66844.722447] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[66844.726331] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[66844.726342] wlan0: associated
[67683.459958] cfg80211: All devices are disconnected, going to restore regulatory settings
[67683.459973] cfg80211: Restoring regulatory settings
[67683.459985] cfg80211: Calling CRDA to update world regulatory domain
[67683.474359] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[67683.474375] cfg80211: World regulatory domain updated:
[67683.474381] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[67683.474390] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[67683.474399] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[67683.474407] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[67683.474415] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[67683.474423] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[67684.732212] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[67684.734216] wlan0: authenticated
[67684.734272] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[67684.738083] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[67684.738094] wlan0: associated
[68283.456207] cfg80211: All devices are disconnected, going to restore regulatory settings
[68283.456222] cfg80211: Restoring regulatory settings
[68283.456234] cfg80211: Calling CRDA to update world regulatory domain
[68283.471009] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[68283.471025] cfg80211: World regulatory domain updated:
[68283.471031] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[68283.471040] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[68283.471049] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[68283.471057] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[68283.471065] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[68283.471073] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[68284.721013] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[68284.722960] wlan0: authenticated
[68284.749344] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[68284.753237] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[68284.753246] wlan0: associated
[69603.458738] cfg80211: All devices are disconnected, going to restore regulatory settings
[69603.458754] cfg80211: Restoring regulatory settings
[69603.458765] cfg80211: Calling CRDA to update world regulatory domain
[69603.473218] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[69603.473234] cfg80211: World regulatory domain updated:
[69603.473240] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[69603.473250] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[69603.473258] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[69603.473267] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[69603.473274] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[69603.473282] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[69604.724664] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[69604.726639] wlan0: authenticated
[69604.726695] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[69604.730493] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[69604.730502] wlan0: associated
[69723.458646] cfg80211: All devices are disconnected, going to restore regulatory settings
[69723.458662] cfg80211: Restoring regulatory settings
[69723.458673] cfg80211: Calling CRDA to update world regulatory domain
[69723.474308] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[69723.474327] cfg80211: World regulatory domain updated:
[69723.474333] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[69723.474342] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[69723.474351] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[69723.474360] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[69723.474367] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[69723.474375] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[69724.726492] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[69724.728506] wlan0: authenticated
[69724.728564] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[69724.732593] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[69724.732602] wlan0: associated
[70923.465455] cfg80211: All devices are disconnected, going to restore regulatory settings
[70923.465472] cfg80211: Restoring regulatory settings
[70923.465485] cfg80211: Calling CRDA to update world regulatory domain
[70923.478043] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[70923.478060] cfg80211: World regulatory domain updated:
[70923.478066] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[70923.478075] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[70923.478084] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[70923.478092] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[70923.478100] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[70923.478108] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[70924.728833] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[70924.730832] wlan0: authenticated
[70924.754802] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[70924.758695] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[70924.758706] wlan0: associated
[71403.464497] cfg80211: All devices are disconnected, going to restore regulatory settings
[71403.464513] cfg80211: Restoring regulatory settings
[71403.464525] cfg80211: Calling CRDA to update world regulatory domain
[71403.485201] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[71403.485218] cfg80211: World regulatory domain updated:
[71403.485224] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[71403.485233] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71403.485242] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[71403.485250] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[71403.485258] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71403.485266] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71404.731060] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[71404.733047] wlan0: authenticated
[71404.733107] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[71404.736926] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[71404.736935] wlan0: associated
[77043.458897] cfg80211: All devices are disconnected, going to restore regulatory settings
[77043.458912] cfg80211: Restoring regulatory settings
[77043.458924] cfg80211: Calling CRDA to update world regulatory domain
[77043.550192] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[77043.550209] cfg80211: World regulatory domain updated:
[77043.550215] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[77043.550224] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[77043.550233] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[77043.550241] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[77043.550249] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[77043.550257] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[77044.740121] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[77044.742080] wlan0: authenticated
[77044.783808] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[77044.787929] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[77044.787935] wlan0: associated
[77283.496074] cfg80211: All devices are disconnected, going to restore regulatory settings
[77283.496083] cfg80211: Restoring regulatory settings
[77283.496089] cfg80211: Calling CRDA to update world regulatory domain
[77283.504905] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[77283.504914] cfg80211: World regulatory domain updated:
[77283.504917] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[77283.504921] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[77283.504926] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[77283.504930] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[77283.504934] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[77283.504938] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[77284.764661] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[77284.766636] wlan0: authenticated
[77284.792152] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[77284.796105] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[77284.796117] wlan0: associated
[79203.461409] cfg80211: All devices are disconnected, going to restore regulatory settings
[79203.461425] cfg80211: Restoring regulatory settings
[79203.461436] cfg80211: Calling CRDA to update world regulatory domain
[79203.475159] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[79203.475177] cfg80211: World regulatory domain updated:
[79203.475182] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[79203.475192] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[79203.475201] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[79203.475209] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[79203.475217] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[79203.475225] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[79204.723255] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[79204.725163] wlan0: authenticated
[79204.751653] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[79204.755542] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[79204.755552] wlan0: associated
[85683.491871] cfg80211: All devices are disconnected, going to restore regulatory settings
[85683.491879] cfg80211: Restoring regulatory settings
[85683.491885] cfg80211: Calling CRDA to update world regulatory domain
[85683.499282] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[85683.499291] cfg80211: World regulatory domain updated:
[85683.499294] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[85683.499299] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[85683.499303] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[85683.499307] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[85683.499311] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[85683.499315] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[85684.758587] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[85684.760905] wlan0: authenticated
[85684.800039] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[85684.803854] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[85684.803861] wlan0: associated
[89403.467880] cfg80211: All devices are disconnected, going to restore regulatory settings
[89403.467888] cfg80211: Restoring regulatory settings
[89403.467894] cfg80211: Calling CRDA to update world regulatory domain
[89403.476318] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[89403.476326] cfg80211: World regulatory domain updated:
[89403.476329] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[89403.476334] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[89403.476338] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[89403.476342] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[89403.476346] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[89403.476350] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[89404.734164] wlan0: authenticate with 30:46:9a:02:38:bc (try 1)
[89404.736267] wlan0: authenticated
[89404.760932] wlan0: associate with 30:46:9a:02:38:bc (try 1)
[89404.764828] wlan0: RX AssocResp from 30:46:9a:02:38:bc (capab=0x421 status=0 aid=4)
[89404.764838] wlan0: associated
choochoo@choochoo-acer:~$

---

