---
title: "Open Office won't start - soffice.bin ld-2.11.1.so issue?"
date: 2011-02-12
forum: General Help
---

### Post by wgstelz on 2011-02-12
Hi All, Thanks in advace for reading my post. 

I have been suffering through this open office issue for months. I have done a bunch of research and tried a number of things to fix my problem.

None of the open office apps launch. I see the splash screen flash and that is it. I don't see any oo proccess. in messages, syslog and kern.log I see the following entries:
kernel: [  949.522617] soffice.bin[2130]: segfault at 4 ip 00a784d2 sp bf8e1ee8 error 4 in ld-2.11.1.so[a6e000+1b000]
kernel: [  953.324315] soffice.bin[2149]: segfault at 4 ip 003b64d2 sp bf9e4558 error 4 in ld-2.11.1.so[3ac000+1b000]
kernel: [   50.283977] __ratelimit: 30 callbacks suppressed

I have tried the obvious... eg.. uninstall and reinstall oo and java, swapped out memory and ran memtest, tried launching oo apps in console window to see if I get more feedback...

I have a feeling that java could be part of the issue... I have some weird problems with some java apps in firefox and chrome.... 

Any ideas will be greatly appreciated.

Thanks!!

fyi... some general system info 

10.04 - all LTS patches
uname - 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
gnome
oo runs on live cd

---

### Post by wgstelz on 2011-02-27
bump ... anybody have any ideas?

---

