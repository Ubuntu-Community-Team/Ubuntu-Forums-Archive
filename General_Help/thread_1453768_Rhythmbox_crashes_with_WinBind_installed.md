---
title: "Rhythmbox crashes with WinBind installed"
date: 2010-04-13
forum: General Help
---

### Post by cas118 on 2010-04-13
Hi folks,

This has been stumping me for some time. I've just upgraded to Lucid Lynx to try and fix the problem.

Essentially, if I have the winbind package installed and start Rhythmbox, RB will crash after a few seconds.

I traced it down to winbind after seeing the following message in dmesg:
```
[49041.647051] rhythmbox[5217]: segfault at 0 ip 00007f4deb5b1e4c sp 00007f4e03969300 error 6 in libnss_wins.so.2[7f4deb559000+283000]
```

Running from the command line returns
```
Segmentation fault (core dumped)
```

For the time being, I've removed winbind - but does anybody have any thoughts on why this could be happening?

Cheers.

---

### Post by BadString on 2010-05-03
I had this as well. However once I unistalled winbind I started rhythmbox and left it running while I reinstalled winbind, it's no longer crashing - so far so good.

---

### Post by Radipon on 2010-05-11
> **BadString said:**
> I had this as well. However once I unistalled winbind I started rhythmbox and left it running while I reinstalled winbind, it's no longer crashing - so far so good.

I followed these steps and found that although rhythmbox doesn't crash intially, it continues to do so once the program has been closed. That is, installing winbind with the program running means that it isn't being used by that process, but future invokations do and subsequently segfault.

---

### Post by lkilcher on 2010-05-13
I've gotten this bug in Karmic, just after installing libimobiledevice (and updating some other things... not sure what).

The fix in #16 at:
[https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/369274](https://bugs.launchpad.net/ubuntu/+source/liferea/+bug/369274)
worked for me.

This also appears to be related to (or is):
[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/529714)

Some people claim that the fix above will disable wins and therefore samba.  I haven't noticed a difference in samba functionality, but I haven't rebooted.

---

### Post by vikamu11 on 2010-08-11
This is so true. Once i uninstall winbind, Rhythmbox stabilized. Kudos..

---

### Post by keithspg on 2010-08-26
and this is not a bug!??

---

### Post by xsyw9998 on 2011-01-02
02-Jan-2011 -- This problem still exists. Installed samba and winbind today, after reboot, rhythmbox crashed with a segfault as described above. Uninstalled winbind, rhythmbox resumed normal operation. Running 10.10 with all the latest updates.

---

