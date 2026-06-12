---
title: "[newbie] disk has many bad sectors"
date: 2010-04-14
forum: General Help
---

### Post by QuiglesTheGreat on 2010-04-14
Hi,

I turned on my computer today and loaded into Windows XP Professional, it came up with an error message, I clicked OK and it shut down so I booted into Ubuntu 9.10, it then came up with an error of "DISK HAS MANY BAD SECTORS." I opened up SMART, did a scan and got these messages:

ID: 5

Attribute: Reallocated Sector Count - Count of remapped sectors. When the hard drive finds a read/write/verification error, it marks the sector as "reallocated" and transfers data to a special reserved area (spare area).

Assessment: (red dot) Warning

Value: Normalized: 219
       Worst: 219
       Threshold: 63
       Value: 347 sectors

_________________________________________________________________

ID: 197

Attribute: Current Pending Sector Count - Number of sectors waiting to be remapped is subsequently written or read successfully, this value is decreased and the sector is not remapped. Read errors on the sector will not remap the sector. it will only be remapped on a failed write attempt.

Assessment: (red dot) Warning

Value: Normalized: 253
       Worst: 253
       Threshold: 0
       Value: 3 sectors


The disk is a 123 GB Hard Disk - ATA Maxtor 6Y120L0
I don't know how old it is because it was my brothers and he is 28 so he has probably had it for a while.

I want to get my files on the Windows side of the machine but I can't access them, please don't tell me ways of reformatting the drive and losing all of my data. I really need these files because they are school work and pictures of holidays. I will then, if I get my files back, make it a Windows 7 Professional/Ubuntu 9.10 machine

Thanks,
QuiglesTheGreat

P.S I have used Ubuntu for about 2 years now but I haven't used it much and haven't learned very much.

---

### Post by QuiglesTheGreat on 2010-04-14
Bump

---

### Post by 2hot6ft2 on 2010-04-14
> **QuiglesTheGreat said:**
> 
Value: Normalized: 219
       Worst: 219
       Threshold: 63
       Value: 347 sectors

Value: Normalized: 253
       Worst: 253
       Threshold: 0
       Value: 3 sectors

No need to panic. It's an indication that the drive MAY be beginning to fail. From what I've seen there are 1 or more bugs in the program that reports it. I have a 250GB drive with more than 655,000 bad sectors and it's been running for months (if not over a year) like that.

It was in my laptop but I replaced it with a larger drive and now I just use it for things that can be replaced.

I also have another with 27 bad sectors I think it is and it's still in use too and has been for months since the warning first showed up. It's several years old.

So just back things up and keep an eye on it and plan for the worst and hope for the best. There's nothing else you can do about it. If it's going to fail then it will fail.

---

