---
title: "How do I install Windows after Karmic ?"
date: 2009-11-04
forum: General Help
---

### Post by YosefKaro on 2009-11-04
I used to have wubi then I decided to do a fresh install of Karmic.  Now I just created a small partition and I want to install Windows on that small partition.  Before I do that, I need some guidance...How to configure Grub 2, etc. so that I will be able to dual boot.  I know that if I just go to install Windows on that small partition, then I am going to run into problems so I welcome any guidance that you may have for me.

-Yos

---

### Post by fancypiper on 2009-11-04
Is that partition a primary partition?  Windows is rather picky as to where it is installed.

If it is a primary partition, installation of Windows will "correct" the mbr, so you will have to re-install grub after installing Windows.  I think Windows has a boot option that you can use, but that is a hazy memory.

I think you use the live Ubuntu to boot and then

sudo grub-install
sudo update-grub

[The Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=reinstall+grub")
[URL="https://help.ubuntu.com/community/WindowsDualBoot"]Windows Dual Boot
[/URL]

---

### Post by YosefKaro on 2009-11-04
Thank you, but you sound a little unsure of yourself...so I'll wait for some more replies.

-Yos

---

### Post by fancypiper on 2009-11-04
> **YosefKaro said:**
> Thank you, but you sound a little unsure of yourself...so I'll wait for some more replies.

-YosCheck out the links...):P
[Ubuntu and Windows Dual Boot](https://help.ubuntu.com/community/)
[Grub 2 Basics](http://ubuntuforums.org/showthread.php?t=1195275&highlight=reinstall+grub)

---

### Post by sliketymo on 2009-11-04
> **YosefKaro said:**
> Thank you, but you sound a little unsure of yourself...so I'll wait for some more replies.

-Yos
  Uh,he's right.Windows is picky about what kind of partition,and the size of the partition.Did you partition it as a Primary partition? Did you partition it as a Logical partition?How much space have you allowed for windows to be installed? How much space does an instalation of your particular version of windows require? You mind find your answers by following the links he provided.Sometimes the answer is right under our noses!

---

### Post by soapBAR2 on 2009-11-04
> **YosefKaro said:**
> Thank you, but you sound a little unsure of yourself...so I'll wait for some more replies.

-Yos

His reply is good - only remember that you'll hose your current GRUB setup. If you've just installed Ubuntu (and it sounds like you have), this is a non-issue. However, if you want to keep the list of old kernel names, you can:

- Save the /boot/grub/grub.cfg (/boot/grub/menu.lst on grub1), and manually add the window entry
- Re-add the old kernel options after the fact

Also, Windows doesn't *HAVE* to be on the primary partition - you can trick it into thinking it is by
```
map (hd0,0) (hd0,**3**)
map (hd0,**3**) (hd0,0)
rootnoverify (hd0,**3**)
```
(changing the 3s to the actual boot device according to grub, trial and error is usually the easiest method).

Oh, and in case you didn't know - you can access your ubuntu partition by installing Ext2IFS on Windows (I've found the newest version doesn't work for me, but an older one does). You may need this if you don't have a liveCD and want to alter your /boot/grub/grub.cfg

---

### Post by YosefKaro on 2009-11-04
Wow, this is a much more involved process than I imagined it would be...too complicated for me to follow.  I'm just going to install windows and then reinstall Karmic and let the installation do all of the hard work for me :p  Oh, and yes, it is a primary partition and yes there is ample space for the Windows installation.

-Yos

---

