---
title: "Ubuntu Tweak"
date: 2010-02-07
forum: General Help
---

### Post by warfacegod on 2010-02-07
Unlock> select all> clean up

---

### Post by zhanglini on 2010-02-07
Eh?

---

### Post by Atzu on 2010-02-07
> **zhanglini said:**
> eh?

+1

---

### Post by warfacegod on 2010-02-07
Just giving a visual to someone. Don't need any help. Sorry.

---

### Post by Uncle Spellbinder on 2010-02-07
[IMG]http://img.photobucket.com/albums/v694/unclespellbinder/Baffled2.jpg[/IMG]

---

### Post by Kai69 on 2010-02-07
Hi warfacegod ive done that removed both kernels ending in 14 and 17 did update grub and restarted, Still have kernels 14 and 17 showing in boot menu ?

---

### Post by warfacegod on 2010-02-07
> **Kai69 said:**
> Hi warfacegod ive done that removed both kernels ending in 14 and 17 did update grub and restarted, Still have kernels 14 and 17 showing in boot menu ?

Which OS did you install to?

---

### Post by Kai69 on 2010-02-07
Ive only installed ubuntu 9.10 and edubuntu 9.10 (which looks like 9.04). Sorry edubnutu was installed today

---

### Post by drs305 on 2010-02-07
> **Kai69 said:**
> Hi warfacegod ive done that removed both kernels ending in 14 and 17 did update grub and restarted, Still have kernels 14 and 17 showing in boot menu ?

You can check a couple of things to see if the correct files were updated/removed

Check the timestamp to see if the proper file was updated:
> ls -la /boot/grub/grub.cfg

Check to see if the kernels still exist in /boot:
```
ls -la /boot/ | grep vmlinuz
```

I actually just needed to make a post to troubleshoot a "missing security" error message, so disregard if you are way ahead on this.  ;-)

---

### Post by warfacegod on 2010-02-07
You may have to run:

```
sudo update-grub
```

from both OSes.

I'm taking my daughters to the park. I'll be back in about an hour.

---

### Post by Kai69 on 2010-02-07
kai@kai-laptop:~$ ls -la /boot/grub/grub.cfg 
-r--r--r-- 1 root root 3528 2010-02-07 20:35 /boot/grub/grub.cfg
kai@kai-laptop:~$ ls -la /boot/ | grep vmlinuz
-rw-r--r--  1 root root 3891264 2010-01-28 04:39 vmlinuz-2.6.31-19-generic
kai@kai-laptop:~$

---

### Post by Kai69 on 2010-02-07
Ok ive gone into edubuntu and installed ubuntu tweak, Ive removed the old kernels updated grub all sorted rebooted all old kernels are gone Yippee

---

### Post by warfacegod on 2010-02-07
> **Kai69 said:**
> Ok ive gone into edubuntu and installed ubuntu tweak, Ive removed the old kernels updated grub all sorted rebooted all old kernels are gone Yippee

Great! I guess I should mark this as solved?

---

### Post by Kai69 on 2010-02-07
Thanks for the Help :p

---

