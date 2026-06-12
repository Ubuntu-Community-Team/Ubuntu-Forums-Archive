---
title: "Dual-boot"
date: 2009-09-11
forum: General Help
---

### Post by Lyerae on 2009-09-11
I have a couple Dual-boot questions:
1. Is it possible to have several Linux distros dual-booting on the same computer?
2. If possible, what would I need to do? Just make a new partition?
3. Is there a way to make it so it will automatically load "Ubuntu Linux 9.04", unless I hit a specific key, and boot into another OS?

Thanks for any help.

---

### Post by iswear on 2009-09-12
1. Yes
2. Go look up geparted and read up on it.
3. When you dual boot youll get a screen that comes up when you start your computer that looks like this [IMG]http://www.tecnobot.com/wp-content/uploads/2008/01/ubuntu5.jpeg[/IMG] from here you can change witch os you want to enter.
I hope i answered all your questions.

---

### Post by Lyerae on 2009-09-12
Yep. Thanks.

Edit:
Actually, it's possible to install 9.04, and then the netbook edition with no problems right? Without losing any data.

---

### Post by snakepit # on 2009-09-12
> **Lyerae said:**
> I have a couple Dual-boot questions:
1. Is it possible to have several Linux distros dual-booting on the same computer?
2. If possible, what would I need to do? Just make a new partition?
3. Is there a way to make it so it will automatically load "Ubuntu Linux 9.04", unless I hit a specific key, and boot into another OS?

Thanks for any help.

On my laptop, I have:

Slackware 13  64 (Primary OS)
Windows Vista 64
Slackware 3.2 (Nostalgia, my first GNU/Linux)
openSUSE 11.1 64
FreeBSD 64
Ubuntu "Satanic Edition" 64  (For the hell of it.  Pun intended.)

The extremely quick n' dirty:

Each GNU/Linux resides in their own partition.  They can all share the share the same swap partition though.  You can only have four primary partitions, make one an extended partition with logical drives for your Linuxes.  Have a main bootloader in your MBR. Install all the other bootloaders to their root partition.  Expect your devices to change during installations, no matter how good your plan is.  You will do some juggling.  Repair act: temp mount one OS using another to change it's /etc/fstab, bootloader, etc..  Learn UUID's, they will make life easier in the long run. The main thing is that you can't do foreheaded installs (banging your forehead on the enter key), you must carefully select your partitions during installs.  You also must carefully select how the bootloader is installed to their respective root partitions and nothing jacks up the MBR.   In distro's like Ubuntu and openSUSE, these options are usually 'hidden' under 'advanced'.  

Don't get carried away with the root partitions' bootloaders and chain everything together.  You will end up with a spaghetti headache.  You already pressed enter once to choose an OS, so go with it.  Eventually you will be building your own kernels and that is what the root partitions' bootloaders are for. 

Yeah, all bootloaders have that behavior.  One OS will be a default unless you interact within your preset timeout limit.

If you have Windows on your computer too, check out Boot-US.  It works well for the MBR.

---

### Post by Lyerae on 2009-09-12
Well, I installed the netbook remix, but I have a problem... It's set that to the default OS, which I don't want. How do I fix that? I just want it to automatically load Ubuntu 9.04 desktop edition...

---

### Post by snakepit # on 2009-09-12
Grub or lilo?

---

### Post by Lyerae on 2009-09-12
The bootup thing? I believe its Grub.

---

### Post by snakepit # on 2009-09-12
Look for 'default' in /boot/grub/menu.lst

then

