---
title: "Can A Portable Hard Drive Be A Computer?"
date: 2010-10-27
forum: General Help
---

### Post by Smallwheels on 2010-10-27
I don't know a lot about technical stuff. Someone here can probably answer my questions. Can I buy a portable USB powered hard drive and have that act as my computer? If I put a variant of Linux on it, wouldn't I be able to connect it to any of my friends computers or even work computers and have my own personal setup? 

Since computers are so different would there always be a problem with drivers for video, keyboards, mice, printers, and monitors?

Having a computer in my pocket that could connect to any hardware seems like a good idea. I believe that computers on tiny flash cards will be the future of computing. We'll all just connect our computers to hardware kiosks or computers provided in hotel rooms. I just wonder if doing that now is possible.

I'm ready to start doing it with my HP and Apple computers.

---

### Post by Megaptera on 2010-10-27
Have a look at PenDriveLinux. I have a copy of Ubuntu 10.04 on a 2gb USB stick ...

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by WorMzy on 2010-10-27
Ubuntu doesn't rely on specific hardware being present, which means that you can install Ubuntu on your portable hard drive and use it on any compatible computer. The only thing that you're limited by is the processor -- for instance, you can't use a 64-bit installation of Ubuntu on a computer that has an Pentium III processor.

---

### Post by dcstar on 2010-10-27
> **Megaptera said:**
> Have a look at PenDriveLinux. I have a copy of Ubuntu 10.04 on a 2gb USB stick ...

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Why use other methods when Ubuntu has built-in tools to simply create Live USB boot systems?

The answer to the OP is yes - simply use a 386 Ubuntu ISO to create a Live USB (System-Administration-Startup Disk Creator) and you can use it on virtually any Intel based hardware that boots from USB drives.

---

### Post by ironic.demise on 2010-10-27
Though, There might be a problem with boot orders.
For example, if he were to do it on MY machine, it would only work if he first went into my (password protected) BIOS and set his hard-drive to boot before my own.
 
By the way, external hdd are (usually sata) just a disk drive in a case that has a "to-usb" adaptor, I pryed open my external and just put the hard-drive in my PC to act like an internal.
 
This means that essentially you get the same effect as if you installed Ubuntu on an internal hard-drive, then put that into a friends machine.

---

### Post by dcstar on 2010-10-27
The OP wants a system that can be used on multiple **different** hardware platforms, a normal Ubuntu install is configured for **one** specific hardware platform.

The Live USB is specifically designed to be used with **any** hardware platform as it has code to probe for different hardware on loading.

---

### Post by ironic.demise on 2010-10-27
> **dcstar said:**
> The OP wants a system that can be used on multiple **different** hardware platforms, a normal Ubuntu install is configured for **one** specific hardware platform.

The Live USB is specifically designed to be used with **any** hardware platform as it has code to probe for different hardware on loading.

So what he wants... essentially is a *persistent live usb*
... To be totally you could set-up a live usb on a hard-drive, considering BIOS just see USB storage as a harddrive anyway.

and on a persistent USB your docs and files will stay.

---

### Post by coldraven on 2010-10-27
I have only tried this with a memory stick but I guess that it would work with a USB drive as well.
If you have a stick give it a try, it is very easy. I think you would need at least a 2GB stick for it to be useful.

Plug in your stick or drive.
Re-boot with a 32bit Ubuntu Live CD.  (Obviously, select the "Try Ubuntu" option)
Choose System -> Admin -> Startup Disk Creator.
Make sure that you select the correct drive!
Tick "Make Persistent" and select how much space you want for storing your files.
Done.

Then test by Re-booting, going into your BIOS setup and under "Boot Order" make USB the first entry.
Exit setup and your PC should boot from the stick.

What I'm unsure of  is this, my stick is formatted with FAT32 and I know that the largest file size on this medium is 4GB. If you want to copy files bigger than that you would have to format your drive with the NTFS file system before creating the Startup disk.
This is a breeze to do with Gparted.
The reason for the choice of NTFS is that if your friends PC cannot boot from USB then it will at least be able to copy files on to your drive. Well Windows anyway, I'm not sure about Macs.
I'm sure that someone will tell you if this works or not.

---

### Post by Smallwheels on 2010-10-27
I have a powered external hard drive that came set up to work with Macs. I bought a program called MacDrive 7 for my Windows computer. Somehow it made it possible to read the files and store files to the drive. 

I noticed that when I dual booted the Vista computer with Ubuntu that Ubuntu could access all of the files on the external drive too, even without the MacDrive 7 program. I just assumed that Linux can read the Mac file format.

I know that originally my HP computer would automatically boot Vista before Ubuntu was added. Now a black screen opens up and I have several choices of Vista, Ubuntu, and their repair files or something like that. When Vista needed repair I had to click F9 repeatedly to get to the black screen to allow me to select a choice for repairing it. If I attached a Linux hard drive via USB and then restarted a computer while pressing F9 wouldn't the choice for the drive show up? I don't know what I should press to get a Mac to recognize the drive and boot from it even though I own a Mac Book.

---

### Post by Megaptera on 2010-10-27
> **dcstar said:**
> Why use other methods when Ubuntu has built-in tools to simply create Live USB boot systems?

Should clarify, I used Ubuntu's own system. I was pointing out the site to show the o/p other options.
                                   :)

---

### Post by Smallwheels on 2010-10-28
Anybody have a response to my above post? This one:[COLOR=DarkOliveGreen] [COLOR=Indigo]I have a powered external hard drive that came set up to work with Macs.  I bought a program called MacDrive 7 for my Windows computer. Somehow  it made it possible to read the files and store files to the drive. 

I noticed that when I dual booted the Vista computer with Ubuntu that  Ubuntu could access all of the files on the external drive too, even  without the MacDrive 7 program. I just assumed that Linux can read the  Mac file format.[/COLOR][/COLOR] [COLOR=Indigo]

I know that originally my HP computer would automatically boot Vista  before Ubuntu was added. Now a black screen opens up and I have several  choices of Vista, Ubuntu, and their repair files or something like that.  When Vista needed repair I had to click F9 repeatedly to get to the  black screen to allow me to select a choice for repairing it. If I  attached a Linux hard drive via USB and then restarted a computer while  pressing F9 wouldn't the choice for the drive show up? I don't know what  I should press to get a Mac to recognize the drive and boot from it  even though I own a Mac Book.[/COLOR]

---

