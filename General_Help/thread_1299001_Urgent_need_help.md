---
title: "Urgent need help"
date: 2009-10-23
forum: General Help
---

### Post by confusedxp on 2009-10-23
I need to change my dual boot from Ubuntu back to Windows. The problem is that I cant log in Windows because my keyboard doesnt work on the boot manager. So basically my system automatically boots Ubuntu instead of Windows and I want to change back to Windows not Ubuntu. Is there any way to do this through Ubuntu!!

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> I need to change my dual boot from Ubuntu back to Windows. The problem is that I cant log in Windows because my keyboard doesnt work on the boot manager. So basically my system automatically boots Ubuntu instead of Windows and I want to change back to Windows not Ubuntu. Is there any way to do this through Ubuntu!!

Bluetooth keyboard? It sounded like a good idea, huh? ;)

What release of Ubuntu are you running?

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> Bluetooth keyboard? It sounded like a good idea, huh? ;)

What release of Ubuntu are you running?

9.04
and no its not a bluetooth its a keyboard normal keyboard that used to be attached to a green connector thing but it broke so now its only a usb

---

### Post by M4rotku on 2009-10-23
I would, within Ubuntu, install startup-manager "sudo apt-get install startupmanager" and select Windows as the default boot.  However, I don't know how you would go about booting into Ubuntu afterwards since then you would be stuck with Windows being the default and not being able to move the highlight down to select Ubuntu.

---

### Post by confusedxp on 2009-10-23
> **M4rotku said:**
> I would, within Ubuntu, install startup-manager "sudo apt-get install startupmanager" and select Windows as the default boot.  However, I don't know how you would go about booting into Ubuntu afterwards since then you would be stuck with Windows being the default and not being able to move the highlight down to select Ubuntu.

i typed this in terminal this is what i get
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
teddycrisps@ubuntu:~$ sudo apt-get install startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by P4man on 2009-10-23
To get the keyboard working again before any OS is loaded, youll need to borrow a PS2 keyboard from someone, then go in to your bios and enable "legacy USB support". That will enable your own USB keyboard to work in the bootloader, and oh irony, in the BIOS (I bet you cant get in the bios now either).

---

### Post by P4man on 2009-10-23
> **confusedxp said:**
> i typed this in terminal this is what i get
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
teddycrisps@ubuntu:~$ sudo apt-get install startupmanager
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

You have another program like synaptic or add/remove programs running. Close them and try again (though you can use either of those to install startup manager as well).

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> 9.04
and no its not a bluetooth its a keyboard normal keyboard that used to be attached to a green connector thing but it broke so now its only a usb

Ah. I have one of those under my desk.

Please open a terminal window and type ```
gksu gedit /boot/grub/menu.lst
```

Now, scroll down to where the kernel is defined and you'll see that there are groups of definitions that begin with a "title" clause.

Count those, starting from zero, ie the first one's zero, the second is one, etc.

There may be a real short one that's used as a separator, but count that "title" entry too.

Note the number of the Windows entry.

Now, scroll back to the top and look for the "default" entry. It probably says "0" for the value. Replace that with the Windows entry number from the previous step.

Save it. Exit.

Type: ```
sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
```

That will do it. Reboot and the default boot OS will be Windows.

You'll be happier if you get a new keyboard. ;)

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> Ah. I have one of those under my desk.

Please open a terminal window and type ```
gksu gedit /boot/grub/menu.lst
```Now, scroll down to where the kernel is defined and you'll see that there are groups of definitions that begin with a "title" clause.

Count those, starting from zero, ie the first one's zero, the second is one, etc.

There may be a real short one that's used as a separator, but count that "title" entry too.

Note the number of the Windows entry.

Now, scroll back to the top and look for the "default" entry. It probably says "0" for the value. Replace that with the Windows entry number from the previous step.

Save it. Exit.

Type: ```
sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
```That will do it. Reboot and the default boot OS will be Windows.

You'll be happier if you get a new keyboard. ;)

