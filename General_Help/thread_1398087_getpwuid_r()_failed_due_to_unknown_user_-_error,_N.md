---
title: "getpwuid_r() failed due to unknown user - error, NO X available"
date: 2010-02-04
forum: General Help
---

### Post by Raubsau on 2010-02-04
Hi!

I'm running an up-to-date Lucid Lynx, full encryption with LUKS on my Eee 1005HA.

Since yesterday, after booting, the only "X" is can see is the mouse cursor above a console-like text, saying:

```
(process_290) GLib-WARNING **: getpwuid_(): failed due to unknown user id (0)
init: ureadahead main process (410) terminated with status 5
fsck [clean, blah bla, check deferred, on battery]
init: ureadahead-other main process (3143) terminated with status 4
*lvm (running)
*Starting init crypto disks... [OK]
*lvm (running)

```
So, I googled for the getpwuid_r thing. I found a blog saying to install nscd (did so) and run it.

But: To my inconvenience, after every booting, I have to switch to console 1, log in, run "sudo /etc/init.d/nscd restart" and then "sudo restart gdm".

What would be a solution (besides reinstall?)

---

### Post by Raubsau on 2010-02-06
After one of today's updates including x-org-core, it now runs smoothly.

edit:
Next update - problem reoccurs.

---

### Post by Raubsau on 2010-02-12
*push*

---

### Post by morryis on 2010-02-22
Same for me. I can mount my home folder and access my files manually by executing "ecryptfs-mount-private" in recovery mode. But I don't get regular start-up to work.

EDIT: I tried booting with a remaining Karmic kernel (2.6.31.20), everything works as expected.

EDIT2: Thats wierd, if I switch to TTY1 and back to TTY7 graphical login works.
I also tried to boot a live system from the daily, got the same getpwuid error.

---

### Post by Raubsau on 2010-02-23
That means you do not have to execute nscd?

Interesting, because without nscd I am able to login but the system will hang up without warning and can only be reset the hard way (power switch).

---

### Post by morryis on 2010-02-26
Yes, I am not using nscd. As soon as I switch to TTY1 and back GDM shows up. I can hear the startup sound before too.

This bug also occurs when I am booting from a live-CD.

EDIT: This thread should be moved to Lucid testing forum

EDIT2: I can simply press ENTER and the login-screen appears. I think my problem is caused by the package cryptsetup somehow, as soon as I remove that the login-window shows up directly.

---

### Post by Raubsau on 2010-03-01
Any update?

Do you use a fully encrypted system?

---

### Post by cristianrosa on 2010-03-03
Do you know if there is already a bug report in launchpad?
I'm having the same problem running Lucid Alpha3 Live-CD on both of my laptops:
Dell Latitude D600 (x86) and Dell Precision M90 (x86_64)

---

### Post by Raubsau on 2010-03-03
No, I don't know whether there's already a bug filed.

I just downloaded a fresh Alpha 3 netbook iso.

Boots fine, network is up & running, no crash so far.

---

