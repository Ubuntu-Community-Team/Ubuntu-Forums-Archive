---
title: "keyboard and mouse inactive at startup"
date: 2010-09-02
forum: General Help
---

### Post by aduxas on 2010-09-02
When booting up my system today, it got until the login screen, but both keyboard and mouse were inactive.  The login window had a triangle (as if to start a video) that I cannot remember having seen before.  Any ideas what is going on and how to get in?  I am running Lucid Lynx and KDE.

---

### Post by llamabr on 2010-09-02
Are they plugged in?

---

### Post by aduxas on 2010-09-02
Sure.  I unplugged them and plugged them back in, no use.

---

### Post by aduxas on 2010-09-02
BTW the keyboard also worked during the boot process.

---

### Post by aduxas on 2010-09-02
I tried rebooting with mouse and keyboard unplugged, then plugging them back in as soon as the OS was running.  That activated the keyboard, but not the mouse.  I was able to log in, but I don't know enough shortcuts to get much done.  Rebooting again deactivated both peripherals.

---

### Post by bergfly on 2010-09-03
Have you tried selecting an older kernel from the boot list. Might be the latest kernel with your motherboard.

---

### Post by aduxas on 2010-09-03
/etc/xconf.org was missing.  I tried reconfiguring xorg.conf, but nothing worked.  I could not get it back.  Then I probably did something really bad: I copied xorg.conf.failsafe onto xorg.conf and rebooted.  All I see now is a short purple flash with "Ubuntu 10.0.4" and that's it:  it hangs.  How can I get back in?

---

### Post by bergfly on 2010-09-04
If you system still accepts the keyboard, give it a while to boot and then hold down alt-ctrl and F2 to bring up a terminal session. If this works then you can start work on xorg.conf. In theory the system will work without an xorg.conf file now, so you might want to move the xorg.conf to xorg.confbackup. If not you could still get in with a boot disk, however, might be time to cut your loses and do a reinstall.

---

### Post by aduxas on 2010-09-04
Alas, alt-ctrl F2 does not work.  It does not have any effect.
I tried booting from a CD with the option not to change anything on the hard drive.  That works correctly, but it does not see the hard drive at all, it seems.  The CD is 9.0.4; I upgraded to 10.0.4 via download.  I'll try to get a new CD first.  I have tons of experience reinstalling Windows, but I never had to reinstall Linux.  I assume I can reinstall without losing user files?

Thanks for the help.

---

