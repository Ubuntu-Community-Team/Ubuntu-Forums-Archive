---
title: "Frequent crashes after 11.04 upgrade"
date: 2011-05-22
forum: General Help
---

### Post by Okuryo on 2011-05-22
I upgraded my desktop computer from 10.10 to 11.04 a few days after it came out.  Since about a week ago, I started to experience weird crashes: sometimes the screen just goes black and I have to restart the computer or it won't respond, and quite often processes get segfaults and crash.

I thought Unity might be the problem, but I changed to Ubuntu Classing and I still get crashes, so it's not it.

The kernel version is 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux.

Here are some examples I grep'd out of [FONT="Courier New"]/var/log/syslog[/FONT]:
```

kernel: [ 4078.631895] aqueue:src[2307]: segfault at 502232c3 ip 00e4fde6 sp b2edbf20 error 4 in libgstreamer-0.10.so.0.28.0[df7000+c3000]
kernel: [ 4695.743285] chromium-browse[3367]: segfault at ffffff95 ip b6072e27 sp bfb7d14d error 4 in chromium-browser[b4a51000+2e49000]
kernel: [  202.902913] chromium-browse[2247]: segfault at 4bf5583 ip b6a6a5fb sp bfd00b00 error 4 in chromium-browser[b4905000+2e49000]
kernel: [ 1425.807425] chrome[2367]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [ 1448.074747] chrome[2387]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [ 1476.307454] chrome[2409]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [ 1654.692691] chrome[2235]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [ 1673.566270] chrome[2430]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [ 1829.207176] duplicity[2011]: segfault at 102ec94 ip 080da5e6 sp bf969490 error 4 in python2.7[8048000+1f0000]
kernel: [10192.853285] chromium-browse[2810]: segfault at a ip b57fb317 sp bfc73c40 error 4 in chromium-browser[b4a4e000+2e49000]
kernel: [10541.983166] chrome[2692]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [10752.033930] chrome[3025]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [10804.174747] chrome[3055]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [10984.579899] chrome[3061]: segfault at 0 ip 09886038 sp bff58450 error 6 in chrome[8048000+2b83000]
kernel: [11086.278431] vlc[3139]: segfault at bd212004 ip 003b6067 sp b4a668fc error 4 in libc-2.13.so[2d0000+15a000]
kernel: [11337.391837] vlc[3205]: segfault at c ip 00e610c2 sp b4857fb0 error 4 in libc-2.13.so[df4000+15a000]
kernel: [11486.973345] chromium-browse[2889]: segfault at 4e656c68 ip b57fb263 sp bfc73c40 error 4 in chromium-browser[b4a4e000+2e49000]
kernel: [12007.621118] chromium-browse[3361]: segfault at a7914a94 ip b57f24bb sp bfc73ba0 error 4 in chromium-browser[b4a4e000+2e49000]
kernel: [12081.398201] chromium-browse[3526]: segfault at 328 ip b6235be2 sp bfc712d0 error 4 in chromium-browser[b4a4e000+2e49000]
kernel: [12591.435450] chromium-browse[2783]: segfault at 4628247e ip ad4e02bb sp b0a46d7c error 6
kernel: [12693.628832] chromium-browse[3713]: segfault at ad317c33 ip ad317c33 sp b444de60 error 4
kernel: [12697.095392] chromium-browse[3901]: segfault at 0 ip b57ebf77 sp bfbef690 error 4 in chromium-browser[b49c2000+2e49000]
kernel: [12738.712522] transmission-gt[3381]: segfault at c4cc0 ip 000c4cc0 sp b763dc0c error 4 in libgdk-x11-2.0.so.0.2400.4[110000+95000]
kernel: [12849.313373] chromium-browse[3689]: segfault at 0 ip b534cdf3 sp b0acb9a0 error 4 in chromium-browser[b4a9e000+2e49000]
kernel: [12877.113360] duplicity[4027]: segfault at fff86c8d ip 080ce74a sp bf9927e4 error 4 in python2.7[8048000+1f0000]
kernel: [13212.117012] chromium-browse[4100]: segfault at 700d8640 ip ad4bd6ee sp b095ed78 error 6
kernel: [13295.860515] chromium-browse[4478]: segfault at 46279928 ip 4ddcddd0 sp bfee7200 error 4 in libflashplayer.so[4d69e000+bc1000]
kernel: [   62.231061] ubuntuone-launc[2037]: segfault at 1ce36dc ip 080bcecc sp bfe14670 error 4 in python2.7[8048000+1f0000]
kernel: [  171.803733] duplicity[2195]: segfault at 1a0aea4 ip 080bcecc sp bfcec2e0 error 4 in python2.7[8048000+1f0000]
kernel: [ 1059.308301] chromium-browse[3180]: segfault at a6ecffcc ip b57b2247 sp bfa8a490 error 4 in chromium-browser[b4a05000+2e49000]
kernel: [   86.062755] ubuntuone-syncd[2019]: segfault at 16d6848 ip 080bd7b3 sp bfc16610 error 6 in python2.7[8048000+1f0000]
kernel: [  100.576560] ubuntu-sso-logi[2048]: segfault at 0 ip   (null) sp bff6a35c error 4 in libdbus-1.so.3.5.4[110000+3b000]
kernel: [  117.829863] chromium-browse[2131]: segfault at 20 ip 669e0250 sp a8b5c2f8 error 4 in libsoftokn3.so[669c1000+37000]
kernel: [  155.968611] chromium-browse[2191]: segfault at 20 ip 01078250 sp b04d2558 error 4 in libsoftokn3.so[1059000+37000]
kernel: [ 1292.766167] ubuntuone-launc[2491]: segfault at 167fa48 ip 080bdafe sp bff7c920 error 4 in python2.7[8048000+1f0000]
kernel: [ 1428.168884] compiz[2147]: segfault at a7e55f08 ip 08426abd sp bfc59230 error 6 in libunityshell.so[83c8000+13e000]
kernel: [ 2058.095141] duplicity[3865]: segfault at 7d32f8 ip 080bcecc sp bfb8f410 error 4 in python2.7[8048000+1f0000]
kernel: [27082.740645] chromium-browse[2877]: segfault at 170 ip b61bdd0e sp bfa42bd0 error 4 in chromium-browser[b4971000+2e49000]
kernel: [27082.740645] chromium-browse[2877]: segfault at 170 ip b61bdd0e sp bfa42bd0 error 4 in chromium-browser[b4971000+2e49000]
[ 1210.114774] chromium-browse[2050]: segfault at 20 ip 0c69e250 sp
 b09c1558 error 4 in libsoftokn3.so[c67f000+37000]
kernel: [ 5244.006805] applet.py[2147]: segfault at 14f8b30 ip 080bcecc sp 
bff08620 error 4 in python2.7[8048000+1f0000]
kernel: [10071.499317] chromium-browse[2372]: segfault at a785c220 ip b56bd
753 sp bfa9a780 error 4 in chromium-browser[b4911000+2e49000]
kernel: [12075.545700] chromium-browse[4226]: segfault at 938d1554 ip b5744
ff3 sp bfa991b0 error 4 in chromium-browser[b4911000+2e49000]
kernel: [  473.225488] chromium-browse[2080]: segfault at 71b8b190 ip b585fee3 sp bfdf30a0 error 4 in chromium-browser[b4a98000+2e49000]

```