(I'm going to assume its installed on the first drive, which you said is a netbook, so must be, and you are installing to MBR)

# grub

root (hd0, N)
setup (hd0,0)

...

N being the (-1) device number. Edit: which device/partition is it on?  First: will be (hd0,0) Second will be  (hd0,1), etc.

Sorry, I'm in Slack at present and I mainly use lilo and need to be in Ubuntu to remember the Ubuntu'isms.

---

### Post by Lyerae on 2009-09-12
Well. I installed 9.04 first, and then netbook.
Okay, now is there a way to recover if I mess it up? Because if I make a mistake, there'll be a good bit of data I'll lose, and I can't back it up.

---

### Post by snakepit # on 2009-09-12
Just to make sure, can you do this ...

$ cat /etc/fstab

...and then copy/paste the output here?

---

### Post by oboedad55 on 2009-09-12
> **snakepit # said:**
> On my laptop, I have:

Slackware 13  64 (Primary OS)
Windows Vista 64
Slackware 3.2 (Nostalgia, my first GNU/Linux)
openSUSE 11.1 64
FreeBSD 64
Ubuntu "Satanic Edition" 64  (For the hell of it.  Pun intended.)

The extremely quick n' dirty:

Each GNU/Linux resides in their own partition.  They can all share the share the same swap partition though.  You can only have four primary partitions, make one an extended partition with logical drives for your Linuxes.  Have a main bootloader in your MBR. Install all the other bootloaders to their root partition.  Expect your devices to change during installations, no matter how good your plan is.  You will do some juggling.  Repair act: temp mount one OS using another to change it's /etc/fstab, bootloader, etc..  Learn UUID's, they will make life easier in the long run. The main thing is that you can't do foreheaded installs (banging your forehead on the enter key), you must carefully select your partitions during installs.  You also must carefully select how the bootloader is installed to their respective root partitions and nothing jacks up the MBR.   In distro's like Ubuntu and openSUSE, these options are usually 'hidden' under 'advanced'.  

Don't get carried away with the root partitions' bootloaders and chain everything together.  You will end up with a spaghetti headache.  You already pressed enter once to choose an OS, so go with it.  Eventually you will be building your own kernels and that is what the root partitions' bootloaders are for. 

Yeah, all bootloaders have that behavior.  One OS will be a default unless you interact within your preset timeout limit.

If you have Windows on your computer too, check out Boot-US.  It works well for the MBR.

Why stop at six? Try 145! [http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

---

### Post by snakepit # on 2009-09-12
I have to get to bed, but don't want you to get 'locked out'.
(Which is fixable, but you have to know how to set mount points, etc)

I'm going to give you an **example** of how I would reinstall grub to my MBR.

(Please excuse me as I mainly use lilo for bootloaders and I'm not in Ubuntu at moment)

This is how I would go about making my present OS the default and reinstalling grub to MBR.
(I use root partitions for lilo, but this is as example.)

First, go into /boot/grub/menu.lst  and find the "default" and change it to preferred boot.  It will be self explained when you look at it.  Edit it and save it.

Double check my current root partition

root@snakepit:~# ***cat /etc/fstab***

/dev/sda8        swap             swap        defaults         0   0
/dev/sda7       /                ext4        defaults         1   1
(All other partitions and devices ommited.)

Ok, my root ("/") is on sda7 on the first drive, so 

*# **grub*** (in Ubuntu, you'll need to do # **sudo grub **)
[I]
grub> **root (hd0,6)**
[/I]
(hd0 = first drive, 6 = sda7.  Remember the format is -1 the device num.)
(This is telling the grub installer "Where the root partition is".)

*grub> **setup (hda0,0)***
(hd0 = first drive, 0 = MBR)
(This is telling the grub installer "Where to actually install Grub at")

---

### Post by snakepit # on 2009-09-12
> **oboedad55 said:**
> Why stop at six? Try 145! [http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

lol

Now thats just WAY too much time on your hands...

---

### Post by oboedad55 on 2009-09-12
> **snakepit # said:**
> lol

Now thats just WAY too much time on your hands...

I've felt like that. You should know something's seriously amiss when you've got six Linux versions and a never-used (just in case!) Windslow XP. I'm still indoctrinated with Windows after many years of using Linux. It's like having a case of the creeping crud that won't go away. You try creams, penicillin, ointments, etc. and yet you still itch. That's me...

---

### Post by Lyerae on 2009-09-12
Okay... This is kinda confusing... Is there an easier way to do it?

---

