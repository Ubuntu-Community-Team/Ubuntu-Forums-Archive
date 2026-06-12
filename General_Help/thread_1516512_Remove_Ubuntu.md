---
title: "Remove Ubuntu?"
date: 2010-06-23
forum: General Help
---

### Post by BobOmg on 2010-06-23
Okay, so I downloaded the Ubuntu 10.04 ISO and burned it to a CD. Then I installed it as a dual boot so I could keep Windows. I did something wrong with the partitioning giving only 3 GB of space, and I couldn't find a way to fix that, and there's other problems happening as well. So, is there a way to completely uninstall Ubuntu and GRUB? I want to reinstall after though.

If anyone needs to know, I'm using Windows 7 Home-Premium 32 bit.

And I don't have my Windows Recovery CD, because I know that can also be used as a way to get rid of it.

Thanks in advance, and sorry if this is in the wrong place.

---

### Post by Leppie on 2010-06-23
if you want to reinstall ubuntu, you don't really need to remove the old install. you could make the modifications for the paritions and then install again, unless you need to fix things in windows first.
you can download a windows 7 recovery disk here: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by BobOmg on 2010-06-23
Is there any other way? Because I don't want to burn anything to get rid of it.

---

### Post by BobOmg on 2010-06-23
Actually nevermind. If I do that, what should I do first? Make the partition larger?

---

### Post by Leppie on 2010-06-23
booting off the ubuntu livecd, go into the live environmnet rather than starting the installation process. you can use gparted (System>Administration>Gparted) to remove the old partiton.
in a terminal issue the following commands:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```after this, rebooting will take you into your windows 7 install where you can resize the partition after which you can re-install ubuntu.

---

### Post by BobOmg on 2010-06-23
When I went into Ubuntu again it gave me a Gnome Power Error. When I try to log it, I get logged out.

(Sorry, because this has nothing to do with what I was asking. I think the partition is causing this for some reason because it warned me about low space before, I didn't think it really mattered though.)

EDIT: Nevermind, missed the live CD part. Anyways, can rebooting go wrong if I do that?

---

### Post by Leppie on 2010-06-23
there is always like the 1% change that something goes wrong, but that's got nothing to do with the procedure i described earlier ;)

---

### Post by BobOmg on 2010-06-24
By resize you mean make a new partition? Windows wont let me resize it.

---

### Post by Leppie on 2010-06-24
no, windows does not handle non-windows filesystems. that's why i told you to use gparted in the ubuntu livecd environment to delete the partition.

---

### Post by BobOmg on 2010-06-24
Okay, well I was able to remove it completely. Will I be able to use the unallocated space I have? To reinstall it or would I have too partition again?

---

### Post by Leppie on 2010-06-24
if you just leave the unallocated space like that, you can choose to have the ubuntu installer take the largest free space available.

---

### Post by BobOmg on 2010-06-24
Okay thanks. Oh, and if I do that, it wont take the space that windows is installed on right? (Just making sure.)

---

### Post by Leppie on 2010-06-24
> **BobOmg said:**
> Okay thanks. Oh, and if I do that, it wont take the space that windows is installed on right? (Just making sure.)
no, it won't take the space windows is installed on if you choose to have ubuntu install into the largest free space available. of course, you need to reduce the windows partition (if you have not done so already) in order to be able to assign more space to ubuntu.

---

### Post by BobOmg on 2010-06-24
I partitioned it the first time I installed. I did something wrong during installing it that gave it only 3 GB of space. (Which was my previous installation.) So I don't have to partition again, correct?

---

### Post by Leppie on 2010-06-24
> **BobOmg said:**
> I partitioned it the first time I installed. I did something wrong during installing it that gave it only 3 GB of space. (Which was my previous installation.) So I don't have to partition again, correct?
well, taking that you previously stated to have removed the ubuntu partition and presuming you have enough free desired space on the drive, you can have the installer do all the partitioning.

---

### Post by BobOmg on 2010-06-24
So, I can just let it use the most free space available right? (The unallocated space.) And I have a recovery drive that's 6 GB, with things on it. It won't take that either right?  (I'm just trying to make sure, because a lot of things went wrong with the first install.)

---

### Post by Leppie on 2010-06-24
yes, just make sure that you have the installer use the free space and you'll be fine ;)

---

### Post by BobOmg on 2010-06-24
Alright, thanks.

---

### Post by Leppie on 2010-06-25
you're welcome.

let us know how it's proceeding.

---

