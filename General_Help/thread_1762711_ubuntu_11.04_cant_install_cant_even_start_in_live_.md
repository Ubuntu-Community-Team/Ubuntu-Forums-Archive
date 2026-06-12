---
title: "ubuntu 11.04 cant install cant even start in live cd mode!!"
date: 2011-05-19
forum: General Help
---

### Post by suraj18 on 2011-05-19
Hello!
I am trying to install ubuntu 11.04 on my PC but i couldn't make it to the desktop of Ubuntu 11.04... i'm so in a need of help i've tried CD burning, using USB/flash drive as a bootable media but couldn't make it to install or get a live system :( 

It boots fine, take a time but it boots than shows the desktop background with log off, volume control and a button which has a arrow sign i think its an network button and a mouse which i can move freely....i cant even click on those buttons which i can see in upper right corner, and its ends here... nothing happens after that....i tried 100times but in vain.... :( is there anyone who can help me?? :| what is happening?? eagerly waiting for the help as i want to stretch my fingers on 11.04 :(

---

### Post by lmn. on 2011-05-19
I also have this problem. I'm in a working 11.04 but if i ever need to reinstall I'm worried I wont be able to without installing windows & using wubi.

---

### Post by suraj18 on 2011-05-19
is there anyone who can help us?? :(

---

### Post by philipballew on 2011-05-19
does it boot into the live cd? also describe your problem in more detail step by step whats wrong so people can know exactly what your problem is and can easily help you.

---

### Post by lmn. on 2011-05-19
my problem is a 'cannot mount live file system .squashfs' or something similar. 
Although I have experienced the blue screen with a little switch at the top.. which is a real pain...

if you have a copy of windows, try wubi. and then remove windows.

---

### Post by philipballew on 2011-05-19
wubi is ok for testing to se if it runs on your system. but to use it permintly there is not something id recomend for optimal system performance. ubuntu on wubi is running inside the windows file system almost in a chroot type enviorment with a ntfs partition. ubuntu runs better on a ext type file system

---

### Post by lmn. on 2011-05-19
> **philipballew said:**
> wubi is ok for testing to se if it runs on your system. but to use it permintly there is not something id recomend for optimal system performance. ubuntu on wubi is running inside the windows file system almost in a chroot type enviorment with a ntfs partition. ubuntu runs better on a ext type file system

fair enough, I didn't know that.

---

### Post by philipballew on 2011-05-19
its all good. I wonder if he can boot into the live cd. because if you can then it will install most  always without to much work

---

### Post by lmn. on 2011-05-19
I am unable to reach the try/install screen. soon after booting from disk/usb this error appears:
[FONT=Courier New]
Enter 'help' for list of built-in commands (initramfs)mount: mounting  dev/loop1 on//filesystem.squashfs failed: Input/Output error
can not mount/dev/loop1c/cdrom/casper/filesystem.squash on "filesystem.squashfs"[/FONT]

both hd's formatted as ext4

sorry for hijacking this thread if sujara's error is different

---

### Post by philipballew on 2011-05-19
did you make the cd yourself?

---

### Post by lmn. on 2011-05-19
I did indeed

---

### Post by philipballew on 2011-05-19
There is a possibility that it is the disc that you made that could be the culprit.

---

### Post by lmn. on 2011-05-19
definitely a possibility, yes. I hope so anyway.
Will download and burn a new copy for when I next break my install. lol.

---

### Post by philipballew on 2011-05-19
always remember to burn at a slow speed to ensure or make the likelihood greater that no errors will occur.

---

### Post by suraj18 on 2011-05-20
Hello philipballew and lmn nice to have you in this discussion :) 

actually i don't get any of the error in verbose, desktop just doesn't load fully only 3-4 icons on the upper right corner only after that nothing happens... yes i burned the CD myself and took all the necessary precautions like burning in slow speed, verifying the data on the disc... i even checked the disc/USB from the unetbootin prompt whether to check the disc for any errors (when i am using USB to boot) and everything is OK.... i burned around 10-11 CD's but all in vain... below are the things I've done:

Using USB/FLASH
===============
1.I made the bootable USB with included USB creator but its says some file error when i boot. so i reformatted and used unetbootin.
2.Created bootable USB using unetbootin shows the prompt 
    (a) Try ubuntu without installing
    (b) Install ubuntu
    (c) Check the media for errors
    (d) Boot from HDD

i tried first option, its boots fine with ubuntu splash screen or logo moving colored tiny disc as a progress bar to and fro for a while then is shows me the screen probably be the desktop because it has 2-3 icons on upper right corner i.e. log off, volume, network(Probably)... and this is it.... no progress after then.... i can move mouse freely click on it but of no use... i thought may be it is loading and i must wait for a while but nothing happens even after a hour :(

Now second option..... Read all above everything same... :confused:

Third option....  it checks the media and found no errors so media is fine..

Using Disc
==========
when i insert the CD it doesn't show any menu or prompt it directly start to boot so i don't have any option but just to wait for the system to load... so when it shows the desktop background whole story begins.. read above i.e GOTO first option in using USB/FLASH 

this is what happening... :( :( don't tell me the concept of using ubuntu within windows as I'm not in the favor of doing it.. I'm using windows 7 and I've fedora 14 installed i.e. Dual boot system and I've no problems with this configuration..... 

Now i think, its the clear picture of what's happening! Help!! :( (

---

### Post by linuxinstalledfromhdd on 2011-05-20
Existing Windows users can download a freeware ISO burner to burn your above downloaded copies of Ubuntu here:
 [http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)

---

### Post by suraj18 on 2011-05-20
i think its another burning software right?
should i waste another CD?? :| :confused:

---

### Post by philipballew on 2011-05-20
What are each one of yours computer spects. what version of ubuntu are ytou trying to install and what method are you trying to install it by?

---

### Post by linuxinstalledfromhdd on 2011-05-20
Use a network installation from a floppy drive if everything else doesn't work.

---

### Post by philipballew on 2011-05-20
alterninte install?

---

### Post by suraj18 on 2011-05-20
mine is

OS : Windows 7 Ultimate 32-bit(6.1, Build 7601)Service Pack 1    System Motherboard : DG41RQI
Processor : Intel(R) Core(TM)2 Duo CPU E7400 @ 2.80GHz (2 CPUs), ~2.8 GHz
Memory : 2048MB RAM
HDD : (a) 1 TB SATA
      (b) 500 GB SATA
      (c) 160 GB PATA
160GB HDD is primary OS installed is Win 7 and Fedora 14 on different partitions.

Graphic Card : NVIDIA GeForce 8400 GS

---

### Post by suraj18 on 2011-05-20
> **philipballew said:**
> alterninte install?

i couldn't understand :-?

---

### Post by suraj18 on 2011-05-20
> **linuxinstalledfromhdd said:**
> Use a network installation from a floppy drive if everything else doesn't work.

its a home PC so no LAN network and i removed floppy disk drive :P

---

### Post by linuxinstalledfromhdd on 2011-05-20
I would use an alternative installation disc or swap out some hardware from another system to test it.. it sounds like you have some really old stuff equipment

---

### Post by suraj18 on 2011-05-20
> **linuxinstalledfromhdd said:**
> I would use an alternative installation disc or swap out some hardware from another system to test it.. it sounds like you have some really old stuff equipment


I've tried that also... and old stuff?? i dont think so..

---

### Post by linuxinstalledfromhdd on 2011-05-20
I think you need to start from the beginning. 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Don't use 11.04 either.

---

### Post by linuxinstalledfromhdd on 2011-05-20
Install it from a USB if possible.

---

### Post by suraj18 on 2011-05-20
> **linuxinstalledfromhdd said:**
> I think you need to start from the beginning. 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Don't use 11.04 either.

> Install it from a USB if possible.

with 10.10 i've same problem but not with the previous releases before 10.10... and i think you haven't read my problem i included USB installation as well... USB installation has the same problem...

---

### Post by suraj18 on 2011-05-24
see if information below can help : 

after inserting Ubuntu 10.10 LIVECD and going to the verbose mode by pressing arrow keys i found this on top:

(process : 349) : GLib_WARNING ** : getpwuid_r() : failed due to unknown user id (0) 
                                                          stdin : error 0


UBUNTU 11.04

stdin : error 0
stdin : error 0
stdin : error 0
stdin : error 0

for both the ubuntu version (10.10 and 11.04) after that error text, it starts loading some other things and desktop background appears with 3 icons on upper left side..... and its over that screen stays forever...

is anything related to my Graphic card ?? 
NVIDIA GeFORCE 8400 GS!!

help anybody? admin? moderator? users?? :( :(

---

### Post by linuxinstalledfromhdd on 2011-05-24
For now install LTS version of Ubuntu 10.04 and file a bug report.  You need to check your log files and try to report all of the errors you are recieving along with your bug report.  

You are receiving this kind of error, I haven't seen one of those in a quite some time. 

GLib_WARNING **  

Roll it back to 10.04 for now.

Just a Live USB stick to install it or a Disc.  Don't use Wubi.  

If you need help compiling a bug report to submit just ask.

---

### Post by muralysunam on 2011-07-20
I toooo suffers from this problem in desktop
Asus P8
core i3 2nd generation

---

### Post by no2498 on 2011-07-20
from what im seeing you need to turn off every thing but the cd
turn off the hard drive every thing but the cd player
boot to/from the cd

---