### Post by 2hot6ft2 on 2010-04-14
You can access what's in windows by installing these programs if you don't already have them like this
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install ntfs-config ntfs-3g ntfsprogs
```
hit Enter
You will have to enter your password which wont be displayed just type it in and hit Enter
When it finishes close the terminal and go to
System --> Administration --> NTFS Configuration Tool
There are only 4 options (2 then another 2) so real simple.
I recommend against automatically mounting the windows partition, you can always browse to it you'll just have to enter your password.

Then you can go to Places > (your windows drive/partition)
Enter your password and hit Enter
Then browse the windows system for whatever you want to copy/save.

:popcorn:

---

### Post by QuiglesTheGreat on 2010-04-15
Hi, 

I installed NTFS Configuration Tool and I only get 2 options:

 - Enable write support for internal device (can't select)

 - Enable write support for external device (automatically selected)

I then click OK and go to Computer and it isn't there, please help!

Thanks,
QuiglesTheGreat

---

### Post by QuiglesTheGreat on 2010-04-15
Bump!

---

### Post by 2hot6ft2 on 2010-04-15
> **QuiglesTheGreat said:**
> Hi, 

I installed NTFS Configuration Tool and I only get 2 options:

 - Enable write support for internal device (can't select)

 - Enable write support for external device (automatically selected)

I then click OK and go to Computer and it isn't there, please help!

Thanks,
QuiglesTheGreat
There is usually 2 options then you click Apply and another window pops up with 2 more options then you click Ok. But it will depend on what NTFS partitions it finds. See the 2 screenshots below.

It should be below Computer in Places.
I click on Places > drive/partition. See screenshot below.
If the windows partition doesn't show up then it is probably corrupt.

1st pop up - 2nd pop up (since I didn't select it in the first pop up it's not selectable in the second) - where to find windows.

---

### Post by 2hot6ft2 on 2010-04-15
[B][COLOR="DarkRed"]Making any changes to the partitions while running the installed system can totally hose your system so I'm telling you how to copy the files from the windows partition here.

If you want to try and recover the windows partition you should run testdisk from the live cd in the same manner using testdisk from it. You would have to go to 
System > Administration > GParted
and right click on anything with a lock on it and select swapoff for the swap partition and unmount for anything else prior to starting testdisk. You would also have to copy/move anything you saved to a usb drive or somewhere before rebooting the livecd or it would be lost.
Also it would be saving everything in RAM so you would have to have enough for everything you saved plus the livecd and testdisk to run.[/COLOR][/B]

[B]Having made that clear. On to how to recover the files from the windows partition using the Ubuntu install.
[/B]
Once you've recovered any important files then you can try recovering the windows partition if you want.

If you can't mount you windows partition doing it the way I said and you can't boot into it there is still hope.
First you'll need to install testdisk. And we'll install nautilus-open-terminal while we're at it (you'll see why in a minute).
Open a terminal
Applications > Accessories > Terminal
and run
```
sudo apt-get install testdisk nautilus-open-terminal
```
And here is a guide to using testdisk.
[How to: Recover data with testdisk!]("http://ubuntuforums.org/showthread.php?t=387922")

It's really not that hard to use but it does take a while to complete scanning the drive for partitions.

You can even copy files from the partition while using testdisk and they will be saved to the folder you start testdisk from so we want to start the terminal in a folder where we want to save everything to. First we need to restart nautilus for open terminal to be available by running this
```
sudo killall nautilus
```
It will close all nautilus windows, then you can open them again.
Make a folder to save things from windows in somewhere
Right click > Create folder

You should also run
```
sudo fdisk -l
```
and write down the info. or save it in a text file so you know what partition is what before starting testdisk.

Open the folder you created to save things to, right click inside it and select Open in Terminal.
This is the terminal you want to run testdisk in by running
```
sudo testdisk
```
That way anything you save using the "c" for copy in testdisk it will default to saving it in that folder.

Keep in mind that the command **ls** (lower case LS) will list the contents of the folder you're in and **cd FolderName** will change the folder you're in while in the terminal to get around. Case is always important a "h" is not the same as a "H".

Good luck.

---

### Post by mk1w86 on 2010-04-15
If you can't mount your partition I would recommend you have a look at TestDisk:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Specifically this part which probably applies to you:

[http://www.cgsecurity.org/wiki/Damaged_Hard_Disk](http://www.cgsecurity.org/wiki/Damaged_Hard_Disk)

Pay particular attention to the fact that if this is the only copy you have of the data you shouldn't use the disk or make any changes to anything until you have an image or copy of the drive saved somewhere.

After you have recovered your data (if you can) you can run the drive diagnostics from Seagate (they now own Maxtor) to properly check the state of your drive.  You can download them from here:

[http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD](http://www.seagate.com/ww/v/index.jsp?locale=en-US&name=SeaTools&vgnextoid=720bd20cacdec010VgnVCM100000dd04090aRCRD)

REMEMBER TO KEEP REGULAR BACKUPS OF IMPORTANT DATA IN FUTURE! ;)

---

### Post by QuiglesTheGreat on 2010-04-16
Replying to 2hot6ft2's message.

I get screenshot 1 but not number 2, and the third screenshot, my drive does not show up.

Now just trying your instructions on your other post.

Thanks,
QuiglesTheGreat

---

### Post by QuiglesTheGreat on 2010-04-16
Hey,

Just using TestDisk to copy my Windows files to the Ubuntu side and it's working really well.

Thanks for all of your help,
QuiglesTheGreat

---

