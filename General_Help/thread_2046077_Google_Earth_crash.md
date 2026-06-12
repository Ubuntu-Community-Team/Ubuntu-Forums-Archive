---
title: "Google Earth crash"
date: 2012-08-22
forum: General Help
---

### Post by jimfl on 2012-08-22
Google Earth starts to load, displays the opening graphic and Start-up Tips, then shows the main window for a split second and crashes.

I've downloaded the latest Linux version, installed it, uninstalled it, and tried again with the same results. (Google Earth worked fine before I upgraded from Ubuntu 11.10 to 12.04.)

I have a Dell Inspiron 530 desktop with  an Intel® G33 x86/MMX/SSE2 graphics card.

Thanks for any help,

Jim

---

### Post by NM5TF on 2012-08-22
where did you download it from???

I went to the official GE site & followed the directions posted there...it
installed & works fine with no problems.....

I am also using 12.04 on a Dell Inspiron 531s, but I have a Nvidia graphics
card....don't know why it should make any difference what card you have...

Tommy

---

### Post by jimfl on 2012-08-22
Yes, I downloaded it from the official site: 
[https://www.google.com/earth/download/ge/agree.html](https://www.google.com/earth/download/ge/agree.html)

When I try to open the program from Terminal, it does the same thing. Terminal also gives me this message:
"We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data have been written:

Major Version 6
Minor Version 2
Build Number 0002
Build Date Apr 14 2012
Build Time 01:09:37
OS Type 3
OS Major Version 3
OS Minor Version 2
OS Build Version 0
OS Patch Version 0
Crash Signal 11
Crash Time 1345664710
Up Time 7.94779

Stacktrace from glibc:
./libgoogleearth_free.so(+0xc645b)[0x77245b]
./libgoogleearth_free.so(+0xc66a3)[0x7726a3]
[0xd4d400]
./libauth.so(_ZN5earth4auth12LoginProcess12AsyncDoLoginEb+0x5d)[0x65797d]
./libauth.so(_ZN5earth4auth12AsyncDoLoginEPv+0x48)[0x6579e8]
/lib/i386-linux-gnu/libpthread.so.0(+0x6d4c)[0x97cd4c]
/lib/i386-linux-gnu/libc.so.6(clone+0x5e)[0x6988ace]
[0x6988ace]

---

### Post by kimberley on 2012-09-12
Similar problem to above. Google Earth has crashed after installation of 12.4 on xubuntu.  I have tried everything I know ( not a lot) without success - any ideas greatly appreciated.):P

---

### Post by jimfl on 2012-09-12
> **kimberley said:**
> Similar problem to above. Google Earth has crashed after installation of 12.4 on xubuntu.  I have tried everything I know ( not a lot) without success - any ideas greatly appreciated.):P

Discovered a workaround elsewhere on the Net. As soon as the Startup Tips box appears, IMMEDIATELY close it by clicking on the little x at the top right of the box. GE then finishes loading and works correctly.

---

### Post by frankvdh on 2012-09-12
In the same boat... crashes as soon as it starts. Don't even get to see the Startup Tips box.

Tried numerous re-installs of various versions of GE 6 in various ways. Tried installing all kinds of lsb-core and suchlike packages.

Running 12.04LTS on a i7 IvyBridge PC, with just the onboard Intel graphics controller. (Had an ATI 7870 card, but Ubuntu didn't like it at all).

---

### Post by pwabrahams on 2012-11-02
I'm running Kubuntu 12.04 on a Lenovo Z580 laptop.  I just downloaded the 64-bit version of Google Earth from Google, installed it, and tried to run it.  The installation had no obvious problems, but when I tried to start GE I got the "caught signal 11" message that a number of others have reported.  Yet some folks do seem to have been able to get GE going.  What's the secret?  And where in the Google empire can I report this bug and see if Google has an answer for it?

---

### Post by mogdad on 2012-11-04
Same problem, different setup (12.04 LTS on Dell Dimension). Used to work fine with 10.04 LTS.

Installed from the official Google site, crashed. Tried "sudo apt-get upgrade google-earth" but still crashes. As with others I only get as far as the first screen - crashes before the tips window appears.

---

