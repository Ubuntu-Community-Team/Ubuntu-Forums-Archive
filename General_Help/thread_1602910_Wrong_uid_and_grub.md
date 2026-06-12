---
title: "Wrong uid and grub"
date: 2010-10-22
forum: General Help
---

### Post by khaos1 on 2010-10-22
Hi guys I'm using 10.10 (updated from 10.04) and from the 10.04 I had problems when the system updated the kernel. After a kernel upgrade I can't boot to my other linux(Backtrack) due to wrong uuids. I must go to /boot/grub/grub.cfg and remove the uid and put /dev/sda5 for example. If I don't edit backtrack loads to busybox.

Is there any way to fix that parameteres permantly? Because I don't want to make this change every time.

Is the grub changed to 10.10 to a new config file?

Any help is appreciated

Thanks in advance

---

### Post by AoSteve on 2010-10-22
Have you tried updating with update-grub?   

```
sudo update-grub
```

---

### Post by khaos1 on 2010-10-22
> **AoSteve said:**
> Have you tried updating with update-grub?   

```
sudo update-grub
```

Thanks for your reply
Yep... And Backtrack can't load. Wrong uid. Is there any way to fix it automatically and permantly?

update-grub fixed my wrong uid only in my main distro the 10.10 not for the other..
Windows is working ok. Only backtrack is the prob. Cause I have 3 OS :p

Is something wrong with fstab? Or I must run update-grub from my backtrack?

---

### Post by mcduck on 2010-10-22
/boot/grub/grub.cfg has never been the file you were supposed to edit, so nothing has changed in that sense. It even tells you in the very file itself that you shouldn't edit it. :)

The files you should use to configure Grub2 are /etc/default/grub (for generic settings) and files located in /etc/grub.d (individual boot options & OS detection).

After making any changes to these files you need to run "sudo update-grub" and Grub will generate the grub.cfg for you. Which is also what happens durng any updates and such, and that should explain why you shouldn't edit the grub.cfg yourself even if you are sure you don't do any mistakes. Kind of the same thing as with the default options section in the menu.lst file that was used by the old Grub, changing settings without changing the default settings will result in your changes disappearing sooner or later.

edit: BTW; if you have configured the Backtrack partiton to mount in Ubuntu you should probably check that you have correct UUID for it in /etc/fstab. But really, simply running "sudo update-grub" should fix your problem unless there's something strange on your system.

---

### Post by Rubi1200 on 2010-10-22
Did you install Backtrack after Ubuntu?

Post the output of 
```
cat /etc/fstab 
sudo blkid
```

Thanks.

---

### Post by khaos1 on 2010-10-22
I don't remember which I installed first. But I have some problems with the bt4 uuid

My fstab:


> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=f5c2f6a2-798d-4a99-a816-be11148fb760 /               ext4    errors=remount-ro 0       1
# /backtrack was on /dev/sda7 during installation
/dev/sda7 /backtrack      ext3    defaults        0       2
# /windows was on /dev/sda2 during installation
UUID=FEFC2874FC2828FB /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=1d81c0ba-7c1a-4cfb-b726-f31104be1f2f none            swap    sw              0       0

blkid:

> /dev/sda1: LABEL="PQSERVICE" UUID="846089046088FE64" TYPE="ntfs" 
/dev/sda2: LABEL="ACER" UUID="FEFC2874FC2828FB" TYPE="ntfs" 
/dev/sda5: UUID="f5c2f6a2-798d-4a99-a816-be11148fb760" TYPE="ext4" 
/dev/sda6: UUID="1d81c0ba-7c1a-4cfb-b726-f31104be1f2f" TYPE="swap" 
/dev/sda7: UUID="511258c8-1d20-4cc4-9c5e-7b6c1c19c06a" TYPE="ext3"

I must do that? 


UUID=511258c8-1d20-4cc4-9c5e-7b6c1c19c06a to the backtrack4?
and after upgrade grub?

If you want to paste my grub settings, just tell me.

I have this > #GRUB_DISABLE_LINUX_UUID=true on my /etc/default/grub

---

### Post by khaos1 on 2010-10-22
I think that I fixed that by chaning the /dev/sda7 uuid. It was generated wrong.

I used the tun2fs command

---

### Post by Rubi1200 on 2010-10-22
Thanks for posting the information.

Is the problem resolved now?

If what you did was add the UUID for Backtrack into fstab, then it should be all good right?

If you want me to take another look, post the output of the commands again.

Thanks.

By the way, if you think this is resolved, please mark this thread Solved using the Thread Tools near the top of the page.

---

### Post by khaos1 on 2010-10-22
Yes and No, The problem was that the uuid of my disk changed due to a disk restore I think

I think that the uuid of backtrack4 changed due to a restore that I made. So it needed to change the uuid of the /dev/sda7 that backtrack4 runs to the current due the change. I think that all fixed now. Ofcourse I edited the fstab too in order to enter the uuid.

I found that cause when I update the grub the grub.cfg auto changes the uuid of bt4 partition to a specific uuid (different from this I believed) so I changed it with the tun2fs command and now it works ok. I tested it and I updated grub again and the BackTrack is loading ok now...

The command that I used is:

> tune2fs -U UUID_THAT_WE_WANT_HERE /dev/sda7

Thanks for the help guys. Many thanks!

I still have an issue with the backtrack but it's not so important.
I made a thread cause its a bit different:

[http://ubuntuforums.org/showthread.php?p=10010104#post10010104](http://ubuntuforums.org/showthread.php?p=10010104#post10010104)

---

