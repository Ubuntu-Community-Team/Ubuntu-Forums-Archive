---
title: "How to run ubuntu with MsDos"
date: 2012-01-08
forum: General Help
---

### Post by tejli007 on 2012-01-08
Hi all.
Am trying to install windows in my pc but the problem is my cd drive is broken.
Is there any chance to run my pc with msdos so i can run the Setup.exe from windows?
I have installed Wine.
I use ubuntu 11.04
and am ubuntu noob. :)
thanks for the help

---

### Post by mikewhatever on 2012-01-08
As the name implies, this is an Ubuntu Help and Support forum. If you want help with MSdos or Windows, you are in the wrong place.

---

### Post by electrojustin on 2012-01-08
How would you run MsDos without a CD drive? If your CD drive is broken you won't be installing Windows (or any other operating system for that matter unless you have a bootable flash drive) anytime soon.

---

### Post by snowpine on 2012-01-08
If your CD drive is broken, you can install Ubuntu using a USB flash drive. Easy instructions on this page: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by mastablasta on 2012-01-08
> **electrojustin said:**
> How would you run MsDos without a CD drive? If your CD drive is broken you won't be installing Windows (or any other operating system for that matter unless you have a bootable flash drive) anytime soon.

maybe they could do it in virtual box, but i am not sure what is the purpose of this exercise. 


to the OP if you wish to install windows you need a CD drive. uneless you find a way to do it from USB.

ms dos can be installed with floppy.

if you need msdos emulator used to run a dos programme use dosbox.

---

### Post by Learning Linux 2011 on 2012-01-08
Why would you need MS DOS anyway?  DOS hasn't really been used by itself in over 15 years.
You don't need DOS to install anything anymore.

---

### Post by grahammechanical on 2012-01-08
If you have a floppy disk with MSDos on it and you set the BIOS to boot first from the floppy drive before looking at the CD drive or hard drive, then MSDos will load. What you do with it afterwards is anybody's guess.

I built my own machine about 4 Years ago. I put a blank hard disk in it. So, in order to see if the hardware was working I booted an old copy of MSDos that I had on a floppy disk. It worked. I then installed Ubuntu 7.04 to the hard disk. Mind you, I had a brand new DVD drive to use to install Ubuntu.

Regards.

---

### Post by tejli007 on 2012-01-08
> **Learning Linux 2011 said:**
> Why would you need MS DOS anyway?  DOS hasn't really been used by itself in over 15 years.
You don't need DOS to install anything anymore.

i use just ubuntu as OS.
must be a way to install windows again without cd or usb.
i have the iso and i have burned to disk, so i have all the files extracted to pc.

msdos: well like everyone the first Os was Windows and i have used msdos.
and from dos i can run the setup.exe.

have ubuntu something like dos? so i can run setup.exe?

and if you have any idea how can i run the setup.exe ur welcomed to share ur idea if not please dont writte this is not the right forum or u cant do that!

thanks.and sorry for my english

---

### Post by snowpine on 2012-01-08
You need to buy a legal Windows install CD and use a functional CD-ROM drive; that is really the only method we support here on UbuntuForums.

It's possible there are other websites on the Internet where you can find a less-than-legal solution to your question. ;)

---

### Post by tejli007 on 2012-01-08
> **snowpine said:**
> You need to buy a legal Windows install CD and use a functional CD-ROM drive; that is really the only method we support here on UbuntuForums.

It's possible there are other websites on the Internet where you can find a less-than-legal solution to your question. ;)

my windows i have copied to my pc.its orginal windows.dont worry about it.
 ok...
my pc is not stollen.
i use all the programs with licence.
i pay may taxes.
my wireless is legal...................

so please just tell me how can i fix my problem.

---

### Post by Mark Phelps on 2012-01-08
The only way you can run Windows .exe files is with Wine -- but you can't use Wine to install Windows.

As to your comment > please dont writte ... u cant do that! you need to face the facts ... as we've all been trying to tell you.

---

### Post by snowpine on 2012-01-08
> **tejli007 said:**
> so please just tell me how can i fix my problem.

Insert your official Windows CD into your functional CD-ROM and follow the instructions onscreen.

