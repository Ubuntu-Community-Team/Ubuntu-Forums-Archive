---
title: "Help installing Linux as the ONLY OS"
date: 2009-10-15
forum: General Help
---

### Post by jarame on 2009-10-15
Hello All! I just want to start by introducing myself: I will go by Jarame on these forums and I am 18 years of age, so I am very computer savvy, and I do live in the U.S.

**My issue:** After 5 years of owning it I recently upgraded my Toshiba Satellite A100/A105 Series laptop that ran Windows XP to Windows Vista Home Basic. Well, down the road my CD Drive broke (the part that clips down the CD has broken off from using it so much) and now I cannot use my restore disc to format my harddrive and revert to XP. I searched the web And ran across an article that said Vista Home Basic cannot be downgraded, I confirmed this by using an ISO burner to make an image file (.iso file) of my restore disc and tried running it, which I then got this message: "Cannot determine current OS version." So then I nabbed Ubuntu 9.04 "Gnome" and partitioned my drive and tested it. I must say that Linux is a hell of a lot faster than Windows will ever be, and so I plan on using Linux as my main OS on this sh***y laptop that I own.

**My question:** Is there a way of replacing Windows Vista with Linux? I don't want to partition my drive or anything. I just want to use Linux and no other OS. Is this possible?

Thanks for any answers and help that I receive!

---

### Post by P4man on 2009-10-15
ahm.. yes, of course?

Im not sure what you're asking exactly (do you want to recover files or settings from windows or what?), but if you install ubuntu and tell the installation wizard to use the entire drive, vista/xp/whatever will be gone from your drive forever.

Oh wait, perhaps you did a wubi install the first time, and hence you're unsure. The "normal" way to install ubuntu is booting from the live CD (which can be a USB stick as well). Then you'll have the option to partition the drive, set a dual boot, or a simple "ubuntu' only option.

---

### Post by wojox on 2009-10-15
You need something like this: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by |Mitch| on 2009-10-15
If you're able to boot from the livecd, when you get to the reformatting/partitioning part of the installation. Do yourself a favor and set your partitions up like this:

10-20 gigs for your / as primary
swap should be double the amount of ram
the rest of the hard-drive as /home logical

That way if you ever have to reinstall Ubuntu, you will not lose your personal files, music, pictures, etc...
All you'll have to do is format the / partition and reinstall...

Just some friendly advice, in case you accidently break Ubuntu. Harder to do than Windows, but still can be done.

---

### Post by jarame on 2009-10-15
I'm tired of Vista. I want to remove Windows COMPLETELY from my laptop and only be left with Linux. I downloaded PowerISO from doing a google search and grabbed Ubuntu 9.04.iso from doing another google search. Right now I'm partitioning my drive again but giving Ubuntu a larger portion of my harddrive.

If I weren't doing this partioning at the moment I would gladly show you a screenshot of the prompt I'm given to install Ubuntu. I will most definitely supply one ASAP. But that link that Wojox posted, the program described there...will that replace Windows with Linux?

---

### Post by P4man on 2009-10-15
> **jarame said:**
> I'm tired of Vista. I want to remove Windows COMPLETELY from my laptop and only be left with Linux. I downloaded PowerISO from doing a google search and grabbed Ubuntu 9.04.iso from doing another google search. Right now I'm partitioning my drive again but giving Ubuntu a larger portion of my harddrive.

If I weren't doing this partioning at the moment I would gladly show you a screenshot of the prompt I'm given to install Ubuntu. I will most definitely supply one ASAP. But that link that Wojox posted, the program described there...will that replace Windows with Linux?

No, its just to make the bootable cd or stick.

If you want to remove vista entirely, then you are doing it wrong though. Did you boot from the cd or did you just run the installer fro within windows ? To get rid of windows, you have to boot from an ubuntu cd or USB stick.

---

### Post by jarame on 2009-10-15
> **P4man said:**
> No, its just to make the bootable cd or stick.

If you want to remove vista entirely, then you are doing it wrong though. Did you boot from the cd or did you just run the installer fro within windows ? To get rid of windows, you have to boot from an ubuntu cd or USB stick.

My CD Drive is broken, so that's a No Go. I could make a USB Stick no problem cause I have tons of USB Drives, but they're all 4 GBs...I don't know how big of a drive I'll need for it though. But if I used a USB Stick it would remove Windows completely?

---

### Post by P4man on 2009-10-15
> **jarame said:**
> My CD Drive is broken, so that's a No Go. I could make a USB Stick no problem cause I have tons of USB Drives, but they're all 4 GBs...I don't know how big of a drive I'll need for it though. But if I used a USB Stick it would remove Windows completely?

You'd need about 650Mb (so a 1 GB stick) if you downloaded the liveCD iso. 4GB might do it for the live DVD.

To make the live usb stick from within windows, use the unetbootin tool linked above. Then reboot the machine, set the bios to boot from USB, and install from there. Yes, that will rid you of windows entirely if tell it to use the entire drive.

---

### Post by jarame on 2009-10-15
> **P4man said:**
> You'd need about 650Mb (so a 1 GB stick) if you downloaded the liveCD iso. 4GB might do it for the live DVD.

To make the live usb stick from within windows, use the unetbootin tool linked above. Then reboot the machine, set the bios to boot from USB, and install from there. Yes, that will rid you of windows entirely if tell it to use the entire drive.


Wewt!! I will most definitely try this method first thing when I wake up! :D And I will share any success/failures with you all, lol. I'm hoping this will rid me of Windows forever, but if there's a problem I'll just post back on here.

Again, I thank you all very much! Happy Linux-ing...err :confused: ...Now to go make an avatar for this forum account xD

---

### Post by jarame on 2009-10-18
Okay guys we have a big problem:

I received a Windows Vista Registry error: Oxc000000d corrupt file or missing error and now Vista will not boot at all. Also when I tell the computer to boot from "Removable Devices" Nothing happens it just goes back to the OS options: Windows Vista or Ubuntu. Selecting Vista just gives me that error, selecting Ubuntu just boot Ubuntu 9.04 from the partition.

But I created an Ubuntu USB stick and it doesn't work when I try to boot from it. Is there something I'm doing wrong? Please help, I would like to wipe my computer clean and only leave Linux on it as the Main OS.

---

### Post by karimruan on 2009-10-18
This is how i did it. Restart with the ubuntu live cd in the cdrom drive. CHoose the install option. Go through all of the steps, and when you get to the partition manager, delete all partitions and make a new one. This could be ext3 or NTFS filesystem I believe. I choose ext3. Set the mount point to / and continue. THis will reformat your hard drive, and in the process erases all current data and replaces it with ubuntu.

Another (easier) way is to run the live cd to test out ubuntu, and go to system>administration>partition editor, and do the same. Reformat the hard drive to ext3, apply it, and then restart (with the live cd still in the drive). Then go on and install it.

---

### Post by karimruan on 2009-10-18
Make sure to edit the bios to allow booting from USB.

---

### Post by jarame on 2009-10-23
Well I got Windows XP put back on my computer and Ubuntu on a partition once again. I'm gonna order an internal replacement CD Drive for my current broken one, or just get an external drive so I can use it for all computers if anymore drives break. I'm not sure yet.

But once I get a working CD/DVD drive I'll do just that. Thanks :]

---