What might cause this kind of problem?  How do I investigate further?
Thanks

---

### Post by corncob on 2011-05-22
Did this just happen after you installed chromium?

---

### Post by ericzmeh on 2011-05-22
Have you tried running a disk check on your OS drive?

---

### Post by linuxinstalledfromhdd on 2011-05-22
I upgraded as well to 11.04 after it was released, and I rolled back my system in a couple of days use.  I'm happy with 10.10 for now.

---

### Post by corncob on 2011-05-22
> **linuxinstalledfromhdd said:**
> I upgraded as well to 11.04 after it was released, and I rolled back my system in a couple of days use.  I'm happy with 10.10 for now.

I've been thinking about doing that too but at the moment I'm downloading pinguy 11.04 ( [http://www.webupd8.org/2011/05/pinguy-os-1104-released-with-classic.html](http://www.webupd8.org/2011/05/pinguy-os-1104-released-with-classic.html) ).  It sounds interesting.

---

### Post by Okuryo on 2011-05-23
> **corncob said:**
> Did this just happen after you installed chromium?
No, Chromium has been installed on my computer even before I upgraded.

---

### Post by linuxinstalledfromhdd on 2011-05-23
How did you install Chromium? From a PPA or direct downloaded deb package from a web site? Or?

---

### Post by hawthornso23 on 2011-05-23
I once had a bunch of applications frequently segfaulting like that. It turned out to be some memory going bad. Suggest you memcheck and eliminate this possibility.

---

### Post by Okuryo on 2011-05-23
> **linuxinstalledfromhdd said:**
> How did you install Chromium? From a PPA or direct downloaded deb package from a web site? Or?

It's from the Chromium Daily PPA (ppa:chromium-daily/ppa).

---

### Post by Okuryo on 2011-05-23
> **hawthornso23 said:**
> I once had a bunch of applications frequently segfaulting like that. It turned out to be some memory going bad. Suggest you memcheck and eliminate this possibility.

I booted into Memtest, and after a while it completed one pass with 0 errors.
Does that eliminate the possibility of a memory problem?

---

### Post by linuxinstalledfromhdd on 2011-05-23
It does look like hardware to me, but it depends. 

Sometimes its just better to install from a fresh disc or live usb stick of Ubuntu rather than upgrade.  I have seen quite a few complaints about the upgrading from 10.10 to 11.04. .

On the other hand I wasn't terribly happy with 11.04 so I rolled my system back to 10.10.

---

### Post by Okuryo on 2011-06-09
After about 12 hours, memtest found 3 errors in my memory (in slot #1).

I bought a new RAM (2 GB too), put it in slot #2.
Worked for 30 minutes, crashed.
Moved to slot #1, didn't boot:
Kernel panic: unable to mount /root on ... (unknown block 00)
Added original memory in slot #2, booted into recovery mode.  Sudden reboot.  Same error.
Got old one out, waited 20 minutes, booted and worked fine. Will crash again.

---

### Post by LarryNG on 2011-06-09
Related to the numerous reports of black screens, I hope this information might help solve some of the problems.

I installed 11.04 on two older computers, a P3 and P4. Both computers previously had Windows XP which worked fine. Both of the computers experienced the black screen shortly after the Ubuntu boot began. After installing Xubuntu I was able to get a display but it was broken up with vertical lines showing that the refresh rate and sync were not correct. Puppy worked fine, but almost no other distro would.

I tried video card driver updates, and in the P4 I installed a newer AGP card which stopped the Ubuntu black screen but left me with a 640x480 maximum resolution after updating Ubuntu. Way no good!

Finally it dawned on me to try a different monitor, and sure enough Ubuntu then worked flawlessly. The old HP Pavilion M90 CRT monitor was not recognized by Ubuntu, but the equally old 15" Komodo CRT works good.

For me, the black screen was caused by Ubuntu and other distros simply not recognizing the monitor.

---

