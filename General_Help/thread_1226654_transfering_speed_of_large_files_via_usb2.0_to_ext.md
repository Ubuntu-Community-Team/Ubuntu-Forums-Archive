---
title: "transfering speed of large files via usb2.0 to external hd is 1mb/s"
date: 2009-07-29
forum: General Help
---

### Post by jtech55 on 2009-07-29
Alright, I'll try to be as detailed as I can about this problem. I have a 300GB external HD (ext4) that comes with USB 2.0. The first thing I tried to do was to copy 6GB worth of documents on my computer(A) to the external HD. The file transfer speed hit about 20mb/s in the first 3 seconds, but then slowly dropped over the matter of 20 seconds to a fts of 1m/bs. 
I've been looking around on how to fix this problem, but all I came up with is "async" needs to be enabled, and to do this you need to add a line in the fstab. However apparently I can't put a line in the fstab because my USBS are all automatically mounted by BIOS if I read everything correctly? If any one knows a fix to this or wants to give a shot, thatd be great. thanks

(A.)
OS:           Ubuntu Jaunty
Processor:    Intel® Core™ 2 Duo T7200 2.0GHz 4MB Cache 667MHz FSB 
Memory:       2GB Dual Channel DDR2 SO-DIMM at 667MHz – 2 x 1024MB 
System Drive: 320GB,400RPM (8MB Cache)

More stuff
> Me@Computer:~$ sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   3932 MB in  2.00 seconds = 1968.21 MB/sec              ....don't understand
 Timing buffered disk reads:  204 MB in  3.02 seconds =  67.51 MB/sec

---

### Post by Arup on 2009-07-29
Your USB drives should be mounted when you boot, to solve the slow transfer issue, try disabling USB legacy support in BIOS.

---

### Post by jtech55 on 2009-07-29
Just did that, but same thing is basically occurring. High file transfer rate in the first 3 seconds, then file transfer rate crawls and sustains itself down to about 1.1-1.3mb/s. 
So we made some progress lol.

Copying 10 files in (In "Docs") to "EXTHD"
740.0 MB of 10 GB -- approximately 3 hours left (1.1MB/sec)

---

### Post by mdurham on 2009-07-29
Do a search of the forums, I'm sure that I've seen this problem described before.

#
Painfully slow USB [Archive] - Ubuntu Forums
10 posts - Last post: 9 Apr 2007
Why are USB transfers so slow in Ubuntu? I have to be doing something wrong... it can't possibly be Linux. Or can it? ...
ubuntuforums.org/archive/index.php/t-381235.html
Labeled Forums
#
[ubuntu] Slow USB and SATA Transfer Speeds in Jaunty 9.04 - Page ...
Page 13-[ubuntu] Slow USB and SATA Transfer Speeds in Jaunty 9.04 x86 64-bit Users.
[www.uluga.ubuntuforums.org/showthread.php?t=1150108&page=13](www.uluga.ubuntuforums.org/showthread.php?t=1150108&page=13)
Labeled Forums
#
HDD to USB slow transfer rate?? [Archive] - Ubuntu Forums
8 posts - Last post: 1 Aug 2007
[Archive] HDD to USB slow transfer rate?? Absolute Beginner Talk.
ubuntuforums.org/archive/index.php/t-432119.html
Labeled Forums
#
[ubuntu] Slow USB and SATA Transfer Speeds in Jaunty 9.04 - Ubuntu ...
10 posts - 8 authors - Last post: 28 May
Disk-speeds are acceptable, but when copying from HDD to USB it's incredibly slow - starts off fast but rapidly falls and ~600 megabyte ...
ubuntu-ky.ubuntuforums.org/showthread.php?t=1150108
Labeled Forums
#
USB Hard Drive too slow? - Ubuntu Forums
10 posts - 9 authors - Last post: 1 Oct 2006
I recently put a 300 GB hard drive into a USB 2.0 enclosure and connected it to my machine. However, it seems to be running painfully slow. ...
ubuntuforums.org/showthread.php?t=150026
Labeled Forums
#
Slow transfer with USB hard drives - Ubuntu Forums
Transferring files to USB devices is suddenly really slow (like 1.5 MB/s, ... I've found several threads about slow USB, but so far none of them have helped ...
ubuntu-virginia.ubuntuforums.org/showthread.php?t=754659
Labeled Forums
#

---

### Post by jtech55 on 2009-07-29
Thanks mdurham, but I've gone through those before I posted this one.
Im getting its a Sata problem, Bios problem, external hd problem etc.
I'm just hoping here I can provide info and get a fix
](*,)

---

### Post by ju2wheels on 2009-07-29
Its a known problem that has yet to be fixed and numerous threads provide "solutions" that typically dont work.

From my research, the issue has something to do with gvfs (IIRC, I looked up the issue a long time ago) and copying using the GUI. 

If you copy from the command line, using cp, you will not see this drastic speed drop when copying over USB.

---

### Post by jtech55 on 2009-07-30
I did:
> Me@Computer:~$ cp -r /home/Me/Desktop/Music(30GB)/ /media/EXTHD

In the terminal it didn't display the file transfer rate after I entered the code above, but I had to leave my pc on over night and it's still copying the files. Bout 16 hours now. Guessin not GUI problem? 
[-X

---

### Post by ju2wheels on 2009-07-30
Well on my machine I can trasnfer ~850gb from USB drive to USB drive using cp in 12-16hrs, while I can barely transfer 49gb using the GUI in the same amount of time. Its a noticable difference on my machine.

---

### Post by LowSky on 2009-07-31
> **ju2wheels said:**
> If you copy from the command line, using cp, you will not see this drastic speed drop when copying over USB.

Command line is not the answer!!

You can't tell the average use to use cp commands in a terminal and it doesn't work for me, it still crawls. this is a Kernel/Driver Issue. something to do with how the devices is loaded and then sent the data. It has been annoying me for over a year, since beta of 8.04. no matter what, Windows plays much better with USB transfers.

All I want to do is move a 1GB file to a flash drive, and I cant as it fails somewhere around 200MB. Even smaller transfers take minutes instead of seconds.

Whats the point of a 16GB flash drive is you cant move/store large files and folders on it?

---

### Post by ju2wheels on 2009-07-31
This is one of those things that wont get fixed until everyone decides to come together and bitch and make a scene about it like was done for the laptop hard drive killing problem about a year ago.

---

### Post by moster on 2009-07-31
Not by any chance intel chipset maybe? :)

---

### Post by ju2wheels on 2009-07-31
Nope, my machine lists the USB Controllers as nvidia corp MCP51 usb controller. Only thing Intel is the CPU.

Ive had this problem on multiple computers though, so I doubt its related to a specific chipset.

---

### Post by moster on 2009-07-31
If I were you I would just boot Carmic Koala live and see if I had problem there. If not, maybe upgrade kernel in jaunty or something..

---

### Post by jtech55 on 2009-07-31
I like the idea moster, but besides using a live cd, does anyone else have any ideas or theories for that matter of how else to stop the transfer rate drop? I'm not a ubuntu advance user but i'm sure there is something in /etc or /sys that can be edited to solve this issue? :(

---

