---
title: "i think i am in over my head..."
date: 2010-01-25
forum: General Help
---

### Post by onyxvu on 2010-01-25
ok here is the story: 10 yr old Dell laptop with NO WORKING DRIVES. i was dual booting xp and xubuntu when i decided it was time to cut the cord. so i installed gparted and deleted my windows partition. now it won't boot. my assumption is that i never installed grub. i got a usb to ide cable so i can access the hard drive from my desktop (xp home edition). i read that grub should be in a folder called "boot". i see on my hard drive that i have: "disks", "winboot" "install", "uninstall-wubi.exe", and "xubuntu.ico".  if i expand the "disks" folder, there is a "boot" folder containing another folder called "grub", but the folder is empty. is this where i install it? am i an idiot and missing something stupid? where do i download grub if i need it? will the questions ever end? thanks in advance for any assistance...

---

### Post by Wataru8675 on 2010-01-25
As long as you can access your hard drive, you could just back it up, do a clean install of Xubuntu, and then put everything back, right?

---

### Post by mharrison on 2010-01-25
I could be wrong, and someone please correct me if I am, but it sounds like you had Xubuntu installed inside of Windows with WUBI and thus killing your Windows killed everything.  I know you said you have no working drives, but I think your only course of action would be to install a fresh copy of Xubuntu in order to get this machine running.

---

### Post by onyxvu on 2010-01-25
that is another option i was considering, i burned a cd to try because the cd drive somewhat works if you hold it in real tight but apparently not well enough. i did test on my desktop that the cd is bootable but what do i do with it? should i format the laptop hard drive and then copy the files on the cd to the hard drive or boot the desktop from the cd and install to the external laptop drive (if that is possible)? did you catch all that:D

---

### Post by mharrison on 2010-01-25
That really depends.  Do you have any data that you are concerned about?  If you don't care, I would try to do a clean install of Xubuntu from the CD, either specifying the partition sizes yourself, or letting the installer partition for you.  This should help you get a working machine again.

If you do have data, I will have to let someone else help you because trying to recover data would not be an area I have any expertise at.

Good luck!

---

### Post by onyxvu on 2010-01-25
no worries, i had previously backed up any important info. when i put the disk in my desktop, a pop-up asks if i want to install inside windows or reboot and boot from cd. in the boot from cd option am i able to install to my laptop's hard drive(now drive h on my desktop)? i am still wondering if this will work. i am presently formatting the hard drive which arises another question which may sound stupid but does ubuntu use ntfs?

---

### Post by t4thfavor on 2010-01-25
Another possible train of thought, is: Do you really want to trust any "Data" to a 10 year old Dell that has been exibiting signs of hardware failure?

I would probably recommend upgrading to something a few years newer in the $50-$100 range, there is plenty out there.



Also greetings to/from Michigan as well :)

---

### Post by dajasc on 2010-01-25
Ubuntu does not use ntfs.  It uses ext4 or ext3 usually.  

If you end up not getting the cd to boot and install you could do a network boot and install over pxe.  In my opinion that is a painful way to go but I've done it when I haven't had working drives and couldn't boot from usb.

---

### Post by onyxvu on 2010-01-26
There is really no recent hardware failure, the laptop was dropped before i bought it through ebay. Plus i really dont put any valuable data on it anyway, more really to surf the web in the upstairs of my house. i have a wireless network set up and its nice not to have to hang out in the basement where i have my desktop. well the format is done, we will see how this works...

---

### Post by mharrison on 2010-01-26
> **t4thfavor said:**
> 
Also greetings to/from Michigan as well :)


Yay, another person who hasn't run out of here like a bat of out you know where!

---

### Post by mharrison on 2010-01-26
> **onyxvu said:**
> in the boot from cd option am i able to install to my laptop's hard drive(now drive h on my desktop)? 

Are you trying to install Xubuntu to the laptop hard drive while it is connected to the Desktop?  This could cause some problems when you put it back in the laptop.  It is best to install it in the laptop.  If you don't have a working CD/DVD drive in the laptop, perhaps try to use the USB-IDE cord you are using on a CD/DVD Drive and hook it to the laptop to install.

---

### Post by onyxvu on 2010-01-26
cause problems? no... i spent my first hour this morning banging my head on my desk because the grub loader got installed on my desktop! so now that i got that fixed, the laptop wont boot. i ran xubuntu via my cd on my desktop and was able to see my laptop's hard drive and it appears everything was installed- accept grub i suppose. the laptop is too old to even boot from a usb. isn't there some way to run xubuntu on my desktop and drop some files into my laptop and make this work?

---

### Post by ushills on 2010-01-26
You can install it on your desktop, disconnect all drives except the laptop drive and install it connected to your desktop.  Then remove the drive and drop it back into the laptop, reboot and it will reconfigure based on your laptop settings.

