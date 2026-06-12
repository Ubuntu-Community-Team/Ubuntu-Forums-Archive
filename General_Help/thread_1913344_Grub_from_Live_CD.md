---
title: "Grub from Live CD"
date: 2012-01-22
forum: General Help
---

### Post by TheAJGman on 2012-01-22
I accedently removed Ubuntu from the GRUB boot loader list and now I can only boot to win7. I do have a live cd and would like to know how I would fix this from the cd.

---

### Post by Old_Grey_Wolf on 2012-01-22
Read this Ubuntu help page [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files). The section you want is _Copy LiveCD Files_.

---

### Post by TheAJGman on 2012-01-22
> **Old_Gray_Wolf said:**
> Read this Ubuntu help page [https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files). The section you want is _Copy LiveCD Files_.

So I should manually edit the config from the live cd? Ok will try when I get back to my laptop.

---

### Post by sgage on 2012-01-22
> **TheAJGman said:**
> So I should manually edit the config from the live cd? Ok will try when I get back to my laptop.

You can boot the LiveCD, chroot into your Ubuntu system, and do a grub-install /dev/sdx (x being your boot drive), followed by update-grub.

---

### Post by Q-collective on 2012-01-22
The easier way is to download the [Boot Repair Disc](http://sourceforge.net/p/boot-repair-cd/home/Home/) or the [Redo backup disc](http://redobackup.org/) (the latter also has Boot Repair as a program, but features an extremely handy clone/backup program called Redo).

---

### Post by Old_Grey_Wolf on 2012-01-22
> **TheAJGman said:**
> So I should manually edit the config from the live cd? Ok will try when I get back to my laptop.

The page I linked to has several methods of re-installing Grub2. It has a lot of other information it it as well; such as, customizing Grub2. I just linked you to the place where the easiest solution IMO can be found.

---

### Post by TheAJGman on 2012-01-22
I don't need to reinstall grub I just accedently removed it from the boot list while getting rid of the random and useless enteries. I'll chroot into Ubuntu and sudo update-grub. When I get back from visiting relatives. *sigh*

---

### Post by sgage on 2012-01-22
> **TheAJGman said:**
> I don't need to reinstall grub I just accedently removed it from the boot list while getting rid of the random and useless enteries. I'll chroot into Ubuntu and sudo update-grub. When I get back from visiting relatives. *sigh*

That should do it.

---

### Post by Old_Grey_Wolf on 2012-01-22
That will work. Sorry, I misread your original post.

---

### Post by TheAJGman on 2012-01-22
nope nothing works. I need to make a new grub.cfg from the live cd but i cant figure out how to chroot correctly.
EDIT: if someone could post what the 11.10 grub entry looks like
EDIT2: hmm, my mnt folder is empty. Is that bad?

---

### Post by Old_Grey_Wolf on 2012-01-22
This might help. It is from the same webpage I posted before [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot).

Note step 10 and the steps prior to it.

---

### Post by TheAJGman on 2012-01-22
> ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: /dev/sda5 already mounted or /mnt busy
mount: according to mtab, /dev/sda5 is already mounted on /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: groups: command not found
root@ubuntu:/# update-grub
bash: update-grub: command not found
root@ubuntu:/# 
dont work
EDIT: when i try to copy mnt from the virtual file system it said there wasnt enough space.I had 200gigs but it needed 140 terabytes?

---

### Post by TheAJGman on 2012-01-22
someone help me

---

### Post by TheAJGman on 2012-01-22
im just gonna try to reinstall

---

### Post by TheAJGman on 2012-01-22
thanks alot for helping everyone *rolls eyes*

---

### Post by Q-collective on 2012-01-23
> **TheAJGman said:**
> thanks alot for helping everyone *rolls eyes*

The solution I provided in post 5 would have saved you from a reinstall.

Have a nice day.

---

### Post by Old_Grey_Wolf on 2012-01-23
Should have waited a little longer than 2 hours for someone to reply before re-installing. Some people are in different time zones, and some people do other things beside answering posts on Ubuntu Forum.

---

