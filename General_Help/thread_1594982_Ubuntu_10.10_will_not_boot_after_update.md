---
title: "Ubuntu 10.10 will not boot after update"
date: 2010-10-12
forum: General Help
---

### Post by SteveEdson on 2010-10-12
I updated ubuntu from 10.04, i had a dual boot with windows 7. It updated successfully, then restarted, then whenever I select ubuntu from my bootloader, it just resets the laptop back to the acer bios screen and takes me back to the bootloader. 

Any ideas on how to fix?

---

### Post by mailprashant07 on 2010-10-13
Yeah same problem. I am doing dual boot with vista but after selecting ubuntu in bootloader....screen goes to restart....happened after the recent update...

ne way to fix this.....

---

### Post by mailprashant07 on 2010-10-13
Any help will be highly appreciated.....thanks

---

### Post by playwaterfish on 2010-10-13
i have the same problem, i installed ubuntu10.04 in my windows vista with wubi, after updated to ubuntu10.10, i can't boot into the new ubuntu10.10, waiting for some guide.
Thanks.

---

### Post by v3rlon on 2010-10-13
Sounds like what I posted in another thread (with another Acer also)
 
I tried downloading the full 10.10 and installing that (erasing my old 10.04), and that also fails after the last restart.
 
10.04 does reinstall and work fine though.

---

### Post by mailprashant07 on 2010-10-13
Any way to solve this friends....???

---

### Post by JustinR on 2010-10-13
Can you post the contents of you '/boot/grub/grub.cfg' in [quote] tags?

And can you post the output of the command 'fdisk -l' from Applications > Accessories > Terminal?

---

### Post by mailprashant07 on 2010-10-13
Unfortunately...it is like this--> When u click on ubuntu in bootloader....system restarts......


                     Windows boot manger

Microsoft windows vista
Ubuntu

---

### Post by JustinR on 2010-10-13
> **mailprashant07 said:**
> Unfortunately...it is like this--> When u click on ubuntu in bootloader....system restarts......


                     Windows boot manger

Microsoft windows vista
Ubuntu

Can you use the Ubuntu Live CD, and select 'Try Ubuntu'. Mount your hard drive with 'System > Administration > Disk Utility'.
Navigate to /boot/grub/grub.cfg and post the results of that, if you can.

---

### Post by mailprashant07 on 2010-10-13
Unfortunately I dont have CD since I installed from internet using wubi...I guess some of friends may help here....and yeah thank u for ur response...

---

### Post by mangloid on 2010-10-13
do you have at least a 1gig usb stick to make a live usb to check drive?


try to do edit from the grub menu and see what it shows.

---

### Post by bcbc on 2010-10-13
Here is a workaround. [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by mailprashant07 on 2010-10-13
oh....I think grub got deleted...

this is where I go--> C-->ubuntu-->disks-->boot-->grub-->no files there

additionally i tried these by reading forum-->

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
ubuntu@ubuntu:~$ sudo fsck /win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/win/ubuntu/disks/root.disk: recovering journal
/win/ubuntu/disks/root.disk: clean, 259460/624624 files, 2121059/2494464 blocks
ubuntu@ubuntu:~$ 

I am ubuntu user for one year now but not a very techie person....any help will be highly appreciated...I dont want to reinstall the whole thing.......

thank u

---

### Post by mailprashant07 on 2010-10-13
I have made a live usb stick and booting from that....any step by step procedure will be appreciated.....


thanks

---

### Post by bcbc on 2010-10-13
> **mailprashant07 said:**
> oh....I think grub got deleted...

this is where I go--> C-->ubuntu-->disks-->boot-->grub-->no files there

additionally i tried these by reading forum-->

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
ubuntu@ubuntu:~$ sudo fsck /win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/win/ubuntu/disks/root.disk: recovering journal
/win/ubuntu/disks/root.disk: clean, 259460/624624 files, 2121059/2494464 blocks
ubuntu@ubuntu:~$ 

I am ubuntu user for one year now but not a very techie person....any help will be highly appreciated...I dont want to reinstall the whole thing.......

thank u

The grub.cfg is on the root.disk. So... you were nearly there:
```
ubuntu@ubuntu:~$ sudo mkdir /win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /win
ubuntu@ubuntu:~$ sudo mkdir /vdisk
ubuntu@ubuntu:~$ sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
ubuntu@ubuntu:~$ sudo chmod +w /vdisk/boot/grub/grub.cfg
ubuntu@ubuntu:~$ gksu gedit /vdisk/boot/grub/grub.cfg

```Delete everything from the first line up until the first "menuentry". It looks something like this:
> ### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
        insmod part_msdos
        insmod ntfs
...
Save and exit. Reboot.

PS don't run fsck on a mounted file system in future.

---

### Post by mailprashant07 on 2010-10-13
Oh thats cool...i did exactly as u told and everything is back to normal..... =D>=D>=D>

thank u :)

---

### Post by bcbc on 2010-10-13
> **mailprashant07 said:**
> Oh thats cool...i did exactly as u told and everything is back to normal..... =D>=D>=D>

thank u :)

Great :) You're welcome.

When you boot Ubuntu and run updates, there's a kernel update that will regenerate grub.cfg if you install it, so just reapply the fix before rebooting.

Also, I've seen reports that copying over the c:\ubuntu\winboot\wubildr to c:\wubildr fixes the problem. I cannot explain this, but a test on my own problem test wubi worked... I don't know if it matters what the original version of the wubi install was - mine was 10.04.1 - but if it works it's a lot better than having to edit grub.cfg all the time.

---

### Post by mailprashant07 on 2010-10-13
Oh great will remember from next time....

I guess this thread should be marked solved...... :)

---

### Post by mailprashant07 on 2010-10-13
And I think thread starter should be happy now....:)

---

### Post by fccluck on 2010-11-28
> **bcbc said:**
> Great :) You're welcome.

When you boot Ubuntu and run updates, there's a kernel update that will regenerate grub.cfg if you install it, so just reapply the fix before rebooting.

Also, I've seen reports that copying over the c:\ubuntu\winboot\wubildr to c:\wubildr fixes the problem. I cannot explain this, but a test on my own problem test wubi worked... I don't know if it matters what the original version of the wubi install was - mine was 10.04.1 - but if it works it's a lot better than having to edit grub.cfg all the time.

I have done this fix several times and it works great for me at least.  What is the permanent fix so we don't have to keep doing this?

---

### Post by bcbc on 2010-11-29
> **fccluck said:**
> I have done this fix several times and it works great for me at least.  What is the permanent fix so we don't have to keep doing this?

I replied here [http://ubuntuforums.org/showpost.php?p=10176276&postcount=75](http://ubuntuforums.org/showpost.php?p=10176276&postcount=75)

---

