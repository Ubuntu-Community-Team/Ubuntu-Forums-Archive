---
title: "Grub 2 Sux!"
date: 2010-03-06
forum: General Help
---

### Post by javyn999 on 2010-03-06
Is there anyway I can go back to the old grub where I can do things like removing and reordering my menu simply with 9.10 and Lucid when it comes out?

---

### Post by joeknoodle on 2010-03-06
> **javyn999 said:**
> Is there anyway I can go back to the old grub where I can do things like removing and reordering my menu simply with 9.10 and Lucid when it comes out?

I sure hope so. A recent foray into grub 2 ended with having to reinstall everything.

Of course, I'm still mad about losing all my cool GDM logins.

---

### Post by PeEllAvaj on 2010-03-06
It looks like on Ubuntu you won't be able to go back to Grub1 using Ubuntu.  The main driver behind this is that Grub1 doesn't support ext4, which is the Ubuntu standard since Karmic.

If you are willing to keep using ext2/3, you might be able to find a PPA for Grub1.  I hated grub2 when it first came out, but you get used to the autodetection, as it is pretty helpful.  Still sucks that you can't just make your own list if you wanted to.

---

### Post by coffeecat on 2010-03-06
> **PeEllAvaj said:**
> It looks like on Ubuntu you won't be able to go back to Grub1 using Ubuntu.  The main driver behind this is that Grub1 doesn't support ext4, which is the Ubuntu standard since Karmic.

Sorry to have to correct you, but both of those statements are incorrect.

Here is a method for reverting to legacy grub:

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

As far as legacy grub support of ext4 goes, ext4 was an option in Jaunty and legacy grub was patched for Jaunty to handle ext4. This is the version of legacy grub still available for Karmic if you so choose. (And available in Lucid as well.)

---

### Post by ibuclaw on 2010-03-06
> **coffeecat said:**
> Sorry to have to correct you, but both of those statements are incorrect.

Here is a method for reverting to legacy grub:

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

As far as legacy grub support of ext4 goes, ext4 was an option in Jaunty and legacy grub was patched for Jaunty to handle ext4. This is the version of legacy grub still available for Karmic if you so choose. (And available in Lucid as well.)

And besides, you always have the ability to have a separate /boot partition in ext2 format. :)

---

### Post by PeEllAvaj on 2010-03-06
Thanks for enlightening me! Apparently I was misinformed. :)

---

### Post by falconindy on 2010-03-06
edit: too slow.

---

### Post by gjoellee on 2010-03-06
> **javyn999 said:**
> Is there anyway I can go back to the old grub where I can do things like removing and reordering my menu simply with 9.10 and Lucid when it comes out?

You can just modify the grub menu file ;)

---

### Post by impert on 2010-03-06
>  Grub 2 Sux!
Is there anyway I can go back to the old grub where I can do things like removing and reordering my menu simply with 9.10 and Lucid when it comes out?

Actually, you can use Grub2 to give you the menu you want with only a little more complication than in Grub1.

1 Edit /etc/default/grub to taste 
2 Run update-grub.
3 Cut and paste the bits you want from /boot/grub/grub.cfg into 40_custom
4 ```
chmod -x /etc/grub.d/30_os-prober
  chmod -x /etc/grub.d/20_memtest86+
```
(You can do the same for the other files in /etc/grub.d if you copy the meaningful bits of the top part of grub.cfg to 40_custom) 
5 Run update-grub again.

Then if you add an OS or do a kernel upgrade you can either edit 40_custom manually, or else make 30_os-prober executable again temporarily, and copy and paste.
You can also use
```
set root (hd*x,y*)
chainloader +1 
```
to boot an OS which has a bootloader in its superblock (first block of its root partition)

---

