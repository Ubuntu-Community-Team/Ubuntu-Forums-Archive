---
title: "Any reason to not run from a USB only?"
date: 2010-09-07
forum: General Help
---

### Post by jaccav on 2010-09-07
I've been running Ubuntu from a USB stick with persistent data. I've been really pleased with it, and have run it on three different computers in my home with no issues at all.  I've tried running Ubuntu many times in the past, and have had problems. I'm running Lucid Lynx, and it has come so far in terms of compatibility and plug and play ability. It really is great.

For several different reasons, I'd rather not do a full install onto the hard drive.  

Is there any reason, other than the size of the persistent file, that I should be concerned about running Ubuntu in this manner? 

Thanks for your help!

---

### Post by krimzonstarr on 2010-09-07
The only reasons that I can think of off the top of my head are: 1. Speed 2. Maintaining system upgrades/Custom packages (Which persistance should help but not fully overcome) 3. Wear and tear on the USB drive, shortening it's life significantly.

---

### Post by sgosnell on 2010-09-07
The liveCD with persistent data isn't really designed for everyday use.  I recommend doing a full install to the USB drive.  That will give you better performance and more security.  There is no reason you can't run regularly from that.  I use an SD card in a couple of laptops, and that works pretty well for me.  I don't like the USB drives as much because they stick out the side, but for a desktop machine it may not be an issue.

I don't worry about 'wearing out' a USB drive, because they cost so little, by the time one wears out a bigger one will be cheaper anyway.  They're disposable.

---

### Post by jaccav on 2010-09-07
Thank you.

I've found speed not to be an issue at all. It does seem to perform updates, unless I'm missing something, which I probably am. I guess I can always run newer releases from a USB stick as well if I need to. I also get that I'll be shortening the life of the USB stick, but I'll take that trade off for the much faster startup and shutdown times and the ability to take my entire system with me wherever I go and use it on pretty much any machine I encounter.

Anyone else?  I just want to make sure I'm not missing something important.

---

### Post by C.S.Cameron on 2010-09-07
Persistence size is only limited to the size of the flash media if you use a persistent partition, (ext2, labled casper-rw) rather than the casper-rw file usb-creator makes.

Flash drives are generally good for 10000 writes, a 4GB drive should last a year writing 8 hours per day.


I prefer a full install to flash drive myself so that it is easy to update/upgrade. This also allows using a password which is probably a good idea with something so easy to loose.

Edit:
Oops, I see that with 10.04 you can add a new user and require a password at login. This seems to vary with releases.

---

### Post by cj.surrusco on 2010-09-07
+1 for the full install on a USB stick. It would just seem to make more sense to me. It wouldn't use that much space, and loading times would be faster. I actually read something about a guy that set up a RAID 0 install with two USB sticks to improve transfer speed. I don't know if you would want to try *that*, but it might be something fun to do.

---

### Post by HermanAB on 2010-09-07
There is no problem with it except maybe speed.  I've been running an EeePC 701 for years with the internal 4GB flash disk for / and /boot and a 16GB SD card for everything else.  It works fine.  In fact, I'm posting this from my ancient Eeep!

Hard disks are sooo 20th century...
;)

---

### Post by dcstar on 2010-09-08
The SquashFS file system used by the Live USB does not reuse deleted file space, this means your Persistent space will eventually run out with every file change you make - even if you delete files.

