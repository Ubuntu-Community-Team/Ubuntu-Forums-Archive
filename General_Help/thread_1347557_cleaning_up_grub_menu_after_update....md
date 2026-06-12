---
title: "cleaning up grub menu after update..."
date: 2009-12-06
forum: General Help
---

### Post by tozymba on 2009-12-06
ok, i updated my ubuntu and in grub menu it shows two ubuntu

Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows Vista (loader) (on /dev/sda2)


i want to remove the other ubuntu.
i was following this ([link]("http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/")) but i don't have anything on menu.lst
please help me with this :-(

---

### Post by ayampanggang on 2009-12-06
you can remove your old kernel which stands by the package name
> 
linux-headers-<version>
and linux-image-<version>


---

### Post by tozymba on 2009-12-06
thx ayampanggang! worked perfectly!

---

### Post by OllyDBG on 2009-12-06
Well thats not a good idea..you may want to switch to your old kernel for some reason

---

### Post by t0p on 2009-12-06
> **OllyDBG said:**
> Well thats not a good idea..you may want to switch to your old kernel for some reason

Indeed.  I think it's wise to keep at least one old kernel image on one's computer, in case of problems with the newest kernel.  It's not unknown for a kernel update to break functionality in some way.

---

### Post by ayampanggang on 2009-12-07
yeah, you need to make sure your newest kernel works first before removing all others. I usually keeps 2 versions. The newest and the last one.

---

### Post by LeifAndersen on 2009-12-07
There's an easy GUI to manage starting up in the software center, I believe it's called startup manager.  But as I'm in front of a CentOS machine at the moment, I can check to make sure.

---

### Post by inhiway on 2009-12-07
> **LeifAndersen said:**
> There's an easy GUI to manage starting up in the software center, I believe it's called startup manager.  But as I'm in front of a CentOS machine at the moment, I can check to make sure.

The program name is correct.  I have just installed it after reading your reply.  And tested with a reboot.  Works for me.  Thanks Leif for the tip.

---

