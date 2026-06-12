---
title: "Is everything now gone :("
date: 2009-08-10
forum: General Help
---

### Post by joper90 on 2009-08-10
Ok, installed everything fine, got the nvidia drivers working etc etc.

Doing an update, it moaned that libdb4.3 was in a partial state, so i did and sudo apt-get --reinstall install libdb4.3, which all seemed to work.

I then did a update, halfway thru it seemed to remove the panel with the network and wireless on it, and then the network stopped working, ping gives network unreachable etc.

So.. I rebooted, just incase, big mistake.

All I now get in the grub menu is Ubuntu 9.04 memtest86+. 

Can someone help, and please explain what i did wrong.?

---

### Post by zkriesse on 2009-08-10
Most likely what you did wrong is a sudo command before the sys was done doing it's thing.

---

### Post by joper90 on 2009-08-10
Im 99% sure I just did exactly what i said, but I cannot understand why and what happened?

Is this a reinstall :(

---

### Post by zkriesse on 2009-08-10
let me research this and get back to you ok?

---

### Post by zkriesse on 2009-08-10
> **joper90 said:**
> Im 99% sure I just did exactly what i said, but I cannot understand why and what happened?

Is this a reinstall :(
it might have to be a fresh install but don't give up hope yet.

---

### Post by P4man on 2009-08-10
Did you perhaps reboot before the upgrade was complete ? Im guessing you got a prompt what to do with the grub menu, and you missed it or ignored it and rebooted.

Anyway, first thing you'd have to do is recover grub. Easiest way is using your cd and follow these instructions:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Then, assuming you can boot  jaunty again, you may have problems you can try solving by running:

```
sudo dpkg --configure -a
```

Can do wonders if you where half way an update.

---

### Post by joper90 on 2009-08-10
oks.. cheers for that.

im 99% sure i didn't reboot before it was complete, i hit the close on the update manager.

Will 'recreate grub' and see what happens.

thanks

---

### Post by martinbaselier on 2009-08-10
I don't know what you did wrong, but you can probably fix it from a live cd. 

Open a terminal on it

cd /mnt
sudo fdisk -l
pick your linux disk from it, in my case it's /dev/sda2

mkdir ubuntu
sudo mount /dev/sda2 ubuntu
cd boot
ls
You should see something like this:
abi-2.6.28-14-generic
config-2.6.28-14-generic
initrd.img-2.6.28-14-generic
System.map-2.6.28-14-generic
vmcoreinfo-2.6.28-14-generic
vmlinuz-2.6.28-14-generic


in /mnt/ubuntu/boot/grub/menu.lst you need to add some entries like these:

```

title		Debian GNU/Linux, kernel 2.6.28-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=95e26515-4968-47c6-a640-7ad7d79c68cd ro quiet splash
initrd		/boot/initrd.img-2.6.28-14-generic

title		Debian GNU/Linux, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=95e26515-4968-47c6-a640-7ad7d79c68cd ro single
initrd		/boot/initrd.img-2.6.28-14-generic

```
use 
sudo gedit /mnt/ubuntu/boot/grub/menu
to edit
replace the image, with the image name on your system.
make sure to use the correct drive:
sda1 -> hd0,0 / sda2 -> hd0,1
sdb1 -> hd1,0 / sdb5 -> hd1,4
and use the correct UUID
sudo blkid will show you the uuids

---

### Post by zkriesse on 2009-08-10
yeah....in this case you will have to use the cd to recover......sucks but hey.....the sacrifice for actual software that's worth something is having to be willing to learn how to use it....

---

### Post by joper90 on 2009-08-10
did a (from live cd)

sudo grub
find /boot/grub/stage1
root (hd0,0)
setup (hd0)
.
.. some output about it being sucessful
.


still only the memtest in the .lst file :(

---

### Post by P4man on 2009-08-10
are you installing it on the right disk or partition?

Can you boot the cd again, and run:

```
sudo fdisk -l
```

and post the output? While you're at it, also the output of 

```
find /boot/grub/stage1
```

In grub. 

BTW, if Im not too terribly, mistaken, you can also run those commands from GRUB itself, so without the cd. Not the fdisk one, but the grub commands.

---

### Post by joper90 on 2009-08-10
Ahh thats the problem:

abi-2.6.28-14-generic
config-2.6.28-14-generic
initrd.img-2.6.28-14-generic
System.map-2.6.28-14-generic
vmcoreinfo-2.6.28-14-generic
vmlinuz-2.6.28-14-generic

are all missing from /boot.

doh... which is not good.. me thinks a reinstall is the best way fwd here.

---

### Post by P4man on 2009-08-10
> **martinbaselier said:**
> 
sudo gedit /mnt/ubuntu/boot/grub/menu


Martin, sound advice, but make a habit of using **gksudo** for graphical apps like gedit. I know it doesn't really seem to give problems with gedit, but using sudo when gksudo is needed, can give so many headaches its a good idea not to teach bad habits :). I know Im still fighting my own bad habit of using sudo all the time :D

---

### Post by P4man on 2009-08-10
> **joper90 said:**
> Ahh thats the problem:

abi-2.6.28-14-generic
config-2.6.28-14-generic
initrd.img-2.6.28-14-generic
System.map-2.6.28-14-generic
vmcoreinfo-2.6.28-14-generic
vmlinuz-2.6.28-14-generic

are all missing from /boot.

doh... which is not good.. me thinks a reinstall is the best way fwd here.

thats indeed not good at all lol. Well, since it sounds like it was a very recent install, its indeed probably easiest to reinstall, but I wouldn't be happy not knowing how those kernels where deleted in the first place..Did you make a separate boot partition ?  Did you play around (a bit too much) with startupmanager perhaps? 

Anyway, better luck this time :s

---

### Post by joper90 on 2009-08-10
nope, I did nothing odd at all, bar what i said.
Will reinstall, with the kernel missing, its not going to go well.

Cheers all

---

### Post by zkriesse on 2009-08-10
It sounds like you're gonna have to reload the software at this point. But if you do....remember this...when you do a synaptic update, if you do a sudo command in terminal, it has a tendency to make things upset...be careful and let it do it's thing.

---

