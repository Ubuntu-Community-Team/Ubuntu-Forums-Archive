---
title: "Now Grub Rescue is just being obnoxious."
date: 2011-09-25
forum: General Help
---

### Post by Lluminari on 2011-09-25
Had Ubuntu. Formatted the drive it was on. Built a new computer from scratch. Installed Windows. Grub Rescue crashes my computer constantly. Why does it exist? How is this possible? I want to get rid of it. 
Do I have to install Ubuntu and uninstall it properly? 
Keep in mind: Fresh system. Brand new Win7 install. 
No, I do not want to use Ubuntu again. I want to get rid of everything about it on my system.
Yes, I tried Repair from my dvd. Yes, I even reinstalled Windows, to no avail.
All I want is to be rid of this issue forever. Get back to my work without fear of GR crashing my computer again.

---

### Post by An Sanct on 2011-09-25
Welcome to the forums!

If you formatted the drive, then no grub rescue or anything else should have stayed behind.

---

### Post by Lluminari on 2011-09-25
You would think so. 
But it is there. 
I'm not posting in this forum to amuse myself. 
I'm here for legitimate help.

---

### Post by Blasphemist on 2011-09-25
Grub isn't crashing anything. Somehow you didn't get windows bootloader installed apparently and the mbr was not formatted. If you are getting the grub rescue prompt when booting, and need to install the windows boot loader, this should help you. 
> 1. Turn on your computer, insert the Windows 7 installation disc or USB flash drive, and then turn off your computer.

2. Restart your computer.

3. Press any key when prompted to do so, and then follow any instructions that appear.

4. When the Install Windows page appears, click Install now to begin the installation process or click Repair your computer to access system recovery options.

5. Follow the instructions.

---

### Post by Lluminari on 2011-09-25
When my computer restarts from the BSOD, my main drive disappears and the drive that used to have Ubuntu on it takes over. Again prompting the grub rescue. 
It even changes how the BIOS acts, making the latter drive the main boot option as well. 
Even when said drive is unplugged, my computer runs without a hitch. But, seeing as I need the space, I had to use it again. 
My main drive being only 100GB SDS to only have windows installed on it. The secondary drive is to install programs. 
The drive has been completely wiped. I even used CCleaner's drive wipe utility and made 50 passes. 
So you can tell, I'm very confused as to why this is happening and have taken steps to try and remove it properly.
What I need is a way that removes it, the Ubuntu way. Obviously the steps I have taken in trying the Windows way hasn't worked. 
Is there a program that works with Windows to get in there, fix the MBR and remove this issue?

---

### Post by Blasphemist on 2011-09-25
I guess I'm not explaining this well. The only remnant that I can tell that you have in play from ubuntu is that grub is still written to the mbr of the drive in question. Nothing from grub nor ubuntu is changing what your bios does. Your bios is booting from the drive in question first when it is installed and without a working boot loader installed, you get the grub rescue prompt. Grub is not a working boot loader because on the small part of it that resides in the mbr is still in place so it does as its designed.

Ideally, since windows will be your only OS, you'd have that drive set to be the boot device in bios and use the other drive as additional storage for that OS. That would be your best solution. My previous post describes how to use the windows installation disk to write a windows boot loader to the disk that you are having trouble with but I think that leaves you a bad boot process as bios is handing the boot process to a disk you have other plans for and doesn't house the OS.

---

### Post by An Sanct on 2011-09-26
Okay, to get things straight ...

Ubuntu is not "*stealing*" your computer, so do not panic. There is no need to wipe anything.

You built a new computer, so you want a fresh windows install.

Insert the windows media (USB/CD/DVD) and boot from it, select install and select "custom install"

A good start is to read this [info (Microsoft)]("http://windows.microsoft.com/en-US/windows7/Installing-and-reinstalling-Windows-7"), click on the "Using the Custom installation option and formatting the hard disk"