If you require additional assistance: [http://support.microsoft.com](http://support.microsoft.com)

---

### Post by restorator on 2012-01-08
After reading through this I could be wrong, but I think you are trying to install windows actually "inside" Ubuntu, but not as a virtual machine. You simply cannot do that, and no OS I know of has that ability unless you use a virtual machine system such as Virtualbox. Wine is not designed to do anything like that either. 
And neither is wubi. Wubi does not really install ubuntu inside the operating system inside windows, just the filesystem.

---

### Post by tejli007 on 2012-01-08
> **restorator said:**
> After reading through this I could be wrong, but I think you are trying to install windows actually "inside" Ubuntu, but not as a virtual machine. You simply cannot do that, and no OS I know of has that ability unless you use a virtual machine system such as Virtualbox. Wine is not designed to do anything like that either. 
And neither is wubi. Wubi does not really install ubuntu inside the operating system inside windows, just the filesystem.

thanks sir.

can any administrator confirms that?

---

### Post by Learning Linux 2011 on 2012-01-08
I think I might have a possible solution, but you would have to be using Windows XP or earlier I think. I don't think Windows Vista or Windows 7 supports this anymore, but I could be wrong.

You would have to create an MS DOS partition using linux, and make it FAT32, no bigger than 32 GB.
Then copy the i386 folder from your Windows disc/ISO file onto the new partition.

Then boot from a DOS floppy, switch to the i386 folder and run setup (although I think it is called winnt or winnt32 as I recall)

It might not work, but it is worth a shot.

---

### Post by BertN45 on 2012-01-08
> **Learning Linux 2011 said:**
> I think I might have a possible solution, but you would have to be using Windows XP or earlier I think. I don't think Windows Vista or Windows 7 supports this anymore, but I could be wrong.

You would have to create an MS DOS partition using linux, and make it FAT32, no bigger than 32 GB.
Then copy the i386 folder from your Windows disc/ISO file onto the new partition.

Then boot from a DOS floppy, switch to the i386 folder and run setup (although I think it is called winnt or winnt32 as I recall)

It might not work, but it is worth a shot.

I have done it in the past. It worked, but I copied the whole content (all files and folders) of the CD and not only the i386 folder. Sometimes I could use setup and sometimes I had to use winnt. It should work also with VISTA and WIN7, since it is basically like a network install. I think that is why you had to use WINNT.

---

### Post by lisati on 2012-01-08
If you want to run MS-DOS programs, and not Windows programs, you might want to check out DOSEMU/DOSBox.

Have a look here: [https://help.ubuntu.com/community/DOSBox](https://help.ubuntu.com/community/DOSBox)

---

### Post by Rugikara on 2012-01-08
I think the easiest way would be to Virtual Box and just download an CD ISO image of the internet, put it onto a USB and then create the new OS.

---

### Post by electrojustin on 2012-01-08
Assuming you have an ISO, your only solution to installing windows on an Ubuntu computer without a working CD/DVD drive is to run it in a virtual machine. No need to run setup.exe as ISOs pretty much automatically boot. In fact you probably couldn't install windows by running setup.exe as you can't boot two operating systems at once on the same hardware and you would need to boot an operating system to execute setup.exe. Perhaps look into VirtualBoxOSE.

---

### Post by electrojustin on 2012-01-08
Actually if you have the ISOs on disk perhaps look into flash drive booting. By the way, are you intending on dual booting windows and ubuntu, installing windows second? If so, be warned that windows will get rid of the bootloader, grub, and you will need to reinstall it to get ubuntu working again.

---

### Post by 73ckn797 on 2012-01-08
> **tejli007 said:**
> so please just tell me how can i fix my problem.
I believe that "snowpine" has your answer.

CD drives are quite cheap these days so why not replace yours.

---

### Post by tejli007 on 2012-01-09
> **Learning Linux 2011 said:**
> I think I might have a possible solution, but you would have to be using Windows XP or earlier I think. I don't think Windows Vista or Windows 7 supports this anymore, but I could be wrong.
 
You would have to create an MS DOS partition using linux, and make it FAT32, no bigger than 32 GB.
Then copy the i386 folder from your Windows disc/ISO file onto the new partition.
 
Then boot from a DOS floppy, switch to the i386 folder and run setup (although I think it is called winnt or winnt32 as I recall)
 
It might not work, but it is worth a shot.
 
Thank you sir!
 
Well there was a option.
For every Problem is one Option dear Friends.
 
Thank you all for the help.Most thanks on Learning Linux ur Pro bro :)

---

### Post by dcstar on 2012-01-11
> **Learning Linux 2011 said:**
> I think I might have a possible solution, but you would have to be using Windows XP or earlier I think. I don't think Windows Vista or Windows 7 supports this anymore, but I could be wrong.

You would have to create an MS DOS partition using linux, and make it FAT32, no bigger than 32 GB.
Then copy the i386 folder from your Windows disc/ISO file onto the new partition.

Then boot from a DOS floppy, switch to the i386 folder and run setup (although I think it is called winnt or winnt32 as I recall)

It might not work, but it is worth a shot.

And to quote the reason this forum exists (clearly stated at the top of this forum):

*All your general support questions for **Ubuntu, Kubuntu, Edubuntu, Xubuntu and Lubuntu**.*

If people want solutions for Windows issues that have nothing whatsoever to do with Ubuntu, then refer them to Windows forums.

This is **not** a "General" help forum for anyone who is too lazy to go to an appropriate resource, there are enough genuine Ubuntu issues here to keep people occupied without cluttering up the place with these irrelevant ones.

Keep this up and people will eventually be posting here asking for help repairing their cars or cooking their meals.

---

### Post by Humanity to others on 2012-01-31
If you want Dos Application on Ubuntu, you  can use dosemu. Is it avialble on ubuntu software centre

---