these are the titles now whatÉ what is the windows entry
title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> these are the titles now whatÉ what is the windows entry


Nice. You don't have a Windows partition defined.

Let's add one.

Please post the output of ```
sudo fdisk -l
```

---

### Post by confusedxp on 2009-10-23
teddycrisps@ubuntu:~$ teddycrisps@ubuntu:~$ sudo fdisk -l
bash: teddycrisps@ubuntu:~$: command not found
teddycrisps@ubuntu:~$ 
teddycrisps@ubuntu:~$ Disk /dev/sda: 640.1 GB, 640135028736 bytes
bash: Disk: command not found
teddycrisps@ubuntu:~$ 255 heads, 63 sectors/track, 77825 cylinders
bash: 255: command not found
teddycrisps@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
teddycrisps@ubuntu:~$ Disk identifier: 0xcfabcfab
bash: Disk: command not found
teddycrisps@ubuntu:~$ 
teddycrisps@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
teddycrisps@ubuntu:~$ /dev/sda1   *           1       77824   625121248+   7  HPFS/NTFS
bash: /dev/sda1: Permission denied
teddycrisps@ubuntu:~$ teddycrisps@ubuntu:~$ 
bash: teddycrisps@ubuntu:~$: command not found
teddycrisps@ubuntu:~$

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> Nice. You don't have a Windows partition defined.

Let's add one.

Please post the output of ```
sudo fdisk -l
```
teddycrisps@ubuntu:~$ sudo fdisk -l
[sudo] password for teddycrisps: 

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcfabcfab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       77824   625121248+   7  HPFS/NTFS
teddycrisps@ubuntu:~$

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> teddycrisps@ubuntu:~$ teddycrisps@ubuntu:~$ sudo fdisk -l
bash: teddycrisps@ubuntu:~$: command not found
teddycrisps@ubuntu:~$ 
teddycrisps@ubuntu:~$ Disk /dev/sda: 640.1 GB, 640135028736 bytes
bash: Disk: command not found
teddycrisps@ubuntu:~$ 255 heads, 63 sectors/track, 77825 cylinders
bash: 255: command not found
teddycrisps@ubuntu:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
bash: Units: command not found
teddycrisps@ubuntu:~$ Disk identifier: 0xcfabcfab
bash: Disk: command not found
teddycrisps@ubuntu:~$ 
teddycrisps@ubuntu:~$    Device Boot      Start         End      Blocks   Id  System
bash: Device: command not found
teddycrisps@ubuntu:~$ /dev/sda1   *           1       77824   625121248+   7  HPFS/NTFS
bash: /dev/sda1: Permission denied
teddycrisps@ubuntu:~$ teddycrisps@ubuntu:~$ 
bash: teddycrisps@ubuntu:~$: command not found
teddycrisps@ubuntu:~$

Uh... You entered that incorrectly. Try to use cut/paste for the rest of this. An l and a | and a 1, and an I can get misinterpreted by the eye...

