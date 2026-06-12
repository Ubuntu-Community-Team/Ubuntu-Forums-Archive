---
title: "Deleted kernel"
date: 2010-11-06
forum: General Help
---

### Post by joey00 on 2010-11-06
I just crashed one of my Hardy boxes (containing valuable data, of course).

I was doing a cleanup and found a large number of old kernels.  So, without thinking about it too hard, I decided to delete (Synaptic) all except the latest 2 (i.e. 4 files- linux-headers and linux-image, I think).

I should mention that this box is a dual boot (Win98 SE).

Now the ubuntu won' t start. It gives the grub (old version) dual -boot menu and sits with any attempt to run ubuntu. Win98 runs ok still.

Is there any way to replace/restore the missing kernel without damaging the valuable data files.

The only other alternative, AFAIK, is to copy off the data and simply do a clean ubuntu install.  But that looks like a very long job. :(

Even in the latter case, there would be problems, since I need to be able to restore a diversity of data files to reasonable locations.

I have the feeling that there should be a simple solution to this, since the only issues are the missing kernel files.

Anybody like to help me out of this potential disaster?

---

### Post by Decatf on 2010-11-06
chroot will save you.

[http://buranen.info/?p=328](http://buranen.info/?p=328)

---

### Post by joey00 on 2010-11-07
This article seems very incomplete.:confused:

Despite its advocacy of chroot, I see no point at which it is used!

Also, when I try to use the mount commands, I get firstly: "Directory doesn' t exist" and then "you must specify the files system".

I am fairly sure that I can carry out the apt-get commands without too much trouble, once I get to the HDs on which the system is built. 

But how to get there?

---

### Post by efflandt on 2010-11-07
For example of chroot go to [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and scroll down to 
**METHOD 3 - CHROOT**

Your grub version is likely an older version, so you may also want to see [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto) about legacy grub, but that does not explain chroot.

---

### Post by dino99 on 2010-11-07
it seem to me that grub simply dont find the good path now: edit the boot line and give the good label or uuid, it should boot, then 

sudo update-grub

---

### Post by joey00 on 2010-11-12
> **dino99 said:**
> it seem to me that grub simply dont find the good path now: edit the boot line and give the good label or uuid, it should boot, then 

sudo update-grub

Can you give a bit more detail on the first part of this?

Where to look and how?

Where is boot line?

label?
uuid?

---

### Post by WorMzy on 2010-11-12
Sod update-grub, this is grub legacy, we can do things *properly*. >:D

First, boot into a LiveCD. Mount your Ubuntu partition and open it's menu.lst in gedit with gksu. e.g.
```
gksu gedit /media/diskname/boot/grub/menu.lst
```

Look for the boot entry that you normally use for Ubuntu. e.g.
```
title        Ubuntu - kernel 2.6.31-22-generic
uuid         af60c425-1def-43fa-a30e-28fc50ecd4ca
kernel       /boot/[COLOR="Red"]vmlinuz-2.6.31-22-generic[/COLOR] root=UUID=af60c425-1def-43fa-a30e-28fc50ecd4ca ro quiet splash 
initrd       /boot/[COLOR="Red"]initrd.img-2.6.31-22-generic[/COLOR]
```

The parts in red are the parts you may need to modify. So look for these files in /media/diskname/boot/, and if they don't exist, there's your problem. Update them to ones that do exist.

If they *do* exist, then there's nothing wrong with grub, your problem lies elsewhere. Try to boot into Ubuntu normally, and make a note of the exact error you get, then post it here. If it just hangs while trying to boot Ubuntu, then try booting into single mode (just edit the kernel line so that it has "single" in it, remove "quiet splash" too, for verbose output during boot), e.g.
```
kernel       /boot/vmlinuz-2.6.31-22-generic root=UUID=af60c425-1def-43fa-a30e-28fc50ecd4ca ro **single**
```

---

### Post by joey00 on 2010-11-16
> **WorMzy said:**
> Sod update-grub, this is grub legacy, we can do things *properly*. >:D

First, boot into a LiveCD. Mount your Ubuntu partition and open it's menu.lst in gedit with gksu. e.g.
```
gksu gedit /media/diskname/boot/grub/menu.lst
```Look for the boot entry that you normally use for Ubuntu. e.g.
```
title        Ubuntu - kernel 2.6.31-22-generic
uuid         af60c425-1def-43fa-a30e-28fc50ecd4ca
kernel       /boot/[COLOR=Red]vmlinuz-2.6.31-22-generic[/COLOR] root=UUID=af60c425-1def-43fa-a30e-28fc50ecd4ca ro quiet splash 
initrd       /boot/[COLOR=Red]initrd.img-2.6.31-22-generic[/COLOR]
```The parts in red are the parts you may need to modify. So look for these files in /media/diskname/boot/, and if they don't exist, there's your problem. Update them to ones that do exist.

If they *do* exist, then there's nothing wrong with grub, your problem lies elsewhere. Try to boot into Ubuntu normally, and make a note of the exact error you get, then post it here. If it just hangs while trying to boot Ubuntu, then try booting into single mode (just edit the kernel line so that it has "single" in it, remove "quiet splash" too, for verbose output during boot), e.g.
```
kernel       /boot/vmlinuz-2.6.31-22-generic root=UUID=af60c425-1def-43fa-a30e-28fc50ecd4ca ro **single**
```


This looks like the right way to go. AFAIK everything is still ok on the system, with the exception of missing kernels. 

The old Grub comes up normally, but the only thing that works is Mem86 and Windows selections.  The 2 ubuntu kernel selections just drop through to error 15 file not found or similar. A further keypress brings up the grub menu again with its countdown...

But whilst I understand your instructions, I fall at the first one: Mount the ubuntu partition.

I did a search for this and find the "explanations" contradictory and confusing. Can you give me something very simple here? It is sda3 which contains the ubuntu.

I need to create a mountpoint, but isnt this maybe going to overwrite something?

The files missing (in red) are certainly removed and need updating anyhow (my original reason for removing them). I just amend the numbers of the red lines to give existing files. The uuids don' t need to be touched?

I somehow managed to blunder into the right places for grub. I made the changes. I will let u know what happened.

---

### Post by WorMzy on 2010-11-16
Once you've booted into a LiveCD, you just need to open nautilus (file browser) and click on your Ubuntu partition under the places sidebar. e.g. [http://img221.imageshack.us/img221/4581/20101116175438775x558sc.png](http://img221.imageshack.us/img221/4581/20101116175438775x558sc.png)

Alternatively, you can mount it from the command line, if you prefer that method. Just run (so long as you're sure that it's sda3, and that the filesystem is ext3 - run "sudo blkid" in a separate terminal to check)
```
sudo mount -t ext3 /dev/sda3 /mnt
```

You don't need to worry about overwriting anything, /mnt is an empty directory by default, and besides - you're in a temporary LiveCD environment. Once your partition is mounted, however, any changes you make to it's files are persistent, so be careful.

---

### Post by WorMzy on 2010-11-16
Oh, and you shouldn't need to modify the UUIDs, unless you've manually generated new ones for your partitions, they shouldn't have changed.

---

### Post by joey00 on 2010-11-16
> **WorMzy said:**
> Once you've booted into a LiveCD, you just need to open nautilus (file browser) and click on your Ubuntu partition under the places sidebar. e.g. [http://img221.imageshack.us/img221/4581/20101116175438775x558sc.png](http://img221.imageshack.us/img221/4581/20101116175438775x558sc.png)

Alternatively, you can mount it from the command line, if you prefer that method. Just run (so long as you're sure that it's sda3, and that the filesystem is ext3 - run "sudo blkid" in a separate terminal to check)
```
sudo mount -t ext3 /dev/sda3 /mnt
```You don't need to worry about overwriting anything, /mnt is an empty directory by default, and besides - you're in a temporary LiveCD environment. Once your partition is mounted, however, any changes you make to it's files are persistent, so be careful.


Thx.
That' s a lot clearer than what I had earlier.  :)

The changes I made to menu.lst didn't "take".  So I just did them again. Taking great care with my sudos and unmounts.

I will get back on this soon.

Thx again!  At least by your method I think I know what I am doing! :)

---

### Post by WorMzy on 2010-11-16
You will need to use sudo to edit that file. Or you should use gksudo if you're using a graphical application like gedit. Also, make sure that you're editing the right menu.lst. If you edit /boot/grub/menu.lst, then that's the LiveCD's menu.lst, and the changes will be lost when you restart. Make sure you're editing the menu.lst in /mnt/boot/grub, or /media/disk/boot/grub, depending on which method you used to mount the disk. :)

---

### Post by joey00 on 2010-11-16
> **WorMzy said:**
> You will need to use sudo to edit that file. Or you should use gksudo if you're using a graphical application like gedit. Also, make sure that you're editing the right menu.lst. If you edit /boot/grub/menu.lst, then that's the LiveCD's menu.lst, and the changes will be lost when you restart. Make sure you're editing the menu.lst in /mnt/boot/grub, or /media/disk/boot/grub, depending on which method you used to mount the disk. :)

Thx. for your clear and concise help. 

I finally got the whole system up and running again. :)

This time the changes worked!

And, thx to everyone who contributed (even tho I was too stupid to follow their advice). :(

---

### Post by WorMzy on 2010-11-16
Glad to hear it's all working again. Just make sure that you learn from the experience and make sure to update your menu.lst next time you remove old kernels. Or switch to grub2, which is supposedly easier to maintain than grub2 (I'm a firm non-believer here, in case you didn't already notice; I like my grub legacy and I'm not moving, but you may it's easier for you.)

---

### Post by joey00 on 2010-11-18
> **WorMzy said:**
> Glad to hear it's all working again. Just make sure that you learn from the experience and make sure to update your menu.lst next time you remove old kernels. Or switch to grub2, which is supposedly easier to maintain than grub2 (I'm a firm non-believer here, in case you didn't already notice; I like my grub legacy and I'm not moving, but you may it's easier for you.)
Switch to grub2? Not if I can help it!!

I can get the old grub to do what I want, easily; but grub2 is not as easy to sort out.

To a relative novice, grub2 looks like a change for the worse where no change was needed!  :)

---