Try installing the UNR on the USB and you will get a fully functional Ubuntu system on the removable device (I don't know if you can actually do this).

---

### Post by 3rdalbum on 2010-09-08
I ran my server from a USB flash drive. Then I started getting read/write errors, causing the filesystem to go read-only. It kept happening and eventually the filesystem didn't last five minutes without going read-only due to errors.

I got sick of this and put in a hard disk, which is still going strong. The flash drive was busted so badly that I couldn't even format it.

This wasn't just some el-cheapo flash drive either - it was made by a well-known memory brand that also makes power supplies and has just started releasing high-end cases.

You might be okay and maybe this flash drive was a bad one - but I'd recommend NOT trusting your data to the fate of a couple of memory cells that were never intended for running an operating system.

---

### Post by HermanAB on 2010-09-08
Hmm, my condolences with your bad flash drive.  These things can be very reliable and are used in many military applications - solid state flight recorders for example, since about 1985.  

So, you just had a baaad one...

---

### Post by C.S.Cameron on 2010-09-08
> **3rdalbum said:**
> I ran my server from a USB flash drive. Then I started getting read/write errors, causing the filesystem to go read-only. It kept happening and eventually the filesystem didn't last five minutes without going read-only due to errors.

I got sick of this and put in a hard disk, which is still going strong. The flash drive was busted so badly that I couldn't even format it.

This wasn't just some el-cheapo flash drive either - it was made by a well-known memory brand that also makes power supplies and has just started releasing high-end cases.

You might be okay and maybe this flash drive was a bad one - but I'd recommend NOT trusting your data to the fate of a couple of memory cells that were never intended for running an operating system.

You are the first person that I have heard from that has lost a flash drive from running Ubuntu.
Years ago when Kingston first released 4GB drives I bought one and did a full install of Ubuntu. It still works fine.
Are you sure it is not just a faulty drive? What sort of guarantee does it have? If not el-cheapo it should be lifetime.

---

### Post by cheetos316 on 2010-09-08
Don't mean to hijack this thread but I'm currently doing the LiveCD with Persistent data on a microSD card.  What is the difference between the LiveCD and installing to card?  

I'm in the camp that I really like being able to carry my tiny microSD card and tiny reader everywhere and know that I can load Ubuntu and be secure.  It's too bad that only newer computers are able to boot from USB though...

---

### Post by C.S.Cameron on 2010-09-08
> **cheetos316 said:**
> Don't mean to hijack this thread but I'm currently doing the LiveCD with Persistent data on a microSD card.  What is the difference between the LiveCD and installing to card?  

I'm in the camp that I really like being able to carry my tiny microSD card and tiny reader everywhere and know that I can load Ubuntu and be secure.  It's too bad that only newer computers are able to boot from USB though...

Live USB is faster than Live CD. More computers boot from CD than USB card.

---

### Post by sgosnell on 2010-09-08
The difference is that the LiveCD/LiveUSB is just an installer, while a full install is the same whether to a HDD or a flash drive.  As noted above, you'll run out of space on a persistent liveUSB eventually, even if you delete files.  On a full install, you can delete files and recover the space, as well as update the OS, and everything else.  You get a drive with the full OS, which you can use on any computer.  You use the LiveUSB drive to install to another flash drive, just as you would to a HDD.  A full install requires two flash drives, one for the liveUSB, and one to take the installed OS.  The LiveUSB only needs to be 1GB, while you need 8, or better, 16, for a full install.  I usually format a 16GB flash drives to two partitions, one about 6GB for /, and the other using the rest of the drive for /home.  That way I can reinstall the OS, upgrade, or whatever else I want without touching the /home partition, which holds my data and much of the configuration.

---

### Post by jaccav on 2010-09-10
If I'm reading that correctly, I can do a full install onto a flash drive?

That may make more sense than running Live USB with persistence. I tried using it last night, and my Casper-rw folder doesn't seem to want to mount any more. There's no way I filled that USB up in a few days.

---

### Post by C.S.Cameron on 2010-09-10
Full Install:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu 10.04.
Fill in "Time Zone" and "Keyboard layout".
At "Prepare disk space" select "Specify partitions manually (advanced)".
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
Click "Forward".
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Select forward.
Select Install.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you select the "Advanced" button and choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your hard drive, even when booting another computer.

---

### Post by sgosnell on 2010-09-10
You can do a full install to any drive, of any type.  Ubuntu is not Windows, and doesn't have its limitations.  Just boot the liveCD (or liveUSB), run the installer, and select your USB drive as the target.  It works exactly the same as installing to the internal HDD, you just choose the drive you want.  Before clicking the final Install button, make sure you click the Advanced button, and have it put the bootloader on the USB drive, NOT on sda1.

---

### Post by cj.surrusco on 2010-09-10
I was able to install to a flash drive the same way that I did with hard drives. In fact, I set up two flash drives in RAID 0, and it has significantly increased read/write speed, and even better access times too.  

After some benchmarks, the read speed for each flash drive individually was about 25 MB/s, and the read speed of the RAID 0 array was 40 MB/s. That's enough to almost double the boot speed, plus applications load faster. 

Of course, the flash drives aren't yet a replacement for my 5 hard disk RAID 5 array, which has read speeds of about 150 MB/s, but it is definitely a good alternative for when a hard drive installations isn't available.

---