So let's open the menu.lst file again: ```
gksu gedit /boot/grub/menu.lst
```

Scroll to the last title entry and move the cursor down to the next blank line. Hit Enter to create another blank line and paste this in: ```
title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```

Now go back to the top and change the "default" value to 5.

Save and exit.

Then enter the grub-install command again.
```
sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
```

(Select that line, hit Ctrl-C, click in the terminal window, hit Shift-Insert, and press enter.)

That will install a new master boot record with the new grub menu you just created. Reboot. After the timeout, it should boot Windows. Please bring this thread back up from Windows and mark the thread SOLVED.

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> Uh... You entered that incorrectly. Try to use cut/paste for the rest of this. An l and a | and a 1, and an I can get misinterpreted by the eye...

So let's open the menu.lst file again: ```
gksu gedit /boot/grub/menu.lst
```Scroll to the last title entry and move the cursor down to the next blank line. Hit Enter to create another blank line and paste this in: ```
title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```Now go back to the top and change the "default" value to 5.

Save and exit.

Then enter the grub-install command again.
```
sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
```(Select that line, hit Ctrl-C, click in the terminal window, hit Shift-Insert, and press enter.)

That will install a new master boot record with the new grub menu you just created. Reboot. After the timeout, it should boot Windows. Please bring this thread back up from Windows and mark the thread SOLVED.

will I have all my programs back

---

### Post by confusedxp on 2009-10-23
> **confusedxp said:**
> will I have all my programs back
teddycrisps@ubuntu:~$ sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
/dev/fd0: Not found or not a block device.
teddycrisps@ubuntu:~$ 
teddycrisps@ubuntu:~$

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> Uh... You entered that incorrectly. Try to use cut/paste for the rest of this. An l and a | and a 1, and an I can get misinterpreted by the eye...

So let's open the menu.lst file again: ```
gksu gedit /boot/grub/menu.lst
```Scroll to the last title entry and move the cursor down to the next blank line. Hit Enter to create another blank line and paste this in: ```
title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1
```Now go back to the top and change the "default" value to 5.

Save and exit.

Then enter the grub-install command again.
```
sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
```(Select that line, hit Ctrl-C, click in the terminal window, hit Shift-Insert, and press enter.)

That will install a new master boot record with the new grub menu you just created. Reboot. After the timeout, it should boot Windows. Please bring this thread back up from Windows and mark the thread SOLVED.

this are my titles
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-16-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
root        ()/ubuntu/disks
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=5C248C62248C40CE loop=/ubuntu/disks/root.disk ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
root        ()/ubuntu/disks
kernel        /boot/memtest86+.bin

title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> teddycrisps@ubuntu:~$ sudo grub-install `head -1 /boot/grub/device.map | awk '{ print $2 }'`
/dev/fd0: Not found or not a block device.
teddycrisps@ubuntu:~$ 
teddycrisps@ubuntu:~$

A floppy drive.

Use this command instead: ```
sudo grub-install `grep hd0 /boot/grub/device.map | head -1 | awk '{ print $2 }'`
```

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> A floppy drive.

Use this command instead: ```
sudo grub-install `grep hd0 /boot/grub/device.map | head -1 | awk '{ print $2 }'`
```

i think i like ubuntu now i just need to figure out some stuff
how do i reset my config file

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> i think i like ubuntu now i just need to figure out some stuff
how do i reset my config file

Are you in Windows?

Do you mean 'how do I boot back to Ubuntu?'

Your best bet is to get a new keyboard so that you can use the grub menu and, if need be, adjust your clock in BIOS... :(

---

### Post by confusedxp on 2009-10-23
> **Giblet5 said:**
> Are you in Windows?

Do you mean 'how do I boot back to Ubuntu?'

no

---

### Post by confusedxp on 2009-10-23
> **confusedxp said:**
> no
basically
1) how do i get my accessories menu back i removed it
2) how do i change my keyboard so i can actually hold backspace to erase without it beeping
3) also how do i reset my config terminal to default because i messed it up
thanks

---

### Post by Giblet5 on 2009-10-23
If you look at the way menu.lst is structured and read the comments, it's pretty straight forward (not all config files are).

It will be difficult or impossible for you to boot back into Ubuntu until you get a new keyboard. I have four or five of them sitting around right now, and they can be gotten for a buck or two at a thrift shop.

Without keyboard support at boot time, you can't access BIOS (bad), you can't use the grub menu (annoying), and you can't boot from a CD (disastrous if your OS dies).

Get a keyboard.

Once you have a new keyboard, you may want to edit that menu.lst again, placing the Windows entry up towards the top. That way, Windows will appear first in the menu, and it won't get overwritten by "update-grub" (whenever the kernel gets patched).

I always set my "default" to "saved" and make sure that every entry has a "makedefault" option. That way, a reboot while I'm not watching (ala Windows update) will boot to whatever I was running last.

---

### Post by Giblet5 on 2009-10-23
> 1) how do i get my accessories menu back i removed it

You can use the main menu editor (System menu -> Preferences -> Main Menu)


> 2) how do i change my keyboard so i can actually hold backspace to erase without it beeping

Mine doesn't beep. Did you select the correct keyboard mapping during the install?

Check in System menu -> Preferences -> Keyboard

That's probably what you need.


Note: You can always play with Ubuntu default settings using these steps:

Log off.
Flip to the console via CtrlAltF1.
Log in.
Type ```
mkdir conf-backup
mv .gconf* .gnome* .config conf-backup
exit
```
Flip back to the GUI via CtrlAltF7.
Log in.

Simple and elegant.

To move your backup config:

Log off.
Flip to the console via CtrlAltF1.
Log in.
Type ```
rm -fr .gconf* .gnome* .config
cd conf-backup
mv .gconf* .gnome* .config $HOME
exit
```
Flip back to the GUI via CtrlAltF7.
Log in.

Everything's back.

---

### Post by confusedxp on 2009-10-23
this is what i get when i dowat u told me to do to get windows
teddycrisps@ubuntu:~$ sudo grub-install `grep hd0 /boot/grub/device.map | head -1 | awk '{ print $2 }'`
[sudo] password for teddycrisps: 
Searching for GRUB installation directory ... found: /boot/grub
The file /boot/grub/stage1 not read correctly.
teddycrisps@ubuntu:~$

---

### Post by P4man on 2009-10-23
Just for the record, if you broke the purple  PS2 connector on your motherboard and not the keyboard (or its adaptor) then you're in serious trouble. If its the just keyboard, as suggested above buy, borrow  or steal or PS2 keyboard. You can probably set your bios in such a way that it works with the usb keyboard, but you first need a PS2 keyboard to get in to the bios.

edit. and Giblet5s solution is very elegant, but startup manager is probably a whole lot easier for you to change the boot priority. Just realize either approach is a one way street. It will let you boot windows but not more ubuntu until you get that PS2 kb. If you have anything to backup do it NOW

---

### Post by confusedxp on 2009-10-23
> **p4man said:**
> just for the record, if you broke the purple  ps2 connector on your motherboard and not the keyboard (or its adaptor) then you're in serious trouble. If its the just keyboard, as suggested above buy, borrow  or steal or ps2 keyboard. You can probably set your bios in such a way that it works with the usb keyboard, but you first need a ps2 keyboard to get in to the bios.

Edit. And giblet5s solution is very elegant, but startup manager is probably a whole lot easier for you to change the boot priority. Just realize either approach is a one way street. It will let you boot windows but not more ubuntu until you get that ps2 kb. If you have anything to backup do it now

all i want is to log into ******* windows
how the **** do i download startupmanager link it to me

---

### Post by Giblet5 on 2009-10-23
> **P4man said:**
> Just for the record

Thanks for the alternative. I've never used Startup-Manager. Does it search for Windows partitions and add them to the mix?

/Hate grub. Makes me stabby.

---

### Post by Giblet5 on 2009-10-23
> **confusedxp said:**
> all i want is to log into ******* windows
how the **** do i download startupmanager link it to me

```
apt-get install startupmanager
```

I'm not sure how successful that will be given the stage 1 error that you got from grub...

I have no experience with that tool.

PS:
You may be able to fix the stage 1 error via ```
sudo grub-install --recheck /dev/hd0
```

It *sounds* like you've moved physical drives around since the install.

---

### Post by P4man on 2009-10-23
> **Giblet5 said:**
> Thanks for the alternative. I've never used Startup-Manager. Does it search for Windows partitions and add them to the mix?

/Hate grub. Makes me stabby.

No. It doesnt rewrite the menu.lst entirely, its just changes a few parameters like the default boot OS / kernel, number of kernels, timeout and stuff like that. But afaik it will neither add nor remove other entries or settings. If it does then at least it seems to pick up windows each time Ive run it :)

Its not the greatest tool ever (for instance I absolutely hate how it doesnt let you quit without applying!) but one nice thing about it is that it supports both grub and grub2.

---