> 
[LIST=1]
[*]             Turn on your computer so that Windows starts normally, insert the  Windows 7 installation disc or USB flash drive, and then shut down your computer.             
[*]             Restart your computer.
[*]             Press any key when prompted, and then follow the instructions that appear.
[*]             On the                  Install Windows page, enter your language and other preferences, and then click Next.             
                                If the                      Install Windows  page doesn't appear, and you're not asked to press any key, you might  need to change some system settings. To learn how to do this, see [Start your computer from a Windows 7 installation disc or USB flash drive]("http://windows.microsoft.com/en-US/windows7/Start-your-computer-from-a-Windows-7-installation-disc-or-USB-flash-drive").                 
[*]             On the Please read the license terms page, if you accept the license terms, click I accept the license terms, and then click Next.             
[*]             On the Which type of installation do you want? page, click Custom.             
[*]             On the                  Where do you want to install Windows?                page, click Drive options (advanced).
[*]             Click the partition that you want to change, click the formatting option you want to perform, and then follow the instructions.
[*]             When you've finished formatting, click Next.             
[*]             Follow the instructions to finish installing Windows 7, which include naming your computer and setting up an initial user account.
[/LIST]


---

### Post by halibaitor on 2011-09-26
When formatting the HD, first delete _all_ partitions.  Then create _one_ partition for the entire disk.  Then do a low level format. (quick format won't do it)

That should give you a brand-new drive to install windoze on.  :D

Your previous format and wiping operations only did the main partition.

---

### Post by An Sanct on 2011-09-26
> **halibaitor said:**
> Then do a low level format. (quick format won't do it)...
Your previous format and wiping operations only did the main partition.

Low level is missleading - it should be "normal" format. ("low level" used to be format from within BIOS ... obsoleted)

Besides, if you delete all the partitions, GRUB will vanish. also a normal Windows install will kill GRUB - even if you wanted it to stay.

---

### Post by Lluminari on 2011-10-03
Nope, nothing. I even moved all my data unto an external hard drive, wiped the hard drive 33 times, reinstalled Windows, using a normal format. 
Grub takes over again.
Even did the repair, memory test etc...
A few times it would just make my C drive disappear altogether.
Keep in mind, both drives were completely wiped. There is no way for this thing to exist. 
Would reinstalling Ubuntu on said drive and doing a proper uninstall work? Can this be done?
I've even went over my hardware, installing one thing at a time. Sure enough, as soon as I install my 500GB HDD, that's when grub takes over. 
It's a persistent problem. And weird.

---

### Post by Blasphemist on 2011-10-03
From your description, you have not wiped grubs initial program loader from the MBR of your 500 GB drive. This is written to the very first sectors of that hard drive. Whatever you are using to wipe the drives must need to be directed to wipe the mbr.

---

### Post by Mr.Enigma on 2011-10-04
trying to wrap my head around this.  I understand your problem like this:

You have two seperate **physical** hard drives. (not 2 partitions on 1 drive)
Disk 1 has windows
Disk 2 has been reformatted and used to contain ubuntu

Disk 1 connected, disk 2 disconnected: boots fine
Disk 1+ 2 connected : grub rescue shows up.

Am I right?
If so:

Edit your Bios setting so that disk 1 is the primary drive
OR
Swap the SATA cables connecting the two drives like this
D1>SATA1
D2>SATA2
becomes
D1>SATA2
D2>SATA1

Hope this helps.

---

### Post by Lluminari on 2011-10-07
I do enter the BIOS settings and try to change it, but my secondary drive, the slave, changes settings to make it the primary drive in my BIOS. Every time. I can change it as many times as I want, but Ubuntu changes it back. It's like having a ghost in my machine, changing my settings and shutting my machine down.

---

### Post by Lluminari on 2011-10-07
Would you know how to do this? Is there a program out there that wipes the drive of anything on there? Reverting it back to the day I bought it? I'll do a search myself as well. 
I would agree the program loader remains untouched no matter how many times I do it.

---

### Post by Lluminari on 2011-10-07
Thanks, forum. For being patient. 
I know this seems unique, but I do hope the solution for this helps you help someone else down the road. 
Thanks again.

---