This is the beauty of ubuntu you can use the drive in a new/different pc and it should just work provided the hardware is supported.

---

### Post by mharrison on 2010-01-26
You could also just do the install and right before you start, you can specify where to install the boot loader, and then specify the laptop hard drive.  But, like above, you can also disconnect all other hard drives and this will force the boot loader to install on the laptop hard drive MBR.

---

### Post by onyxvu on 2010-01-26
ok, so i'm making progress. I got everything straight with the desktop. The laptop will now boot however only into recovery. when i select normal boot the screen goes black and it will just sit and idle. i tried pressing "e" to see if there is something obvious but i have no idea what i'm looking at. what is supposed to be there? is the a command i can type in recovery to fix this or at least diagnose it? you guys have been a really invaluable source of info and i really appreciate it.

---

### Post by ushills on 2010-01-26
Does the laptop drive boot okay in your desktop, if so you may need to reconfigure your display (I will advise in next post).

If it does boot okay in your desktop when booting your laptop do you get an error if you hold ctrl>alt + F1 while booting.  Can you log in from this screen.

---

### Post by ushills on 2010-01-26
The command for reconfiguring your display if you can log in to a console from the boot menu is

```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by onyxvu on 2010-01-26
i was not able to configure the desktop to boot from the laptop's hard drive- it may not be able to, it is also about 10 yrs old. i tried ctrl+alt+f1 but all i get is a millisecond flash and then a black screen with a flashing cursor in the upper left. i tried changing the video settings but there is only system or dock card- it was set to system. i can log in from the ubuntu version of "command prompt" in recovery mode but i don't know what to do from there...

---

### Post by onyxvu on 2010-01-26
oh ok, i will try. does that auto configure or is there something else i will need to type. thank you for "holding my hand" here. i have never been good with command prompt either.

---

### Post by ushills on 2010-01-26
It sounds like an issue with X, if you managed to install correctly then the fact that the drive is a laptop drive is irrelevant.  I am concerned that you cannot boot into ubuntu even when connected to the desktop.  This would seem to imply that the install did not go well (I assume that you install the desktop version not the server version).

If however you can log into a recovery console what happens when you enter.

```
startx
```

---

### Post by ushills on 2010-01-26
9.10 comes with grub2 as default, there is a help section with advice what to do in a recovery console, you will have a grub-recovery> prompt.

[https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode]("https://help.ubuntu.com/community/Grub2#Command Line & Rescue Mode")

---

### Post by onyxvu on 2010-01-26
that loads me a gui! it seems a little lack function though. is this like a recovery gui? i was running xubuntu before this whole mess...

---

### Post by ushills on 2010-01-26
> **onyxvu said:**
> that loads me a gui! it seems a little lack function though. is this like a recovery gui? i was running xubuntu before this whole mess...


If you have managed to start the x server then it would appear that you have an installed system but an incorrect grub2 setup.

Can you post a snapshot of your gui so that we understand what you mean by lacking in function.  It may be that the display resolution etc require setting.

From memory xubuntu is a littel sparse anyway, can you access application, places etc.

---

### Post by onyxvu on 2010-01-26
is there some kind of trick to fixing it? i have been trying to read the link you gave me but its slow going. i am comparing what i see now to what i had when i downloaded it with wubi. all the menus seem to be present and accounted for- i guess i just need to figure out this boot issue...

---

### Post by ushills on 2010-01-26
You could try 

```
sudo update-grub
```
or 

```
sudo dpkg-reconfigure grub-pc
```

that may fix it if not you will need to read the section of the link

---

### Post by ushills on 2010-01-26
```
dpkg-reconfigure grub-pc
```

This should work, it may be that your drive references changed when you moved between machines.

```
fdisk -l
```

will tell you what the correct drive referenc should be i.e. /dev/sda

---

### Post by onyxvu on 2010-01-26
when i run this command: sudo dpkg-reconfigure grub-pc, i am getting a blue screen labeled "package configuration". i can't seem to find any information on what i need to enter here. any ideas?

---

### Post by ushills on 2010-01-26
if you 
```
sudo fdisk -l
```

it will give you the reference for your drive.

then with

```
sudo dpkg-reconfigure grub-pc
```

Select the disk that has your boot partition as the disk to boot from. Then change the boot order in your bios to boot from that drive.

This should work, however, i don't use grub2 so i am going from guides.

---

### Post by onyxvu on 2010-01-26
im still getting no where, every other restart stalls out, and i cant get it to load by itself. i have to go into recovery and use "startx". i really feel like i'm spinning my wheels. i am trying to read these instructions, but to me they are not very user friendly...:(
 
edit- scratch that, now all of a sudden it works fine. i believe it was installing startup manager. i didnt change anything just looked at the settings. my only issue now is that i get a message that flashes that says something like "vga 759 is depreciated".

---

