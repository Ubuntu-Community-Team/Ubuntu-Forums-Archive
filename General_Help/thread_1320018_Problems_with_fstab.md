---
title: "Problems with fstab"
date: 2009-11-08
forum: General Help
---

### Post by sablefoxx on 2009-11-08
I have a drobo ([www.drobo.com](www.drobo.com)) which is basically a really fancy usb external hdd.  Now I would like to mount this drive to ~/drobo on every boot so I edited my /etc/fstab like so;

```
/dev/sdb1 /home/user/drobo auto defaults,realtime 0 1
```

This however does not work, but after booting into the OS I can run "sudo mount /dev/sdb1 ~/drobo" and it mounts without a problem.  Now I have the drive formatted to ext3 but in gparted it says that the file system is unrecognized, I am also running Ubuntu 9.04

Any ideas on why this isn't working?

or should I should I just write a shell script to mount it for me?

---

### Post by Barriehie on 2009-11-08
> **sablefoxx said:**
> I have a drobo ([www.drobo.com](www.drobo.com)) which is basically a really fancy usb external hdd.  Now I would like to mount this drive to ~/drobo on every boot so I edited my /etc/fstab like so;

```
/dev/sdb1 /home/user/drobo auto defaults,realtime 0 1
```

This however does not work, but after booting into the OS I can run "sudo mount /dev/sdb1 ~/drobo" and it mounts without a problem.  Now I have the drive formatted to ext3 but in gparted it says that the file system is unrecognized, I am also running Ubuntu 9.04

Any ideas on why this isn't working?

or should I should I just write a shell script to mount it for me?

This could be a stupid ? but is **user** the login account name?

Barrie

---

### Post by sablefoxx on 2009-11-08
Sorry for being unclear, I was substituting "user" for my actual user name.

---

### Post by Barriehie on 2009-11-08
Okay, should 'realtime' in your fstab line perhaps be relatime???  And perhaps go ahead and put ext3 in there too!

Barrie

---

### Post by sablefoxx on 2009-11-08
You sir are brilliant I just got it working, I just typed in "realtime" without even thinking about it, brain sees what it wants to see sorta thing.  Out of curiosity what does "relatime" mean?

---

### Post by Barriehie on 2009-11-09
> **sablefoxx said:**
> You sir are brilliant I just got it working, I just typed in "realtime" without even thinking about it, brain sees what it wants to see sorta thing.  Out of curiosity what does "relatime" mean?

It has to do with the files access time being updated.  Can read more about it [here](http://lwn.net/Articles/244829/).  I only noticed because I was just messing with that in my fstab!

Barrie

---

