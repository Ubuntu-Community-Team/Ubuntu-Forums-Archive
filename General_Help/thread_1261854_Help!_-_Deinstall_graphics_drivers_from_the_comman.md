---
title: "Help! - Deinstall graphics drivers from the command line"
date: 2009-09-09
forum: General Help
---

### Post by stevebond001 on 2009-09-09
Help!
I have just installed Envy to help me install a driver for my (ATI based) graphics card. Envy downloaded the recommended driver and asked me to reboot, which I did.
However, when the PC boots up now I just get a garbled screen and it locks up.

Does anyone know how to de-install the driver from the command line (as I can boot into recovery mode OK)

Many thanks in advance

Sorry for cross posting but I need to resolve this asap :(

---

### Post by gastly on 2009-09-09
If you installed it from a .deb package, then this would do it:
```
sudo dpkg -P envy
```

---

### Post by wojox on 2009-09-09
If that doesn't work reset xorg.conf

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

---

### Post by stevebond001 on 2009-09-09
> **gastly said:**
> If you installed it from a .deb package, then this would do it:
```
sudo dpkg -P envy
```

Hi
Thanks for the reply.  When I try to run this I get an error stating:
Unable to access dpkg status area: Read-only file system

When running sudo dpkg-reconfigure xserver-xorg -phigh I get the same sort of error message (Read-only file system)

Any other ideas?

Thanks in advance

---

### Post by stevebond001 on 2009-09-09
Just rebooted and retried the commands suggested:

sudo dpkg -P envy gives the error "warning: ignoring request to remove envy which isn't installed".  This is weird as I know I installed it.


sudo dpkg-reconfigure xserver-xorg -phigh returned no error.  However when I rebooted after this I still have the same problem (garbled screen)

How can I list and deinstall the offending graphics driver?

---

### Post by gastly on 2009-09-09
```

sudo mount -o remount,rw /

```

This will try to remount the root filesystem read-write.

---

### Post by gastly on 2009-09-09
Please ignore the above post...I forgot to refresh the page and check for any new posts hehe :P

You can do this:
```
aptitude search envy
```

This will search all packages with 'envy' in their names. See which one is installed and remove it using **sudo apt-get purge <package-name>**

Btw, how did u install envy?

---

### Post by stevebond001 on 2009-09-09
Thanks for that - I actually rebooted and tried the suggestions again, as follows:

sudo dpkg -P envy gives the error "warning: ignoring request to remove envy which isn't installed". This is weird as I know I installed it.


sudo dpkg-reconfigure xserver-xorg -phigh returned no error. However when I rebooted after this I still have the same problem (garbled screen)

How can I list and deinstall the offending graphics driver?

---

### Post by stevebond001 on 2009-09-09
Sorry, I also forgot to refresh the thread :-\"

I installed envy via the command from the envy website.

I think the problem resides with the graphics driver.  I've been looking around other posts, etc and have (i think) identified the driver.

I used "dpkg -l '*amdcccle*' and received the following output:

ii  fglrx-amdcccle                   2:8.600-0ubuntu2

Is this the driver?  If so, how do I deinstall it?

TVM

---

### Post by wojox on 2009-09-09
Look in /usr/share/ati/ and see if there's an uninstall script.

---

### Post by gastly on 2009-09-09
hmm...I looked at the envy website and they have a command to un-install it.
```
envy --uninstall-all
```

And if that doesn't work then the driver you specified can be un-installed by ```
sudo dpkg -P fglrx-amdcccle
```

but I recommend you try the first option and see if it works :)

---

### Post by Yellow Pasque on 2009-09-09
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by stevebond001 on 2009-09-09
Sorted
I ran the following command
sudo envyng --uninstall-all

This deinstalled envy and all the appropriate drivers

Many thanks for your help, you're a star :KS

---

### Post by gastly on 2009-09-09
I'm glad I could help :)

---

