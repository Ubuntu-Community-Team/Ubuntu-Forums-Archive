---
title: "Startup Disk with Windows ISO"
date: 2010-07-18
forum: General Help
---

### Post by HoodedHooligan on 2010-07-18
I have a 1 tb external hard drive and I was trying to put a windows.iso on it with startup disk creator but everytime I would select the windows iso it wouldn't show up.

Some background:

- the disk images are from the reboot disks that came with my labtop
- I do not have access to windows

Edits:

Using gparted, I turned my external hard drive into a bootable and put both ISO disc on it. Once I plugged it in my labtop and turned my labtop on, I get an error messages that says "BOOTMGR is missing". 

- I ripped the both ISO images from the 2 system recovery disc that I ordered from HP specially for my brand of laptop.
- My CD-ROM drive does not work, or else I would have just used the disc regularly
- The operating system currently on the labtop is Ubuntu 10.04

---

### Post by lkjoel on 2010-07-18
> **HoodedHooligan said:**
> I have a 1 tb external hard drive and I was trying to put a windows.iso on it with startup disk creator but everytime I would select the windows iso it wouldn't show up.

Some background:

- the disk images are from the reboot disks that came with my labtop
- I do not have access to windows
Are you sure that the file is not named .windows.iso?
And are you sure that you were looking in the correct place? (that happens a lot of times to me:p)

---

### Post by HoodedHooligan on 2010-07-18
The iso is called bootDisk1.iso and I know where it is at on my computer but when I select it with the startup disk creator, it doesn't show up.

---

### Post by lkjoel on 2010-07-18
So you cannot select it right?
If so, on selection box, and on the correct folder, type in the text field: file.iso

---

### Post by bumanie on 2010-07-18
Don't believe you can make a start-up for windows with start-up disk creator, it only works for ubuntu, as far as I know. There is a universal usb start-up disk creator at pen drive linux, but it can only configure various linux distro's. 
Windows 7 will install to a usb stick, but not a usb external hard drive. Not believe xp or vista have that capability - there may be a 'hack' somewhere on the internet if you do some searching.
Not sure whether you could possibly install your version of windows to an internal hard drive and then clone it with dd to an external hard drive - never tried it - that may work, but no guarantees.

---

### Post by C.S.Cameron on 2010-07-18
The only method I have found to run XP off of a USB flash drive is described here:

[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)

If you just want to make a Windows 7 install disk this should work:

1. sudo apt-get install gparted
2. open gparted -> format stick to ntfs
-> put bootable flag (right click in gparted - manage flags)

3. extract win7.iso to usb stick or if you have live dvd just copy contents to usb stick

From amedac

---

### Post by HoodedHooligan on 2010-07-18
Yea I just figured that startup disk creator only works with ubuntu .iso

Is there some other program I can use then.

---

### Post by HoodedHooligan on 2010-07-19
Well I am not trying to run Windows Vista (the version of windows I have) off of the external, what I am trying to do is to change the OS from Ubuntu back to Windows. In that sense, I only need the harddrive to help put Windows back on my labtop since my CDdrive its destroyed.

---

### Post by lkjoel on 2010-07-19
There are USB CD drives, but they do cost a lot.

---

### Post by HoodedHooligan on 2010-07-19
So far, gparted seems only to create partitions on the external itself instead of helping to put one on the labtop.

---

### Post by C.S.Cameron on 2010-07-19
In gparted, on the upper right hand side, there is a dropdown menu for selecting the drive you want to partition.

---

### Post by HoodedHooligan on 2010-07-19
Maybe I'm sayin the wrong thing. I want to put a windows installer on the external harddrive. I am not trying to run windows from the external.

---

### Post by C.S.Cameron on 2010-07-20
So 
1) Format external hard drive to NTFS with gparted. 
2) Set bootable flag.
3) Extract Windows iso to hard disk, or if you have live DVD just copy contents to hard drive.

Edit:
This works with Windows 7 not XP

---

### Post by HoodedHooligan on 2010-07-20
> **C.S.Cameron said:**
> So 
1) Format external hard drive to NTFS with gparted. 
2) Set bootable flag.
3) Extract Windows iso to hard disk, or if you have live DVD just copy contents to hard drive.

So I did the first 2 steps but I don't know how to "extract windows iso to hard drive". Am I supposed to do this through gparted itself because I do not see the option or do I just put the iso on the hard drive just like any other file?

---

### Post by HoodedHooligan on 2010-07-20
Ok well i put the iso(s) on the hard drive like any other file but when I plugged my hard drive into my labtop to install windows I got message that says "BOOTMGR is missing".

When I looked for what to do, I found this:
[http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/](http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/)

But I want to do a system restore type install so this imformation isn't useful.Is there some way to fix this BOOTMGR because I feel like I'm in the home stretch.

---

### Post by C.S.Cameron on 2010-07-20
You should be able to open a iso file using archive manager from the live CD.
Right click on it and select open. 
An iso file is similar to a zip file.

---

### Post by Mark Phelps on 2010-07-21
Maybe I'm misunderstanding what you're trying to do ... but it appears that you are trying to install Win7 from files contained on an external hard drive. Right?

To do that, both of the following must be true:
1) The hard drive must be bootable
2) The PC must be able to boot from an external hard drive

I may have missed it, but I didn't see any discussion of your PC being able to do 2).  If it CAN, then fixing up 1) will make you good to go.  If it can't, nothing you will do will fix it.

BTW, you can't install MS Windows from inside Ubuntu.

---

### Post by HoodedHooligan on 2010-07-21
Its not Windows 7, its Windows Vista in the form of the 2 system restore DVDs. I have the ISOs of both disc and a external harddrive. My BIOS does seem to have support to boot from the external so with gparted I made it bootable. Then I put the ISO images on the external and restarted my computer. After putting the external on the top of the boot-list. I got the BOOTMGR is missing after not to long after that.

Now I'm trying to extract ISOs to see if that will work.

---

### Post by HoodedHooligan on 2010-07-21
When I tried extracting the ISO, I got the following error message:


/usr/lib/file-roller/file-roller/isoinfo.sh: 28: cannot create ___: Is a directory

At this point I am almost ready to claim defeat

---

### Post by Mark Phelps on 2010-07-22
To boot your hard drive, you're going to need to have the boot directory (and its contents) along with a bootmgr file.

If you can't extract them from your existing ISOs, then go to the link below and download and burn the appropriate Vista Recovery CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

It will have the necessary boot directory and files on it -- which you can then copy to your hard drive to make it bootable.

---

### Post by HoodedHooligan on 2010-07-23
So I tried putting all 3 ISOs on the hard drive but still get the "BOOTMGR is missing" error. So should I extract the files from the ISOs and try that or do I need to do something else. I used gparted to format my hard drive nfts and checked the bootable box so that shouldn't be the problem.

---

### Post by C.S.Cameron on 2010-07-23
The method I've mentioned only works with Win7.
I've tried it with XP and Vista and get the same error message as you.

---

### Post by HoodedHooligan on 2010-07-24
So there another process that can work with vista or is it just not possible yet if ever

---

