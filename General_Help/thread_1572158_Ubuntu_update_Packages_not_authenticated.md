---
title: "Ubuntu update Packages not authenticated"
date: 2010-09-10
forum: General Help
---

### Post by BSG Fan on 2010-09-10
Hi I have a doubt
well, in fact I am scared to download a package that may harm my pc.
Why the fright? well, I read something like said:
[CENTER]
Update Packages not authenticated”[/CENTER]

so imagine.

I wonder why (and how) a 'contaminated' update/package can get access to the Ubuntu server.

Out there somebody can help me what I have on my desktop waiting for my approval to download?

Help

The information of those updates is as follows:

1- Firefox
Changes for the versions:
3.6.8+build1+nobinonly-0ubuntu0.10.04.1
3.6.9+build1+nobinonly-0ubuntu0.10.04.1

Version 3.6.9+build1+nobinonly-0ubuntu0.10.04.1: 

  * New upstream release v3.6.9 (FIREFOX_3_6_9_BUILD1)
    - see USN-975-1

  * Add support for mozilla breakpad symbols and in turn enable
    crashreporter (LP: #623962)
    - update debian/control
    - update debian/rules


==========

2- Firefox-branding
Changes for the versions:
3.6.8+build1+nobinonly-0ubuntu0.10.04.1
3.6.9+build1+nobinonly-0ubuntu0.10.04.1

Version 3.6.9+build1+nobinonly-0ubuntu0.10.04.1: 

  * New upstream release v3.6.9 (FIREFOX_3_6_9_BUILD1)
    - see USN-975-1

  * Add support for mozilla breakpad symbols and in turn enable
    crashreporter (LP: #623962)
    - update debian/control
    - update debian/rules
============
3- Firefox-gnome support
Changes for the versions:
3.6.8+build1+nobinonly-0ubuntu0.10.04.1
3.6.9+build1+nobinonly-0ubuntu0.10.04.1

Version 3.6.9+build1+nobinonly-0ubuntu0.10.04.1: 

  * New upstream release v3.6.9 (FIREFOX_3_6_9_BUILD1)
    - see USN-975-1

  * Add support for mozilla breakpad symbols and in turn enable
    crashreporter (LP: #623962)
    - update debian/control
    - update debian/rules
============
4- Mountall
Changes for the versions:
2.15.1
2.15.2

Version 2.15.2: 

  * SECURITY UPDATE: do not leave writable udev rules file around.
    - src/mountall.c: set umask correctly (LP: #591807).
    - debian/preinst: remove boot-time udev rules file.
    - CVE-2010-2961
================
5- Seamonkey browser
Changes for the versions:
2.0.6+build1+nobinonly-0ubuntu0.10.04.1
2.0.7+build1+nobinonly-0ubuntu0.10.04.1

Version 2.0.7+build1+nobinonly-0ubuntu0.10.04.1: 

  * New upstream release v2.0.7 (SEAMONKEY_2_0_7_BUILD1)

  * SECURITY UPDATES:
  * MFSA 2010-49: Miscellaneous memory safety hazards (rv:1.9.2.9/ 1.9.1.12)
    - CVE-2010-3169
  * MFSA 2010-50: Frameset integer overflow vulnerability
    - CVE-2010-2765
  * MFSA 2010-51: Dangling pointer vulnerability using DOM plugin array
    - CVE-2010-2767
  * MFSA 2010-52: Windows XP DLL loading vulnerability
    - CVE-2010-3131
  * MFSA 2010-53: Heap buffer overflow in nsTextFrameUtils::TransformText
    - CVE-2010-3166
  * MFSA 2010-54: Dangling pointer vulnerability in nsTreeSelection
    - CVE-2010-2760
  * MFSA 2010-55: XUL tree removal crash and remote code execution
    - CVE-2010-3168
  * MFSA 2010-56: Dangling pointer vulnerability in nsTreeContentView
    - CVE-2010-3167
  * MFSA 2010-57: Crash and remote code execution in normalizeDocument
    - CVE-2010-2766
  * MFSA 2010-58: Crash on Mac using fuzzed font in data: URL
    - CVE-2010-2770
  * MFSA 2010-60: XSS using SJOW scripted functio
    - CVE-2010-2763
  * MFSA 2010-61: UTF-7 XSS by overriding document charset using <object> 
    type attribute
    - CVE-2010-2768
  * MFSA 2010-62: Copy-and-paste or drag-and-drop into designMode document 
    allows XSS
    - CVE-2010-62
  * MFSA 2010-63: Information leak via XMLHttpRequest statusText
    - CVE-2010-63

  * Refresh patches for new upstream version
    - update debian/patches/seamonkey-fsh.patch 
  * Fix LP: #593571 - searching for am-newsblog.xul in the wrong chrome package
    Install the newsblog.js XPCOM component
    - update debian/seamonkey-mailnews.install
==============
6- Xulrunner-1.9.2
Changes for the versions:
1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1
1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1

Version 1.9.2.9+build1+nobinonly-0ubuntu0.10.04.1: 

  * New upstream release v1.9.2.9 (FIREFOX_3_6_9_BUILD1)
    - see USN-975-1

  [ Micah Gersten <micahg@ubuntu.com> ]
  * Add patch to allow building with system NSPR less than 4.8.6
    - add debian/patches/fix_build_w_nspr_less_than_486.patch
    - update debian/series
==========


Well, hope receive some light, thank you
=)

Thanks in advance and have a great day,

BSG Fan

---

### Post by BSG Fan on 2010-09-10
What can be?

---

### Post by BSG Fan on 2010-09-11
Nobody has answered :(

Any answer?

---

### Post by sikander3786 on 2010-09-11
Have you tried changing your update server? Set to Main preferably and see if it is sorted out.

It is not the contaminated package I think, it is the server not authenticating your territory. Change the server and let us know what happens.

---

### Post by BSG Fan on 2010-09-11
> **sikander3786 said:**
> Have you tried changing your update server? Set to Main preferably and see if it is sorted out.

It is not the contaminated package I think, it is the server not authenticating your territory. Change the server and let us know what happens.

Hey sikander3786
Yes, you are right.
How to know it if I don't ask?
Thanks you so much for be the one who educated me about that issue.
You rock
):P

Me

---

### Post by hoakz on 2010-10-08
I solved this problem by updating the sources.

Seems there might have been some change I needed to get synced.

Edit: I already had the right territory selected though.

---

