---
title: "ubuntu+windows = dual booting"
date: 2009-07-17
forum: General Help
---

### Post by matt12345 on 2009-07-17
Alright so I have finally decided I would like to dual boot ubuntu with windows. Problem is I have really no idea what I am doing. I have a CD with a custom version of Windows XP that suits what I want. So I was wondering how would I dual boot, and how would I chose what operating system I would want. Ex: I would use ubuntu for work, and windows for gaming, so how would I be able to choose between the two.

---

### Post by Marlonsm on 2009-07-17
Put the Ubuntu CD in the computer and reboot.
It'll boot into Ubuntu, and there you'll have the option to partition your HD (divide it in two parts, one for Windows, and one for Ubuntu).
After installing, when you turn your computer on, you'll have the option to choose which OS do you want to use.

---

### Post by merlinus on 2009-07-17
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by matt12345 on 2009-07-17
> **Marlonsm said:**
> Put the Ubuntu CD in the computer and reboot.
It'll boot into Ubuntu, and there you'll have the option to partition your HD (divide it in two parts, one for Windows, and one for Ubuntu).
After installing, when you turn your computer on, you'll have the option to choose which OS do you want to use.

I'm already booting from Ubuntu 9.04.

And I read the guide, doesn't really seem to be helping me.

---

### Post by ~sHyLoCk~ on 2009-07-17
> **matt12345 said:**
> I'm already botting from Ubuntu 9.04.

And I read the guide, doesn't really seem to be helping me.

Install Ubuntu on a separate partition and it will automatically detect your windows install and add it to the boot menu.

---

### Post by merlinus on 2009-07-17
Since you already installed linux, this may help:

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by matt12345 on 2009-07-17
Altight, I'm on the 3rd step. But I'm lost when it says "Restart the system using the Ubuntu Live CD" whats the ubuntu live CD?

---

### Post by ~sHyLoCk~ on 2009-07-17
> **matt12345 said:**
> Altight, I'm on the 3rd step. But I'm lost when it says "Restart the system using the Ubuntu Live CD" whats the ubuntu live CD?

The CD you used to install Ubuntu.

---

### Post by merlinus on 2009-07-17
The cd you used to install ubuntu, if indeed you did it that way.

My guess is this is to reinstall grub, which is overwritten when installing windows after linux.

---

### Post by matt12345 on 2009-07-17
Well it tells me to go to  System, Administration, Partition Editor. But I cannot find the Partition editor :(

---

### Post by lisati on 2009-07-17
> **matt12345 said:**
> Well it tells me to go to  System, Administration, Partition Editor. But I cannot find the Partition editor :(

Which version of Ubuntu is on your disk? I think on some older versions the partition editor has a different name.

---

### Post by merlinus on 2009-07-17
If you were running from the live cd, it would be there.  Perhaps it is called gparted, or gnome partition editor.

In any event, if running ubuntu you can easily install it.

```
sudo apt-get install gparted
```

---

### Post by matt12345 on 2009-07-18
When it's saying "Right-click on the main data partition which has been formatted with ext3 - it should be /dev/sda1 - and select "Resize/Move" 

It's not letting me click on :(

Anyone mind helping me?

---

### Post by lisati on 2009-07-18
> **matt12345 said:**
> When it's saying "Right-click on the main data partition which has been formatted with ext3 - it should be /dev/sda1 - and select "Resize/Move" 

It's not letting me click on :(

Anyone mind helping me?

You might need to click on "unmount" first.

---

### Post by matt12345 on 2009-07-18
Alright tried that and I got,

```
Could not unmount /dev/sda1

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually.
```

---

### Post by lisati on 2009-07-18
Are you running from an installed copy of Ubuntu or from the Live CD?

---

### Post by matt12345 on 2009-07-18
well to be honest with you, I'm not entirely  sure. I mean I click on Ubuntu 8.10 i386 and it comes up with:

Demo and Full installation 

Install inside Windows
and
Learn More

When ever I click on one, it comes up with a bunch of screens saying extracting.

---

### Post by ~sHyLoCk~ on 2009-07-18
> **matt12345 said:**
> well to be honest with you, I'm not entirely  sure. I mean I click on Ubuntu 8.10 i386 and it comes up with:

Demo and Full installation 

Install inside Windows
and
Learn More

When ever I click on one, it comes up with a bunch of screens saying extracting.

Put the CD inside. Restart your computer. Boot from the CD and follow the step by step procedure. This is a much simpler and better way.

---

### Post by lisati on 2009-07-18
> **matt12345 said:**
> well to be honest with you, I'm not entirely  sure. I mean I click on Ubuntu 8.10 i386 and it comes up with:

Demo and Full installation 

Install inside Windows
and
Learn More

When ever I click on one, it comes up with a bunch of screens saying extracting.

It almost sounds like you've got Windows running with the Ubuntu CD in the CD drive, which will help explain why you couldn't find the partition editor. As shylock suggests, you need to put the CD in, and restart your computer. Then choose "Try Ubuntu without installing", wait for Ubuntu to load, and you should be able to find the partition editor on the system->administration menu.

---

### Post by matt12345 on 2009-07-18
I've already restarted my computer about 4 times now, and nothing has come up :\

---

### Post by ~sHyLoCk~ on 2009-07-18
> **matt12345 said:**
> I've already restarted my computer about 4 times now, and nothing has come up :\

Goto BIOS and check if Boot preference has CD/DVD drive as 1st preference, before HDD and then boot from the LIVE CD.

---

### Post by OooBuntuRox on 2009-07-20
> **~sHyLoCk~ said:**
> Goto BIOS and check if Boot preference has CD/DVD drive as 1st preference, before HDD and then boot from the LIVE CD.
 
 
Hello sHyLoCk/ Anyone,
 
Do you have any clues for installing windows on a fresh drive? I have some older (virgin XP disks, non-dell, just generic full version). Can't even get xp to load. It goes through the initial install, then hangs with errors when xp reboots to beging the hardware configuration process. Are there some proprietary install tricks? I noticed about 16 xp drivers for download. But what use are they if xp must be installed first?
 
By the way, using the same drive, 9.04 goes in without a hitch! So how do you get windows installed first for a dual boot system?
 
Thanks, OooBuntuRox :guitar:

---

