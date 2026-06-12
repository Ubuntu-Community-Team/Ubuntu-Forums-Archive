---
title: "Segfaults in multiple applications"
date: 2010-08-04
forum: General Help
---

### Post by gus_zernial on 2010-08-04
I've got an Intel Atom/Nvidia ION nettop with newly-installed Ubuntu 10.04 Desktop and 2.6.32-24-generic-pae kernel. I'm using Nvidia restricted drivers with the ION. I'm getting frequent segfaults, typically followed by a system freeze of some kind.

I'm using chromium-browser, and the segfaults most often come while browsing, but as shown in the list below the segfaults occur in multiple applications (even FireFox if I use it instead of chromium-browser).

I'm baffled as to underlying cause. Can someone give me an idea what's wrong, or next steps to diagnose? Thx, Gus

------------------
Aug  1 21:04:40 FoxConn kernel: [  817.802053] polkitd[1289]: segfault at 9316f3d4 ip b749af14 sp bfad209c error 6 in libpolkit-gobject-1.so.0.0.0[b7492000+1c000]
Aug  1 21:04:44 FoxConn kernel: [  822.409584] gnome-panel[1276]: segfault at 85c5464 ip b6f0d6f7 sp bfb2f1e0 error 4 in libgobject-2.0.so.0.2400.1[b6ef3000+3d000]
Aug  1 21:04:45 FoxConn kernel: [  822.510487] indicator-apple[1492]: segfault at 0 ip (null) sp bf884390 error 14 in indicator-applet-session[8048000+7000]
Aug  2 06:57:17 FoxConn kernel: [  952.617958] gtk-window-deco[1408]: segfault at 50 ip b75a4246 sp bfece780 error 4 in libwnck-1.so.22.3.26[b7590000+36000]
Aug  2 06:57:17 FoxConn kernel: [  952.625176] wnck-applet[1414]: segfault at 50 ip b784060f sp bfe21100 error 4 in libwnck-1.so.22.3.26[b782c000+36000]
Aug  2 07:02:16 FoxConn kernel: [ 1252.007931] chrome[2106]: segfault at 60375648 ip 08c58635 sp bf9f73ec error 4 in chrome[8048000+2354000]
Aug  2 07:02:22 FoxConn kernel: [ 1257.607925] chrome[2291]: segfault at 13c5ba10 ip 08c58635 sp bf9f739c error 4 in chrome[8048000+2354000]
Aug  2 07:02:31 FoxConn kernel: [ 1267.319784] chrome[2322]: segfault at 14f25830 ip 08c58635 sp bf9e358c error 4 in chrome[8048000+2354000]
Aug  2 07:07:30 FoxConn kernel: [ 1565.823989] chrome[2404]: segfault at 67b49188 ip 08c58635 sp bf99829c error 4 in chrome[8048000+2354000]
Aug  2 09:08:47 FoxConn kernel: [ 6666.674137] apt-get[1627]: segfault at c11acaee ip b774a05e sp bf8ff3f0 error 7 in libapt-pkg-libc6.10-6.so.4.8.0[b770c000+c8000]
Aug  3 06:46:42 FoxConn kernel: [  495.920846] update-apt-xapi[1581]: segfault at 95c496b0 ip b734b522 sp bfa423f0 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[b7312000+c8000]
Aug  3 06:48:56 FoxConn kernel: [  629.592195] chrome[1442]: segfault at 1 ip 08865d4f sp b3981e50 error 6 in chrome[8048000+2354000]
Aug  3 06:49:02 FoxConn kernel: [  636.258872] chrome[1738]: segfault at 686c821 ip 0686c821 sp b3956180 error 14 in chrome[8048000+2354000]
Aug  3 06:49:05 FoxConn kernel: [  638.673423] chrome[1808]: segfault at 686c821 ip 0686c821 sp b3950180 error 14 in chrome[8048000+2354000]
Aug  3 06:49:50 FoxConn kernel: [  683.954582] chrome[1882]: segfault at 686c821 ip 0686c821 sp b3981180 error 14 in chrome[8048000+2354000]
Aug  3 06:50:32 FoxConn kernel: [  726.401484] chrome[1978]: segfault at 686c821 ip 0686c821 sp b3981180 error 14 in chrome[8048000+2354000]
Aug  3 06:50:41 FoxConn kernel: [  734.496198] nautilus[1042]: segfault at b0444084 ip b7710603 sp bf81fe4c error 4 in ld-2.11.1.so[b7703000+1b000]
Aug  3 06:53:28 FoxConn kernel: [  148.386072] NetworkManager[736]: segfault at b704ae60 ip b704ae60 sp bfbeab4c error 15
Aug  3 06:58:39 FoxConn kernel: [  459.424051] apt-check[1818]: segfault at 6d035c4a ip b73f7cbb sp bf891f00 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[b7395000+c8000]
Aug  3 06:59:19 FoxConn kernel: [  499.425490] apt-check[1844]: segfault at 6bf43ad2 ip b7364cbb sp bfd5d650 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[b7302000+c8000]
Aug  3 07:07:36 FoxConn kernel: [  996.680182] chrome[1556]: segfault at 4 ip 082cca3f sp bfadd2e4 error 4 in chrome[8048000+2354000]
Aug  3 07:09:44 FoxConn kernel: [ 1124.586342] apt-check[1881]: segfault at 6c2ebc9a ip b737acbb sp bf853020 error 4 in libapt-pkg-libc6.10-6.so.4.8.0[b7318000+c8000]
Aug  3 19:15:43 FoxConn kernel: [  850.870469] gconfd-2[1249]: segfault at 810ce38 ip b73e317f sp bfc98a20 error 4 in libgobject-2.0.so.0.2400.1[b73b9000+3d000]
Aug  3 19:20:49 FoxConn kernel: [ 1157.162312] chromium-browse[2352]: segfault at 800870a2 ip 800870a2 sp bfcc4c41 error 14
Aug  3 19:20:54 FoxConn kernel: [ 1162.339004] chromium-browse[2359]: segfault at 800870a2 ip 800870a2 sp bfcc4c41 error 14 in SYSV00000000 (deleted)[b5790000+a7000]
Aug  3 19:20:59 FoxConn kernel: [ 1166.796578] chromium-browse[2362]: segfault at 800870a2 ip 800870a2 sp bfcc4c41 error 14 in SYSV00000000 (deleted)[b547c000+3bb000]
Aug  3 19:20:59 FoxConn kernel: [ 1166.847120] chromium-browse[2161]: segfault at 640840aa ip 640840aa sp bf8bc331 error 14
Aug  3 19:21:02 FoxConn kernel: [ 1169.774984] chromium-browse[2404]: segfault at 83f72908 ip b695f60e sp bfae8bbc error 4 in libc-2.11.1.so[b687f000+153000]
Aug  3 19:21:36 FoxConn kernel: [ 1203.424556] chromium-browse[2447]: segfault at 83f72908 ip b686960e sp bfd3bf7c error 4 in libc-2.11.1.so[b6789000+153000]
Aug  3 19:21:54 FoxConn kernel: [ 1222.261089] gnome-terminal[2453]: segfault at 83f72908 ip b6efc60e sp bfa7970c error 4 in libc-2.11.1.so[b6e1c000+153000]
Aug  3 19:22:18 FoxConn kernel: [ 1246.178427] login[1162]: segfault at cb842e ip b77d8706 sp bff0fb78 error 4 in libc-2.11.1.so[b76f8000+153000]
Aug  3 19:22:35 FoxConn kernel: [ 1262.721376] login[2456]: segfault at cb842e ip b765f706 sp bfd3b528 error 4 in libc-2.11.1.so[b757f000+153000]
Aug  3 19:31:57 FoxConn kernel: [  456.433649] chromium-browse[1595]: segfault at bd559085 ip 08a3f89c sp bfd48800 error 4 in chromium-browser[8048000+25ef000]
Aug  3 19:32:03 FoxConn kernel: [  462.905900] chromium-browse[1813]: segfault at bd558e15 ip 08a3f89c sp bfd48590 error 4 in chromium-browser[8048000+25ef000]
Aug  3 19:32:04 FoxConn kernel: [  464.095766] chromium-browse[1816]: segfault at bd558e15 ip 08a3f89c sp bfd48590 error 4 in chromium-browser[8048000+25ef000]
Aug  3 19:32:15 FoxConn kernel: [  475.186747] chromium-browse[1883]: segfault at bd37c365 ip 08a3f89c sp bfb6bae0 error 4 in chromium-browser[8048000+25ef000]
Aug  3 19:32:38 FoxConn kernel: [  498.146168] chromium-browse[1926]: segfault at bd37c365 ip 08a3f89c sp bfb6bae0 error 4 in chromium-browser[8048000+25ef000]
Aug  3 19:32:41 FoxConn kernel: [  500.821615] chromium-browse[1929]: segfault at bd37c365 ip 08a3f89c sp bfb6bae0 error 4 in chromium-browser[8048000+25ef000]
Aug  3 19:45:18 FoxConn kernel: [  267.387501] NetworkManager[685]: segfault at 88fffffc ip 0806b19c sp 89000000 error 6 in NetworkManager[8048000+83000]
Aug  3 19:45:18 FoxConn kernel: [  267.659009] NetworkManager[1817]: segfault at 6000c ip b74d52d6 sp bfa3dcd0 error 4 in libgobject-2.0.so.0.2400.1[b74af000+3d000]
Aug  3 19:45:18 FoxConn kernel: [  267.977270] NetworkManager[1819]: segfault at 6000c ip b73f82d6 sp bfe6af00 error 4 in libgobject-2.0.so.0.2400.1[b73d2000+3d000]
Aug  3 19:45:18 FoxConn kernel: [  268.246171] NetworkManager[1821]: segfault at 6000c ip b75022d6 sp bfe20c80 error 4 in libgobject-2.0.so.0.2400.1[b74dc000+3d000]
Aug  3 19:45:19 FoxConn kernel: [  268.477276] NetworkManager[1823]: segfault at 6000c ip b73562d6 sp bfd5c660 error 4 in libgobject-2.0.so.0.2400.1[b7330000+3d000]
Aug  3 19:45:19 FoxConn kernel: [  268.727833] NetworkManager[1826]: segfault at 6000c ip b74c42d6 sp bfb39810 error 4 in libgobject-2.0.so.0.2400.1[b749e000+3d000]
Aug  3 19:45:19 FoxConn kernel: [  269.011706] NetworkManager[1828]: segfault at 6000c ip b74c22d6 sp bf8fa7e0 error 4 in libgobject-2.0.so.0.2400.1[b749c000+3d000]
Aug  3 19:45:19 FoxConn kernel: [  269.263922] NetworkManager[1830]: segfault at 6000c ip b745f2d6 sp bf9e6c40 error 4 in libgobject-2.0.so.0.2400.1[b7439000+3d000]
Aug  3 19:45:20 FoxConn kernel: [  269.549031] NetworkManager[1832]: segfault at 6000c ip b74242d6 sp bf9cfd80 error 4 in libgobject-2.0.so.0.2400.1[b73fe000+3d000]
Aug  3 19:45:20 FoxConn kernel: [  269.828816] NetworkManager[1834]: segfault at 6000c ip b75312d6 sp bfbe50d0 error 4 in libgobject-2.0.so.0.2400.1[b750b000+3d000]
Aug  3 19:49:32 FoxConn kernel: [  521.439005] gnome-terminal[1551]: segfault at 0 ip b7868bdd sp bfe27e80 error 4 in libvte.so.9.12.1[b7832000+8c000]
Aug  4 11:55:52 FoxConn kernel: [ 8687.272760] apt-get[2504]: segfault at ef1ba9fc ip b77c32cb sp bfd00660 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b7778000+c8000]
Aug  4 11:56:16 FoxConn kernel: [ 8711.221848] apt-get[2508]: segfault at ef2339fc ip b783c2cb sp bfde6870 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b77f1000+c8000]
Aug  4 11:56:40 FoxConn kernel: [ 8735.398192] apt-get[2529]: segfault at ef0c19fc ip b76ca2cb sp bff0d510 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b767f000+c8000]
Aug  4 12:00:54 FoxConn kernel: [ 8989.793271] aptitude[2554]: segfault at d9f97e74 ip b77f9885 sp bfb8b330 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b77c1000+c8000]
Aug  4 12:00:58 FoxConn kernel: [ 8993.619478] apt-check[2636]: segfault at d958de74 ip b71fd885 sp bffd5bb0 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b71c5000+c8000]
Aug  4 12:02:57 FoxConn kernel: [ 9112.991593] aptitude[2644]: segfault at d9f74e74 ip b77d6885 sp bff43fa0 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b779e000+c8000]
Aug  4 12:03:12 FoxConn kernel: [ 9128.159587] aptitude[2646]: segfault at d9f2ce74 ip b778e885 sp bfcfce50 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b7756000+c8000]
Aug  4 12:03:26 FoxConn kernel: [ 9141.514251] aptitude[2647]: segfault at d9ea5e74 ip b7707885 sp bf88f550 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b76cf000+c8000]
Aug  4 12:03:51 FoxConn kernel: [ 9166.524127] aptitude[2648]: segfault at d9e1be74 ip b767d885 sp bfb0eef0 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b7645000+c8000]
Aug  4 12:04:11 FoxConn kernel: [ 9187.004734] chromium-browse[2450]: segfault at b34cc0b4 ip 08a543a8 sp bfeabc70 error 4 in chromium-browser (deleted)[8048000+25fc000]
Aug  4 12:05:06 FoxConn kernel: [ 9241.382403] chromium-browse[2713]: segfault at bb3ce04c ip 08a538d2 sp bfc68200 error 4 in chromium-browser[8048000+25ed000]
Aug  4 12:11:15 FoxConn kernel: [  251.628877] apt-get[1430]: segfault at da182e74 ip b76ab885 sp bfd8d070 error 5 in libapt-pkg-libc6.10-6.so.4.8.0[b7673000+c8000]
Aug  4 13:44:56 FoxConn kernel: [  334.349558] chromium-browse[1767]: segfault at c381ffff ip b7009eeb sp bfb9df50 error 5 in libcairo.so.2.10800.10[b6ff2000+77000]
Aug  4 13:45:02 FoxConn kernel: [  339.683482] gnome-terminal[1915]: segfault at c381ffff ip b6d57eeb sp bfbbecd0 error 5 in libcairo.so.2.10800.10[b6d40000+77000]
Aug  4 13:45:24 FoxConn kernel: [  361.800390] chromium-browse[1980]: segfault at c381ffff ip b7061eeb sp bfdd6450 error 5 in libcairo.so.2.10800.10[b704a000+77000]
Aug  4 13:45:24 FoxConn kernel: [  361.901141] chromium-browse[1917]: segfault at c381ffff ip b70a0eeb sp bf83c630 error 5 in libcairo.so.2.10800.10[b7089000+77000]
Aug  4 13:45:34 FoxConn kernel: [  371.942066] indicator-apple[1521]: segfault at c381ffff ip b6d73eeb sp bf90d0a0 error 5 in libcairo.so.2.10800.10[b6d5c000+77000]
Aug  4 13:45:34 FoxConn kernel: [  371.968764] gnome-panel[1340]: segfault at c381ffff ip b7036eeb sp bfb21890 error 5 in libcairo.so.2.10800.10[b701f000+77000]
Aug  4 13:45:34 FoxConn kernel: [  372.343810] gnome-panel[2022]: segfault at c381ffff ip b70faeeb sp bf889570 error 5 in libcairo.so.2.10800.10[b70e3000+77000]

---

### Post by WorMzy on 2010-08-04
Sounds like you've either got some dodgy memory, or your pae kernel is messing up.

If you need the extra memory, then consider installing 64-bit Ubuntu. If you don't need the extra memory, or can't use 64-bit for whatever reason, then consider switching to a non-pae kernel.

---

### Post by gus_zernial on 2010-08-04
I thought of the possibility of dodgy memory, and I note that I had previously installed Kubuntu on this system and saw some problems there as well.

But I ran memtest86 and got zero errors. Is that indicative, or could I have dodgy memory anyway?

Thx, Gus

---

### Post by WorMzy on 2010-08-04
I'm not sure whether mem test tests all your RAM, or just the first 4GB. I'd expect it to test all of it though, so if it failed to find any problems then it'd be safe to surmise that it's your pae kernel at fault. Try using a non-pae kernel and see if the same issues occur.

---

