---
title: "Multiple applications segmentation faults after GNOME load"
date: 2010-05-04
forum: General Help
---

### Post by Djzn.BR on 2010-05-04
update : [ Possible major issue with **fglrx** ]

As some are aware, some users [ possibly ATI card owners running fglrx default ubuntu driver ] have issues having compiz enabled and trying to change the mouse pointer to a larger size. It actually doesn't get resized at all, expect when moved over Firefox and OpenOffice. 

Very well... Yesterday, I was fiddling in trying to get a workaround for this when suddenly Nautilus started to crash and respawn in an infinite loop. Everything then started to fail. gnome-terminal wouldn't open, xterm wouldn't open, menus wouldn't respond. Etc... The entire GNOME desktop was inoperable. 

Logging out and choosing Fluxbox and KDE didn't help. I was sent right back to the GDM login screen. Hmm... seems not related entirely to GNOME... if it all.

From a terminal, I could see constant crashes, segfaults on libc6-2.11.1... 

While at it, I logged on another account (my wife's) and everything was perfectly FINE, with no issues at all. Creating them another account and initializing, it also didn't happen any segfaults. However, everytime I logged in my own account, everything would happen again... nautilus respawning, no terminal, nothing, not even logout would work. 

Either I hit a** MAJOR BUG** in libc6 current ubuntu compile, or a setting file inside my home dir got really corrupted and screwed up. It was very frustrating, because this bug was a show stopper. 

For those who concern, my mobo is an Asus M3A78-EM running a ATI HD 3200 IGP, and I have ubuntu-default **fglrx** running.

I had run memtest+ overnight and no errors whatsoever. The fact that this was an "account specific" issue deems that there is no hardware fault. 

I had to migrate my old account to a newly created account, it was hard work because of my 100GB files. Setting ownership in each of them, etc. 

Everything is OK now, but I really wished to know what dimmed out my bright Lucid Lynx experience yesterday. And I just hope this doesn't happen again.

Please if you can add any confirmation that this is fglrx issue, please do so.
Next post have some information on the segmentation faults:

---

### Post by Djzn.BR on 2010-05-04
This is the first time it occured...
Looks to me it may be an issue with infamous fglrx.

```
May  3 21:24:21 orion-desktop kernel: [   14.855547] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 21:24:21 orion-desktop kernel: [   14.856402] [fglrx] Firegl kernel thread PID: 1142
May  3 21:24:21 orion-desktop kernel: [   14.856646] [fglrx] IRQ 27 Enabled
May  3 21:24:21 orion-desktop kernel: [   15.259488] [fglrx] Gart USWC size:548 M.
May  3 21:24:21 orion-desktop kernel: [   15.259491] [fglrx] Gart cacheable size:215 M.
May  3 21:24:21 orion-desktop kernel: [   15.259494] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 21:24:21 orion-desktop kernel: [   15.259497] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 21:44:30 orion-desktop kernel: [ 1223.153579] __ratelimit: 12 callbacks suppressed
May  3 21:44:30 orion-desktop kernel: [ 1223.153583] gnome-appearanc[1999]: segfault at bef0cfec ip 00542835 sp bef0cff0 error 6 in libc-2.11.1.so[4e7000+153000]
May  3 21:44:42 orion-desktop kernel: [ 1235.375366] gnome-appearanc[2002]: segfault at bf087ffc ip 004fda2a sp bf088000 error 6 in libc-2.11.1.so[441000+153000]
May  3 21:44:47 orion-desktop kernel: [ 1240.077970] gtk-logout-help[2005]: segfault at bf5f3ffc ip 001e5a2a sp bf5f4000 error 6 in libc-2.11.1.so[129000+153000]
May  3 21:44:57 orion-desktop bonobo-activation-server (djzn-2033): could not associate with desktop session: Failed to connect to socket /tmp/dbus-v9hVXSo8ID: Conexão recusada
May  3 21:45:08 orion-desktop kernel: [ 1260.690103] nautilus[2187]: segfault at bf5edfec ip 0370a835 sp bf5edff0 error 6 in libc-2.11.1.so[36af000+153000]
May  3 21:45:09 orion-desktop kernel: [ 1262.463548] nautilus[2250]: segfault at bf0d5fcc ip 09a02835 sp bf0d5fd0 error 6 in libc-2.11.1.so[99a7000+153000]
May  3 21:45:11 orion-desktop kernel: [ 1264.184040] nautilus[2257]: segfault at bf1f0fcc ip 037a3835 sp bf1f0fd0 error 6 in libc-2.11.1.so[3748000+153000]
May  3 21:45:13 orion-desktop kernel: [ 1265.898524] nautilus[2259]: segfault at bf57dffc ip 06a8c2b3 sp bf57dffc error 6 in libc-2.11.1.so[6a25000+153000]
May  3 21:45:15 orion-desktop kernel: [ 1267.634671] nautilus[2266]: segfault at bf284fec ip 05214835 sp bf284ff0 error 6 in libc-2.11.1.so[51b9000+153000]
May  3 21:45:16 orion-desktop kernel: [ 1269.333264] nautilus[2269]: segfault at befd6ffc ip 025f7835 sp befd7000 error 6 in libc-2.11.1.so[259c000+153000]
May  3 21:45:18 orion-desktop kernel: [ 1271.032469] nautilus[2271]: segfault at bf3ddfbc ip 04b07835 sp bf3ddfc0 error 6 in libc-2.11.1.so[4aac000+153000]
May  3 21:45:20 orion-desktop kernel: [ 1272.755777] nautilus[2273]: segfault at bf152fbc ip 01bbc835 sp bf152fc0 error 6 in libc-2.11.1.so[1b61000+153000]
May  3 21:45:22 orion-desktop kernel: [ 1274.740075] nautilus[2276]: segfault at bf130ffc ip 03f37835 sp bf131000 error 6 in libc-2.11.1.so[3edc000+153000]
May  3 21:45:22 orion-desktop kernel: [ 1275.161534] gnome-terminal[2279]: segfault at bf127ffc ip 00a792b3 sp bf127ffc error 6 in libc-2.11.1.so[a12000+153000]
May  3 21:45:23 orion-desktop kernel: [ 1276.511656] nautilus[2280]: segfault at bee8cfec ip 01466835 sp bee8cff0 error 6 in libc-2.11.1.so[140b000+153000]
May  3 21:45:25 orion-desktop kernel: [ 1278.286290] gnome-terminal[2283]: segfault at bee22fdc ip 00d56835 sp bee22fe0 error 6 in libc-2.11.1.so[cfb000+153000]
May  3 21:45:25 orion-desktop kernel: [ 1278.515103] nautilus[2284]: segfault at befb6fec ip 08b71835 sp befb6ff0 error 6 in libc-2.11.1.so[8b16000+153000]
May  3 21:45:27 orion-desktop kernel: [ 1280.231192] nautilus[2287]: segfault at bf542ffc ip 03d062b3 sp bf542ffc error 6 in libc-2.11.1.so[3c9f000+153000]
May  3 21:45:29 orion-desktop kernel: [ 1281.923761] nautilus[2289]: segfault at bf29efec ip 070ab835 sp bf29eff0 error 6 in libc-2.11.1.so[7050000+153000]
May  3 21:45:31 orion-desktop kernel: [ 1283.606438] nautilus[2291]: segfault at bee2efec ip 02651835 sp bee2eff0 error 6 in libc-2.11.1.so[25f6000+153000]
May  3 21:45:32 orion-desktop kernel: [ 1285.318051] nautilus[2293]: segfault at bf37bfbc ip 05b78835 sp bf37bfc0 error 6 in libc-2.11.1.so[5b1d000+153000]
May  3 21:45:34 orion-desktop kernel: [ 1287.177969] nautilus[2295]: segfault at bef1dffc ip 00d1d835 sp bef1e000 error 6 in libc-2.11.1.so[cc2000+153000]
May  3 21:45:36 orion-desktop kernel: [ 1288.907517] nautilus[2327]: segfault at beea3fcc ip 039bb835 sp beea3fd0 error 6 in libc-2.11.1.so[3960000+153000]
May  3 21:45:38 orion-desktop kernel: [ 1290.674008] nautilus[2331]: segfault at befe3fdc ip 03dde835 sp befe3fe0 error 6 in libc-2.11.1.so[3d83000+153000]
May  3 21:45:39 orion-desktop kernel: [ 1292.379809] nautilus[2356]: segfault at bf5c6ffc ip 01c232b3 sp bf5c6ffc error 6 in libc-2.11.1.so[1bbc000+153000]
May  3 21:45:41 orion-desktop kernel: [ 1294.062541] nautilus[2358]: segfault at bf47cffc ip 07a70a2a sp bf47d000 error 6 in libc-2.11.1.so[79b4000+153000]
May  3 21:45:43 orion-desktop kernel: [ 1295.763260] nautilus[2360]: segfault at bf319fec ip 07de6835 sp bf319ff0 error 6 in libc-2.11.1.so[7d8b000+153000]
May  3 21:45:44 orion-desktop kernel: [ 1297.444707] nautilus[2362]: segfault at bf034ffc ip 065342b3 sp bf034ffc error 6 in libc-2.11.1.so[64cd000+153000]
May  3 21:45:46 orion-desktop kernel: [ 1299.154329] nautilus[2364]: segfault at bf000fbc ip 06e87835 sp bf000fc0 error 6 in libc-2.11.1.so[6e2c000+153000]
May  3 21:45:48 orion-desktop kernel: [ 1300.866579] nautilus[2366]: segfault at bf21dffc ip 049262b3 sp bf21dffc error 6 in libc-2.11.1.so[48bf000+153000]
May  3 21:45:50 orion-desktop kernel: [ 1302.592013] nautilus[2368]: segfault at bf1b3ffc ip 03829835 sp bf1b4000 error 6 in libc-2.11.1.so[37ce000+153000]
May  3 21:45:51 orion-desktop kernel: [ 1304.276877] nautilus[2370]: segfault at bf196fec ip 02d07835 sp bf196ff0 error 6 in libc-2.11.1.so[2cac000+153000]
May  3 21:45:53 orion-desktop kernel: [ 1305.961770] nautilus[2372]: segfault at bf425ffc ip 0535b835 sp bf426000 error 6 in libc-2.11.1.so[5300000+153000]
May  3 21:45:55 orion-desktop kernel: [ 1307.624013] nautilus[2392]: segfault at bf4adffc ip 075652b3 sp bf4adffc error 6 in libc-2.11.1.so[74fe000+153000]
May  3 21:45:57 orion-desktop kernel: [ 1309.747544] gnome-appearanc[2298]: segfault at bee87fdc ip 0078b835 sp bee87fe0 error 6 in libc-2.11.1.so[730000+153000]
May  3 21:45:57 orion-desktop kernel: [ 1310.489915] nautilus[2402]: segfault at bf208ffc ip 01453a2a sp bf209000 error 6 in libc-2.11.1.so[1397000+153000]
May  3 21:45:59 orion-desktop kernel: [ 1312.372676] nautilus[2412]: segfault at bf03bfdc ip 046fd835 sp bf03bfe0 error 6 in libc-2.11.1.so[46a2000+153000]
May  3 21:46:01 orion-desktop kernel: [ 1314.093264] nautilus[2414]: segfault at bf027ffc ip 012fe835 sp bf028000 error 6 in libc-2.11.1.so[12a3000+153000]
May  3 21:46:03 orion-desktop kernel: [ 1315.795627] nautilus[2416]: segfault at bf109fcc ip 05378835 sp bf109fd0 error 6 in libc-2.11.1.so[531d000+153000]
May  3 21:46:04 orion-desktop kernel: [ 1317.503815] nautilus[2418]: segfault at bef93ffc ip 09893a2a sp bef94000 error 6 in libc-2.11.1.so[97d7000+153000]
May  3 21:46:06 orion-desktop kernel: [ 1319.207544] nautilus[2422]: segfault at bf1ccfec ip 07593835 sp bf1ccff0 error 6 in libc-2.11.1.so[7538000+153000]
May  3 21:46:08 orion-desktop kernel: [ 1320.940353] nautilus[2434]: segfault at beea7ffc ip 03c2b2b3 sp beea7ffc error 6 in libc-2.11.1.so[3bc4000+153000]
May  3 21:46:10 orion-desktop kernel: [ 1322.592937] nautilus[2440]: segfault at bef32fcc ip 08751835 sp bef32fd0 error 6 in libc-2.11.1.so[86f6000+153000]
May  3 21:46:11 orion-desktop kernel: [ 1324.290690] nautilus[2442]: segfault at bf2c6fcc ip 07c97835 sp bf2c6fd0 error 6 in libc-2.11.1.so[7c3c000+153000]
May  3 21:46:13 orion-desktop kernel: [ 1326.007558] nautilus[2444]: segfault at bf05afec ip 070eb835 sp bf05aff0 error 6 in libc-2.11.1.so[7090000+153000]
May  3 21:46:15 orion-desktop kernel: [ 1327.958780] nautilus[2446]: segfault at bf0a2ffc ip 0443d835 sp bf0a3000 error 6 in libc-2.11.1.so[43e2000+153000]
May  3 21:46:15 orion-desktop kernel: [ 1328.345814] gtk-logout-help[2449]: segfault at bf331fdc ip 007a0835 sp bf331fe0 error 6 in libc-2.11.1.so[745000+153000]
May  3 21:46:17 orion-desktop kernel: [ 1329.728014] nautilus[2450]: segfault at beecbffc ip 00d67a2a sp beecc000 error 6 in libc-2.11.1.so[cab000+153000]
May  3 21:46:18 orion-desktop kernel: [ 1331.410195] nautilus[2452]: segfault at bf4b6ffc ip 00ed5a2a sp bf4b7000 error 6 in libc-2.11.1.so[e19000+153000]
May  3 21:46:21 orion-desktop kernel: [ 1334.514294] gnome-session[2112]: segfault at bf4edfcc ip 00eee835 sp bf4edfd0 error 6 in libc-2.11.1.so[e93000+153000]
May  3 21:46:22 orion-desktop bonobo-activation-server (djzn-2467): could not associate with desktop session: Failed to connect to socket /tmp/dbus-n56xKndM7w: Conexão recusada
May  3 21:46:22 orion-desktop pulseaudio[2477]: pid.c: Stale PID file, overwriting.
May  3 21:46:27 orion-desktop bonobo-activation-server (djzn-2600): could not associate with desktop session: Failed to connect to socket /tmp/dbus-n56xKndM7w: Conexão recusada
May  3 22:04:26 orion-desktop kernel: [ 2419.446336] nautilus[2826]: segfault at bf219fec ip 06bf8835 sp bf219ff0 error 6 in libc-2.11.1.so[6b9d000+153000]
May  3 22:04:29 orion-desktop kernel: [ 2421.775790] nautilus[2833]: segfault at bee54ffc ip 05e5da2a sp bee55000 error 6 in libc-2.11.1.so[5da1000+153000]
May  3 22:04:30 orion-desktop kernel: [ 2423.466187] nautilus[2895]: segfault at bf0b1fcc ip 02444835 sp bf0b1fd0 error 6 in libc-2.11.1.so[23e9000+153000]
May  3 22:04:32 orion-desktop kernel: [ 2425.166389] nautilus[2899]: segfault at bf4a7fec ip 06f33835 sp bf4a7ff0 error 6 in libc-2.11.1.so[6ed8000+153000]
May  3 22:04:33 orion-desktop bonobo-activation-server (djzn-2914): could not associate with desktop session: Failed to connect to socket /tmp/dbus-enUf3eiIry: Conexão recusada
May  3 22:04:34 orion-desktop kernel: [ 2426.935501] nautilus[2901]: segfault at bf34efdc ip 0628e835 sp bf34efe0 error 6 in libc-2.11.1.so[6233000+153000]
May  3 22:05:23 orion-desktop kernel: Kernel logging (proc) stopped.
May  3 22:05:23 orion-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="815" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  3 22:05:54 orion-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  3 22:05:54 orion-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="844" x-info="http://www.rsyslog.com"] (re)start
May  3 22:05:54 orion-desktop rsyslogd: rsyslogd's groupid changed to 103
May  3 22:05:54 orion-desktop rsyslogd: rsyslogd's userid changed to 101
```


And there, more tries.... when the desktop became inoperable!

```
May  3 22:05:54 orion-desktop kernel: [   14.591202] r8169: eth0: link up
May  3 22:05:54 orion-desktop kernel: [   14.591217] r8169: eth0: link up
May  3 22:05:55 orion-desktop kernel: [   15.353618] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:05:55 orion-desktop kernel: [   15.354242] [fglrx] Firegl kernel thread PID: 1114
May  3 22:05:55 orion-desktop kernel: [   15.354490] [fglrx] IRQ 27 Enabled
May  3 22:05:55 orion-desktop kernel: [   15.765501] [fglrx] Gart USWC size:548 M.
May  3 22:05:55 orion-desktop kernel: [   15.765504] [fglrx] Gart cacheable size:215 M.
May  3 22:05:55 orion-desktop kernel: [   15.765508] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:05:55 orion-desktop kernel: [   15.765510] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:06:11 orion-desktop kernel: [   26.445009] __ratelimit: 12 callbacks suppressed
May  3 22:06:11 orion-desktop kernel: [   26.445013] nautilus[1470]: segfault at befb9ffc ip 06c422b3 sp befb9ffc error 6 in libc-2.11.1.so[6bdb000+153000]
May  3 22:06:12 orion-desktop pulseaudio[1467]: ratelimit.c: 15428 events suppressed
May  3 22:06:13 orion-desktop kernel: [   28.399715] nautilus[1546]: segfault at bee1efcc ip 05e73835 sp bee1efd0 error 6 in libc-2.11.1.so[5e18000+153000]
May  3 22:06:15 orion-desktop kernel: [   30.042534] nautilus[1550]: segfault at bf2dafec ip 0202a835 sp bf2daff0 error 6 in libc-2.11.1.so[1fcf000+153000]
May  3 22:06:17 orion-desktop kernel: [   31.674229] nautilus[1552]: segfault at bf1fffdc ip 065ed835 sp bf1fffe0 error 6 in libc-2.11.1.so[6592000+153000]
May  3 22:06:18 orion-desktop kernel: [   33.326624] nautilus[1559]: segfault at bee35ffc ip 07ece835 sp bee36000 error 6 in libc-2.11.1.so[7e73000+153000]
May  3 22:06:20 orion-desktop kernel: [   34.974917] nautilus[1562]: segfault at bf5c8fdc ip 04b04835 sp bf5c8fe0 error 6 in libc-2.11.1.so[4aa9000+153000]
May  3 22:06:22 orion-desktop kernel: [   36.622019] nautilus[1564]: segfault at bf53dffc ip 05476a2a sp bf53e000 error 6 in libc-2.11.1.so[53ba000+153000]
May  3 22:06:23 orion-desktop kernel: [   38.258353] nautilus[1566]: segfault at beeadfec ip 03463835 sp beeadff0 error 6 in libc-2.11.1.so[3408000+153000]
May  3 22:06:25 orion-desktop kernel: [   39.923086] nautilus[1569]: segfault at bf1b1fbc ip 00d04835 sp bf1b1fc0 error 6 in libc-2.11.1.so[ca9000+153000]
May  3 22:06:27 orion-desktop kernel: [   41.570203] nautilus[1571]: segfault at bf0cafdc ip 03913835 sp bf0cafe0 error 6 in libc-2.11.1.so[38b8000+153000]
May  3 22:06:28 orion-desktop kernel: [   43.254585] nautilus[1576]: segfault at bf46dffc ip 01050835 sp bf46e000 error 6 in libc-2.11.1.so[ff5000+153000]
May  3 22:06:30 orion-desktop kernel: [   44.892989] nautilus[1578]: segfault at befb8ffc ip 05f9f835 sp befb9000 error 6 in libc-2.11.1.so[5f44000+153000]
May  3 22:06:31 orion-desktop kernel: [   46.534643] nautilus[1580]: segfault at bef0cfcc ip 02d74835 sp bef0cfd0 error 6 in libc-2.11.1.so[2d19000+153000]
May  3 22:06:33 orion-desktop kernel: [   48.186965] nautilus[1582]: segfault at beec4ffc ip 010b0a2a sp beec5000 error 6 in libc-2.11.1.so[ff4000+153000]
May  3 22:06:35 orion-desktop kernel: [   49.822674] nautilus[1584]: segfault at bf3ddffc ip 096fd835 sp bf3de000 error 6 in libc-2.11.1.so[96a2000+153000]
May  3 22:06:36 orion-desktop kernel: [   51.456329] nautilus[1588]: segfault at bf52cfdc ip 07f0b835 sp bf52cfe0 error 6 in libc-2.11.1.so[7eb0000+153000]
May  3 22:06:38 orion-desktop kernel: [   53.175924] nautilus[1590]: segfault at bef9affc ip 062ee835 sp bef9b000 error 6 in libc-2.11.1.so[6293000+153000]
May  3 22:06:40 orion-desktop kernel: [   54.814836] nautilus[1720]: segfault at bf3e3fdc ip 03e59835 sp bf3e3fe0 error 6 in libc-2.11.1.so[3dfe000+153000]
May  3 22:06:41 orion-desktop kernel: [   56.456455] nautilus[1724]: segfault at befc6fdc ip 00d15835 sp befc6fe0 error 6 in libc-2.11.1.so[cba000+153000]
May  3 22:06:44 orion-desktop kernel: [   58.690156] nautilus[1729]: segfault at beedeffc ip 00dc8a2a sp beedf000 error 6 in libc-2.11.1.so[d0c000+153000]
May  3 22:06:46 orion-desktop kernel: [   60.705157] nautilus[1735]: segfault at bf2ebffc ip 0501ba2a sp bf2ec000 error 6 in libc-2.11.1.so[4f5f000+153000]
May  3 22:06:47 orion-desktop kernel: [   62.350292] nautilus[1737]: segfault at bf3b4ffc ip 074772b3 sp bf3b4ffc error 6 in libc-2.11.1.so[7410000+153000]
May  3 22:06:49 orion-desktop kernel: [   63.999697] nautilus[1739]: segfault at bf491fec ip 085a4835 sp bf491ff0 error 6 in libc-2.11.1.so[8549000+153000]
May  3 22:06:51 orion-desktop kernel: [   65.655013] nautilus[1741]: segfault at bf577fdc ip 06f8f835 sp bf577fe0 error 6 in libc-2.11.1.so[6f34000+153000]
May  3 22:06:52 orion-desktop kernel: [   67.535735] nautilus[1743]: segfault at bf2a2fbc ip 04f93835 sp bf2a2fc0 error 6 in libc-2.11.1.so[4f38000+153000]
May  3 22:06:53 orion-desktop kernel: [   68.212992] gnome-terminal[1746]: segfault at bf286fec ip 01032835 sp bf286ff0 error 6 in libc-2.11.1.so[fd7000+153000]
May  3 22:06:54 orion-desktop kernel: [   69.288307] nautilus[1747]: segfault at bf5cdfbc ip 0897b835 sp bf5cdfc0 error 6 in libc-2.11.1.so[8920000+153000]
May  3 22:06:56 orion-desktop kernel: [   70.945712] nautilus[1749]: segfault at bf007ffc ip 0580a835 sp bf008000 error 6 in libc-2.11.1.so[57af000+153000]
May  3 22:06:58 orion-desktop kernel: [   72.599515] nautilus[1751]: segfault at bf159ffc ip 0603c835 sp bf15a000 error 6 in libc-2.11.1.so[5fe1000+153000]
May  3 22:06:59 orion-desktop kernel: [   74.227640] nautilus[1753]: segfault at bf32afec ip 04564835 sp bf32aff0 error 6 in libc-2.11.1.so[4509000+153000]
May  3 22:07:01 orion-desktop kernel: [   75.881361] nautilus[1755]: segfault at bf56effc ip 0868b2b3 sp bf56effc error 6 in libc-2.11.1.so[8624000+153000]
May  3 22:07:03 orion-desktop kernel: [   77.576576] nautilus[1757]: segfault at bef3bfcc ip 01283835 sp bef3bfd0 error 6 in libc-2.11.1.so[1228000+153000]
May  3 22:07:04 orion-desktop kernel: [   79.237936] nautilus[1759]: segfault at bf18dfcc ip 06c24835 sp bf18dfd0 error 6 in libc-2.11.1.so[6bc9000+153000]
May  3 22:07:06 orion-desktop kernel: [   80.921142] nautilus[1763]: segfault at bf009ffc ip 00bfc2b3 sp bf009ffc error 6 in libc-2.11.1.so[b95000+153000]
May  3 22:07:08 orion-desktop kernel: [   82.772842] gnome-session[1390]: segfault at beedbfec ip 009de835 sp beedbff0 error 6 in libc-2.11.1.so[983000+153000]
May  3 22:07:08 orion-desktop kernel: [   83.507499] [fglrx] IRQ 27 Disabled
May  3 22:07:09 orion-desktop pulseaudio[1785]: pid.c: Stale PID file, overwriting.
May  3 22:07:09 orion-desktop kernel: [   84.284419] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:07:09 orion-desktop kernel: [   84.286208] [fglrx] Firegl kernel thread PID: 1794
May  3 22:07:09 orion-desktop kernel: [   84.286569] [fglrx] IRQ 27 Enabled
May  3 22:07:10 orion-desktop kernel: [   84.689513] [fglrx] Gart USWC size:548 M.
May  3 22:07:10 orion-desktop kernel: [   84.689516] [fglrx] Gart cacheable size:215 M.
May  3 22:07:10 orion-desktop kernel: [   84.689519] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:07:10 orion-desktop kernel: [   84.689522] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:07:13 orion-desktop bonobo-activation-server (djzn-1978): could not associate with desktop session: Failed to connect to socket /tmp/dbus-Zg2bEneXnE: Conexão recusada
May  3 22:13:56 orion-desktop kernel: [  491.087265] [fglrx] IRQ 27 Disabled
May  3 22:13:57 orion-desktop kernel: [  491.921403] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:13:57 orion-desktop kernel: [  491.923181] [fglrx] Firegl kernel thread PID: 2425
May  3 22:13:57 orion-desktop kernel: [  491.923540] [fglrx] IRQ 27 Enabled
May  3 22:13:57 orion-desktop kernel: [  492.346532] [fglrx] Gart USWC size:548 M.
May  3 22:13:57 orion-desktop kernel: [  492.346534] [fglrx] Gart cacheable size:215 M.
May  3 22:13:57 orion-desktop kernel: [  492.346538] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:13:57 orion-desktop kernel: [  492.346540] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:14:06 orion-desktop kernel: [  500.766108] nautilus[2560]: segfault at bf3f8fec ip 00fbc835 sp bf3f8ff0 error 6 in libc-2.11.1.so[f61000+153000]
May  3 22:14:07 orion-desktop kernel: [  502.510323] nautilus[2626]: segfault at bef97ffc ip 040472b3 sp bef97ffc error 6 in libc-2.11.1.so[3fe0000+153000]
May  3 22:14:09 orion-desktop kernel: [  504.249157] nautilus[2630]: segfault at bf397fcc ip 07442835 sp bf397fd0 error 6 in libc-2.11.1.so[73e7000+153000]
May  3 22:14:11 orion-desktop kernel: [  505.957202] nautilus[2632]: segfault at bee9cfdc ip 03127835 sp bee9cfe0 error 6 in libc-2.11.1.so[30cc000+153000]
May  3 22:14:13 orion-desktop kernel: [  507.681687] nautilus[2639]: segfault at bf543fbc ip 077f6835 sp bf543fc0 error 6 in libc-2.11.1.so[779b000+153000]
May  3 22:14:14 orion-desktop kernel: [  509.386607] nautilus[2642]: segfault at bf2b9fdc ip 058f6835 sp bf2b9fe0 error 6 in libc-2.11.1.so[589b000+153000]
May  3 22:14:16 orion-desktop kernel: [  511.086790] nautilus[2644]: segfault at bf170ffc ip 06e33835 sp bf171000 error 6 in libc-2.11.1.so[6dd8000+153000]
May  3 22:14:18 orion-desktop kernel: [  512.851939] nautilus[2646]: segfault at bf44bffc ip 03b6a2b3 sp bf44bffc error 6 in libc-2.11.1.so[3b03000+153000]
May  3 22:14:20 orion-desktop kernel: [  514.584735] nautilus[2649]: segfault at bf001fdc ip 00d7d835 sp bf001fe0 error 6 in libc-2.11.1.so[d22000+153000]
May  3 22:14:21 orion-desktop kernel: [  516.289706] nautilus[2651]: segfault at bf3abfcc ip 01606835 sp bf3abfd0 error 6 in libc-2.11.1.so[15ab000+153000]
May  3 22:14:23 orion-desktop kernel: [  517.989178] nautilus[2653]: segfault at bf509fbc ip 00cfb835 sp bf509fc0 error 6 in libc-2.11.1.so[ca0000+153000]
May  3 22:14:25 orion-desktop kernel: [  519.671293] nautilus[2655]: segfault at bee34ffc ip 0381d2b3 sp bee34ffc error 6 in libc-2.11.1.so[37b6000+153000]
May  3 22:14:26 orion-desktop kernel: [  521.356903] nautilus[2657]: segfault at beec7ffc ip 00d492b3 sp beec7ffc error 6 in libc-2.11.1.so[ce2000+153000]
May  3 22:14:28 orion-desktop kernel: [  523.077512] nautilus[2659]: segfault at bee60ffc ip 015102b3 sp bee60ffc error 6 in libc-2.11.1.so[14a9000+153000]
May  3 22:14:30 orion-desktop kernel: [  525.037208] nautilus[2665]: segfault at bf154fdc ip 00953835 sp bf154fe0 error 6 in libc-2.11.1.so[8f8000+153000]
May  3 22:14:32 orion-desktop kernel: [  527.060216] nautilus[2671]: segfault at bf09bfbc ip 01dd3835 sp bf09bfc0 error 6 in libc-2.11.1.so[1d78000+153000]
May  3 22:14:34 orion-desktop kernel: [  528.861775] nautilus[2721]: segfault at befd2fbc ip 086be835 sp befd2fc0 error 6 in libc-2.11.1.so[8663000+153000]
May  3 22:14:36 orion-desktop kernel: [  530.545816] nautilus[2724]: segfault at bf290ffc ip 014152b3 sp bf290ffc error 6 in libc-2.11.1.so[13ae000+153000]
May  3 22:14:37 orion-desktop kernel: [  532.285229] nautilus[2726]: segfault at bf3dcfcc ip 08564835 sp bf3dcfd0 error 6 in libc-2.11.1.so[8509000+153000]
May  3 22:14:39 orion-desktop kernel: [  534.032688] nautilus[2728]: segfault at befb8ffc ip 00eaf2b3 sp befb8ffc error 6 in libc-2.11.1.so[e48000+153000]
May  3 22:14:41 orion-desktop kernel: [  535.739847] nautilus[2730]: segfault at bf3eaffc ip 0478b835 sp bf3eb000 error 6 in libc-2.11.1.so[4730000+153000]
May  3 22:14:42 orion-desktop kernel: [  537.451002] nautilus[2732]: segfault at bef91ffc ip 064fd2b3 sp bef91ffc error 6 in libc-2.11.1.so[6496000+153000]
May  3 22:14:44 orion-desktop kernel: [  539.140095] nautilus[2736]: segfault at bf598ffc ip 03cb2a2a sp bf599000 error 6 in libc-2.11.1.so[3bf6000+153000]
May  3 22:14:46 orion-desktop kernel: [  541.300415] gnome-session[2485]: segfault at bf077fdc ip 00d2d835 sp bf077fe0 error 6 in libc-2.11.1.so[cd2000+153000]
May  3 22:14:47 orion-desktop kernel: [  541.942496] [fglrx] IRQ 27 Disabled
May  3 22:14:47 orion-desktop pulseaudio[2752]: pid.c: Stale PID file, overwriting.
May  3 22:14:48 orion-desktop kernel: [  542.773911] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:14:48 orion-desktop kernel: [  542.774536] [fglrx] Firegl kernel thread PID: 2762
May  3 22:14:48 orion-desktop kernel: [  542.774775] [fglrx] IRQ 27 Enabled
May  3 22:14:48 orion-desktop kernel: [  543.164777] [fglrx] Gart USWC size:548 M.
May  3 22:14:48 orion-desktop kernel: [  543.164780] [fglrx] Gart cacheable size:215 M.
May  3 22:14:48 orion-desktop kernel: [  543.164783] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:14:48 orion-desktop kernel: [  543.164786] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:14:51 orion-desktop bonobo-activation-server (djzn-2876): could not associate with desktop session: Failed to connect to socket /tmp/dbus-MOYY6erN1r: Conexão recusada
May  3 22:14:57 orion-desktop pulseaudio[3014]: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-MOYY6erN1r: Conexão recusada
May  3 22:14:58 orion-desktop kernel: [  553.007874] xterm[2985]: segfault at bf2b0fbc ip 0016b835 sp bf2b0fc0 error 6 in libc-2.11.1.so[110000+153000]
May  3 22:14:58 orion-desktop kernel: [  553.210960] [fglrx] IRQ 27 Disabled
May  3 22:14:59 orion-desktop kernel: [  554.010907] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:14:59 orion-desktop kernel: [  554.012730] [fglrx] Firegl kernel thread PID: 3046
May  3 22:14:59 orion-desktop kernel: [  554.013090] [fglrx] IRQ 27 Enabled
May  3 22:14:59 orion-desktop kernel: [  554.427112] [fglrx] Gart USWC size:548 M.
May  3 22:14:59 orion-desktop kernel: [  554.427115] [fglrx] Gart cacheable size:215 M.
May  3 22:14:59 orion-desktop kernel: [  554.427119] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:14:59 orion-desktop kernel: [  554.427121] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:15:09 orion-desktop pulseaudio[3014]: ratelimit.c: 215 events suppressed
May  3 22:15:13 orion-desktop kernel: [  568.183353] metacity[3163]: segfault at bf097ffc ip 01023a2a sp bf098000 error 6 in libc-2.11.1.so[f67000+153000]
May  3 22:15:13 orion-desktop kernel: [  568.268211] nautilus[3167]: segfault at bee09fbc ip 048f2835 sp bee09fc0 error 6 in libc-2.11.1.so[4897000+153000]
May  3 22:15:15 orion-desktop kernel: [  570.058825] metacity[3233]: segfault at bf53efec ip 017a5835 sp bf53eff0 error 6 in libc-2.11.1.so[174a000+153000]
May  3 22:15:15 orion-desktop kernel: [  570.213987] nautilus[3234]: segfault at bf2e6ffc ip 07a12835 sp bf2e7000 error 6 in libc-2.11.1.so[79b7000+153000]
May  3 22:15:17 orion-desktop kernel: [  571.922096] metacity[3236]: segfault at befa6fdc ip 00f5a835 sp befa6fe0 error 6 in libc-2.11.1.so[eff000+153000]
May  3 22:15:17 orion-desktop kernel: [  572.185027] nautilus[3237]: segfault at bef84ffc ip 01cdb2b3 sp bef84ffc error 6 in libc-2.11.1.so[1c74000+153000]
May  3 22:15:19 orion-desktop kernel: [  573.808948] metacity[3239]: segfault at befbaffc ip 0102c835 sp befbb000 error 6 in libc-2.11.1.so[fd1000+153000]
May  3 22:15:19 orion-desktop kernel: [  574.208155] nautilus[3240]: segfault at bee5bffc ip 04070835 sp bee5c000 error 6 in libc-2.11.1.so[4015000+153000]
May  3 22:15:21 orion-desktop kernel: [  575.739415] metacity[3242]: segfault at bf36bfbc ip 01032835 sp bf36bfc0 error 6 in libc-2.11.1.so[fd7000+153000]
May  3 22:15:21 orion-desktop kernel: [  576.146594] nautilus[3243]: segfault at bf4f4fcc ip 078c2835 sp bf4f4fd0 error 6 in libc-2.11.1.so[7867000+153000]
May  3 22:15:23 orion-desktop kernel: [  577.621689] metacity[3245]: segfault at bf41cffc ip 00f9f835 sp bf41d000 error 6 in libc-2.11.1.so[f44000+153000]
May  3 22:15:23 orion-desktop kernel: [  578.137298] nautilus[3246]: segfault at bf562fdc ip 051a4835 sp bf562fe0 error 6 in libc-2.11.1.so[5149000+153000]
May  3 22:15:24 orion-desktop kernel: [  579.515996] metacity[3248]: segfault at bf1c9fcc ip 00da2835 sp bf1c9fd0 error 6 in libc-2.11.1.so[d47000+153000]
May  3 22:15:25 orion-desktop kernel: [  580.108996] nautilus[3249]: segfault at bee4cfdc ip 08303835 sp bee4cfe0 error 6 in libc-2.11.1.so[82a8000+153000]
May  3 22:15:26 orion-desktop kernel: [  581.381568] metacity[3251]: segfault at bf165fcc ip 00936835 sp bf165fd0 error 6 in libc-2.11.1.so[8db000+153000]
May  3 22:15:27 orion-desktop kernel: [  582.089578] nautilus[3252]: segfault at bf11efec ip 0359b835 sp bf11eff0 error 6 in libc-2.11.1.so[3540000+153000]
May  3 22:15:28 orion-desktop kernel: [  583.232246] metacity[3254]: segfault at bf4cbfec ip 00a11835 sp bf4cbff0 error 6 in libc-2.11.1.so[9b6000+153000]
May  3 22:15:29 orion-desktop kernel: [  584.056256] nautilus[3255]: segfault at bf103fbc ip 06cbe835 sp bf103fc0 error 6 in libc-2.11.1.so[6c63000+153000]
May  3 22:15:30 orion-desktop kernel: [  585.103869] metacity[3257]: segfault at bef46fcc ip 00b5d835 sp bef46fd0 error 6 in libc-2.11.1.so[b02000+153000]
May  3 22:15:31 orion-desktop kernel: [  586.023147] nautilus[3258]: segfault at bf405ffc ip 084f22b3 sp bf405ffc error 6 in libc-2.11.1.so[848b000+153000]
May  3 22:15:32 orion-desktop kernel: [  586.996636] metacity[3260]: segfault at bef55ffc ip 00ff42b3 sp bef55ffc error 6 in libc-2.11.1.so[f8d000+153000]
May  3 22:15:33 orion-desktop kernel: [  587.975198] nautilus[3261]: segfault at bf165ffc ip 02214a2a sp bf166000 error 6 in libc-2.11.1.so[2158000+153000]
May  3 22:15:34 orion-desktop kernel: [  588.864421] metacity[3263]: segfault at bf18cffc ip 0390a835 sp bf18d000 error 6 in libc-2.11.1.so[38af000+153000]
May  3 22:15:35 orion-desktop kernel: [  589.947742] nautilus[3264]: segfault at bef17ffc ip 06ad72b3 sp bef17ffc error 6 in libc-2.11.1.so[6a70000+153000]
May  3 22:15:36 orion-desktop kernel: [  590.753192] metacity[3266]: segfault at bf03cfbc ip 01000835 sp bf03cfc0 error 6 in libc-2.11.1.so[fa5000+153000]
May  3 22:15:37 orion-desktop kernel: [  591.903227] nautilus[3267]: segfault at bee19ffc ip 0726d2b3 sp bee19ffc error 6 in libc-2.11.1.so[7206000+153000]
May  3 22:15:38 orion-desktop kernel: [  592.611433] metacity[3269]: segfault at bf478ffc ip 01073a2a sp bf479000 error 6 in libc-2.11.1.so[fb7000+153000]
May  3 22:15:39 orion-desktop kernel: [  593.856691] nautilus[3270]: segfault at bf5e4fdc ip 03cd9835 sp bf5e4fe0 error 6 in libc-2.11.1.so[3c7e000+153000]
May  3 22:15:39 orion-desktop bonobo-activation-server (djzn-3283): could not associate with desktop session: Failed to connect to socket /tmp/dbus-bs8Ks7Ao4g: Conexão recusada
May  3 22:15:40 orion-desktop kernel: [  594.580597] metacity[3272]: segfault at bf219ffc ip 0101e2b3 sp bf219ffc error 6 in libc-2.11.1.so[fb7000+153000]
May  3 22:15:40 orion-desktop kernel: [  594.751094] [fglrx] IRQ 27 Disabled
May  3 22:15:41 orion-desktop kernel: [  595.571049] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:15:41 orion-desktop kernel: [  595.571886] [fglrx] Firegl kernel thread PID: 3302
May  3 22:15:41 orion-desktop kernel: [  595.572147] [fglrx] IRQ 27 Enabled
May  3 22:15:41 orion-desktop kernel: [  595.655031] nautilus[3273]: segfault at bf2f8fbc ip 07aea835 sp bf2f8fc0 error 6 in libc-2.11.1.so[7a8f000+153000]
May  3 22:15:41 orion-desktop kernel: [  595.976598] [fglrx] Gart USWC size:548 M.
May  3 22:15:41 orion-desktop kernel: [  595.976601] [fglrx] Gart cacheable size:215 M.
May  3 22:15:41 orion-desktop kernel: [  595.976605] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:15:41 orion-desktop kernel: [  595.976607] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:21:38 orion-desktop kernel: [  953.054876] [fglrx] IRQ 27 Disabled
May  3 22:21:39 orion-desktop kernel: [  953.857636] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:21:39 orion-desktop kernel: [  953.859428] [fglrx] Firegl kernel thread PID: 3652
May  3 22:21:39 orion-desktop kernel: [  953.859789] [fglrx] IRQ 27 Enabled
May  3 22:21:39 orion-desktop kernel: [  954.254159] [fglrx] Gart USWC size:548 M.
May  3 22:21:39 orion-desktop kernel: [  954.254162] [fglrx] Gart cacheable size:215 M.
May  3 22:21:39 orion-desktop kernel: [  954.254166] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:21:39 orion-desktop kernel: [  954.254168] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:21:48 orion-desktop kernel: [  962.648712] nautilus[3787]: segfault at bf158ffc ip 07b97a2a sp bf159000 error 6 in libc-2.11.1.so[7adb000+153000]
May  3 22:21:49 orion-desktop kernel: [  964.338937] nautilus[3852]: segfault at bf3b7ffc ip 059262b3 sp bf3b7ffc error 6 in libc-2.11.1.so[58bf000+153000]
May  3 22:21:51 orion-desktop kernel: [  966.018451] nautilus[3854]: segfault at bf3b5fec ip 00d64835 sp bf3b5ff0 error 6 in libc-2.11.1.so[d09000+153000]
May  3 22:21:53 orion-desktop kernel: [  967.750856] nautilus[3858]: segfault at bf43ffbc ip 03da3835 sp bf43ffc0 error 6 in libc-2.11.1.so[3d48000+153000]
May  3 22:21:55 orion-desktop kernel: [  969.696771] nautilus[3865]: segfault at bf515ffc ip 05dcba2a sp bf516000 error 6 in libc-2.11.1.so[5d0f000+153000]
May  3 22:21:56 orion-desktop kernel: [  970.753574] gnome-terminal[3868]: segfault at bee70ffc ip 004bf2b3 sp bee70ffc error 6 in libc-2.11.1.so[458000+153000]
May  3 22:21:57 orion-desktop kernel: [  971.582228] nautilus[3870]: segfault at bf5fdffc ip 06edca2a sp bf5fe000 error 6 in libc-2.11.1.so[6e20000+153000]
May  3 22:21:58 orion-desktop kernel: [  973.275771] nautilus[3872]: segfault at bef69ffc ip 048b32b3 sp bef69ffc error 6 in libc-2.11.1.so[484c000+153000]
May  3 22:22:00 orion-desktop kernel: [  974.968129] nautilus[3874]: segfault at bf2f0fdc ip 03c83835 sp bf2f0fe0 error 6 in libc-2.11.1.so[3c28000+153000]
May  3 22:22:02 orion-desktop kernel: [  976.676692] nautilus[3877]: segfault at bef95ffc ip 016c12b3 sp bef95ffc error 6 in libc-2.11.1.so[165a000+153000]
May  3 22:22:03 orion-desktop kernel: [  978.398796] nautilus[3879]: segfault at bf4dcffc ip 063b1835 sp bf4dd000 error 6 in libc-2.11.1.so[6356000+153000]
May  3 22:22:05 orion-desktop kernel: [  980.109206] nautilus[3881]: segfault at bf363ffc ip 0306c835 sp bf364000 error 6 in libc-2.11.1.so[3011000+153000]
May  3 22:22:07 orion-desktop kernel: [  981.807889] nautilus[3883]: segfault at bef07ffc ip 099f32b3 sp bef07ffc error 6 in libc-2.11.1.so[998c000+153000]
May  3 22:22:08 orion-desktop kernel: [  983.499784] nautilus[3885]: segfault at bf028fcc ip 06e02835 sp bf028fd0 error 6 in libc-2.11.1.so[6da7000+153000]
May  3 22:22:10 orion-desktop kernel: [  985.216158] nautilus[3887]: segfault at bf52cffc ip 0526e2b3 sp bf52cffc error 6 in libc-2.11.1.so[5207000+153000]
May  3 22:22:12 orion-desktop kernel: [  986.900098] nautilus[3889]: segfault at bf243ffc ip 04d082b3 sp bf243ffc error 6 in libc-2.11.1.so[4ca1000+153000]
May  3 22:22:14 orion-desktop kernel: [  988.613386] nautilus[3891]: segfault at bf0b3ffc ip 00c83a2a sp bf0b4000 error 6 in libc-2.11.1.so[bc7000+153000]
May  3 22:22:15 orion-desktop kernel: [  990.340316] nautilus[3893]: segfault at bf598ffc ip 094562b3 sp bf598ffc error 6 in libc-2.11.1.so[93ef000+153000]
May  3 22:22:17 orion-desktop kernel: [  992.063641] nautilus[3925]: segfault at bf13ffbc ip 01de0835 sp bf13ffc0 error 6 in libc-2.11.1.so[1d85000+153000]
May  3 22:22:19 orion-desktop kernel: [  993.763591] nautilus[3927]: segfault at beeb6fdc ip 08f12835 sp beeb6fe0 error 6 in libc-2.11.1.so[8eb7000+153000]
May  3 22:22:21 orion-desktop kernel: [  995.726828] nautilus[3929]: segfault at bf1a3fbc ip 08a34835 sp bf1a3fc0 error 6 in libc-2.11.1.so[89d9000+153000]
May  3 22:22:21 orion-desktop kernel: [  996.209000] gtk-logout-help[3932]: segfault at bf29dfdc ip 009a6835 sp bf29dfe0 error 6 in libc-2.11.1.so[94b000+153000]
May  3 22:22:22 orion-desktop kernel: [  997.493004] nautilus[3933]: segfault at bf21efcc ip 01158835 sp bf21efd0 error 6 in libc-2.11.1.so[10fd000+153000]
May  3 22:22:24 orion-desktop kernel: [  999.196525] nautilus[3935]: segfault at bf555fcc ip 03681835 sp bf555fd0 error 6 in libc-2.11.1.so[3626000+153000]
May  3 22:22:26 orion-desktop kernel: [ 1000.905645] nautilus[3937]: segfault at bf448fdc ip 05c9b835 sp bf448fe0 error 6 in libc-2.11.1.so[5c40000+153000]
May  3 22:22:28 orion-desktop kernel: [ 1002.598639] nautilus[3939]: segfault at bf52bffc ip 01019835 sp bf52c000 error 6 in libc-2.11.1.so[fbe000+153000]
May  3 22:22:29 orion-desktop kernel: [ 1004.338794] nautilus[3941]: segfault at bf115ffc ip 02b692b3 sp bf115ffc error 6 in libc-2.11.1.so[2b02000+153000]
May  3 22:22:31 orion-desktop kernel: [ 1005.926440] gtk-logout-help[3944]: segfault at bf2eafec ip 00717835 sp bf2eaff0 error 6 in libc-2.11.1.so[6bc000+153000]
May  3 22:22:31 orion-desktop kernel: [ 1006.287786] nautilus[3945]: segfault at bf58bffc ip 039c3835 sp bf58c000 error 6 in libc-2.11.1.so[3968000+153000]
May  3 22:22:33 orion-desktop kernel: [ 1007.997411] nautilus[3947]: segfault at bf58affc ip 06644835 sp bf58b000 error 6 in libc-2.11.1.so[65e9000+153000]
May  3 22:22:35 orion-desktop kernel: [ 1009.710924] nautilus[3949]: segfault at bf5ddfdc ip 03ae1835 sp bf5ddfe0 error 6 in libc-2.11.1.so[3a86000+153000]
May  3 22:22:36 orion-desktop kernel: [ 1011.435777] nautilus[3951]: segfault at bf214fdc ip 06a02835 sp bf214fe0 error 6 in libc-2.11.1.so[69a7000+153000]
May  3 22:22:38 orion-desktop kernel: [ 1013.124626] nautilus[3953]: segfault at bf51afdc ip 02e93835 sp bf51afe0 error 6 in libc-2.11.1.so[2e38000+153000]
May  3 22:22:40 orion-desktop kernel: [ 1014.843433] nautilus[3957]: segfault at bf076fec ip 07cb3835 sp bf076ff0 error 6 in libc-2.11.1.so[7c58000+153000]
May  3 22:22:42 orion-desktop kernel: [ 1016.560728] nautilus[3959]: segfault at bf436ffc ip 097fe2b3 sp bf436ffc error 6 in libc-2.11.1.so[9797000+153000]
May  3 22:22:43 orion-desktop kernel: [ 1018.252276] nautilus[3961]: segfault at bf5ffffc ip 08a2a835 sp bf600000 error 6 in libc-2.11.1.so[89cf000+153000]
May  3 22:22:45 orion-desktop kernel: [ 1019.976113] nautilus[3963]: segfault at bef43fbc ip 00d3b835 sp bef43fc0 error 6 in libc-2.11.1.so[ce0000+153000]
May  3 22:22:47 orion-desktop kernel: [ 1021.789616] nautilus[3969]: segfault at befd8fcc ip 05bfa835 sp befd8fd0 error 6 in libc-2.11.1.so[5b9f000+153000]
May  3 22:22:48 orion-desktop kernel: [ 1023.132949] gnome-session[3712]: segfault at bee1efec ip 007e3835 sp bee1eff0 error 6 in libc-2.11.1.so[788000+153000]
May  3 22:22:49 orion-desktop kernel: [ 1023.752426] [fglrx] IRQ 27 Disabled
May  3 22:22:49 orion-desktop pulseaudio[4000]: pid.c: Stale PID file, overwriting.
May  3 22:22:50 orion-desktop kernel: [ 1024.547510] [fglrx] GART Table is not in FRAME_BUFFER range 
May  3 22:22:50 orion-desktop kernel: [ 1024.549361] [fglrx] Firegl kernel thread PID: 4008
May  3 22:22:50 orion-desktop kernel: [ 1024.549730] [fglrx] IRQ 27 Enabled
May  3 22:22:50 orion-desktop kernel: [ 1024.951762] [fglrx] Gart USWC size:548 M.
May  3 22:22:50 orion-desktop kernel: [ 1024.951765] [fglrx] Gart cacheable size:215 M.
May  3 22:22:50 orion-desktop kernel: [ 1024.951769] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
May  3 22:22:50 orion-desktop kernel: [ 1024.951771] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
May  3 22:22:53 orion-desktop bonobo-activation-server (djzn-4111): could not associate with desktop session: Failed to connect to socket /tmp/dbus-ljHjnuiZqN: Conexão recusada
May  3 22:22:54 orion-desktop kernel: Kernel logging (proc) stopped.
May  3 22:22:54 orion-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="844" x-info="http://www.rsyslog.com"] exiting on signal 15.
May  3 22:24:25 orion-desktop kernel: imklog 4.2.0, log source = /proc/kmsg started.
May  3 22:24:25 orion-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="860" x-info="http://www.rsyslog.com"] (re)start
May  3 22:24:26 orion-desktop rsyslogd: rsyslogd's groupid changed to 103
May  3 22:24:26 orion-desktop rsyslogd: rsyslogd's userid changed to 101
```

---

### Post by Djzn.BR on 2010-05-05
**Update:**

Turns out that this may be a bug related to ATI hardware (fglrx or radeon) and this script:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141500/comments/18](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/141500/comments/18)

---

