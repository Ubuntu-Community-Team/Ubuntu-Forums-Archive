---
title: "Edit Grub on Ubuntu 9.10"
date: 2009-11-04
forum: General Help
---

### Post by W29 on 2009-11-04
Hi

I'm using Ubuntu 9.10 and Windows 7.
I'm quite new to Ubuntu, so I want to change the default OS to Windows 7.
In Ubuntu 9.04, you could just edit the menu.lst file (gksudo gedit /boot/grub/menu.lst).
But this is different for Grub2 and not as discribed in [here]("https://help.ubuntu.com/9.10/switching/dualboot-custom.html"). If I want to edit /boot/grub/grub.cfg, it says it is a read-only file and that I can't edit it.
I searched aroud to find a solution and the only thing I could find, was another file /etc/default/grub. I've changed this file, but nothing happens.

What am I doing wrong?
Grtz W29

---

### Post by coffeecat on 2009-11-04
> **W29 said:**
> But this is different for Grub2 and not as discribed in [here]("https://help.ubuntu.com/9.10/switching/dualboot-custom.html").

Yes that is a surprising link - telling you how to edit legacy grub menu.lst in a community documentation Karmic page. I hope it gets marked for editing.

Anyway, two better links for you. 

Ubuntu community documentation as it should be:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

A very clear starter's guide from this forum:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by P4man on 2009-11-04
I reported a bug for that page. Apparently thats the way to report problems with the documentation. Bug report here:
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/474022](https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs/+bug/474022)

They probably just copied it over from previous ubuntu docs without checking.

---

### Post by wilee-nilee on 2009-11-04
Startup manager in synaptic will allow you to allocate the grub list, and the time out.

---

### Post by W29 on 2009-11-04
The startupmanager did the job.
@coffeecat: Your 2nd link is very usefull.

But I still got a question. How can I change the name of these values? (e.g. Ubuntu generic 2.6.3... to Ubuntu 9.10 Keramic Koala)

---

### Post by oldos2er on 2009-11-04
I believe you'd need to edit /etc/init.d/10_linux , but check [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602) and [http://ubuntuforums.org/showthread.php?t=1305113](http://ubuntuforums.org/showthread.php?t=1305113) first.

---

### Post by drs305 on 2009-11-04
I will start editing the referred page this afternoon to include the GRUB 2 procedures. Thanks for pointing it out.

Oops - no I can't. It's not a community document, but it's reported.

---

### Post by drs305 on 2009-11-04
Deleted - duplicate post.

---

### Post by wentzr on 2009-12-21
> **W29 said:**
> The startupmanager did the job.
@coffeecat: Your 2nd link is very usefull.

But I still got a question. How can I change the name of these values? (e.g. Ubuntu generic 2.6.3... to Ubuntu 9.10 Keramic Koala)

**take another look at **[B]

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

it tells you exactly how to do this. you edit 40_custom... NOTHING else.. just chmod -x those files in /etc/grub.d/ which you don't want going in your grub.cfg.
[/B]

---

### Post by Leppie on 2009-12-21
open /etc/default/grub with a text editor and change GRUB_DEFAULT=0 to GRUB_DEFAULT="xxx". where xxx is the exact description of the menu entry.
to find the exact menu entry issue the following command:
```
$cat /boot/grub/grub.cfg | grep Windows
```

if you want to change the appearance of your ubuntu installs in the menu list, edit the line:
```
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
```
to:
```
GRUB_DISTRIBUTOR=`lsb_release -cris 2> /dev/null || echo Debian`
```
like this, it should appear as "Ubuntu 9.10 Karmic"

---

