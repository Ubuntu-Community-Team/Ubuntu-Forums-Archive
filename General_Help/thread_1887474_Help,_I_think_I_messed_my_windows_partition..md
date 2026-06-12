---
title: "Help, I think I messed my windows partition."
date: 2011-11-27
forum: General Help
---

### Post by serghei on 2011-11-27
Hello, first of all I would like to excuse my English, grammar and all that stuff, I'm not a native.

After a power outage my laptop (actually I think the better word to describe 'net-book'), an acer aspire one, turned off. That's weird I know because usually it should have worked just fine only on it's battery. Now after I started my net-book again, windows started loading, and loading, and loading, and after that suddenly it restarted itself. Couldn't even start in safe mode, same thing happened. Disabled the auto-restart feature from windows and "voila" BSoD (unmountable boot volume xxx Stop : 0x000000ed bla bla bla). I had this problem on my main computer a while ago and used my windows xp cd to repair my OS, i know i's because the main boot sector. 
The problem with this 'little one' is that it has no CD-dvd-flopy-drive, only a "service partition" which is protected by a password (some crazy dude at acer maybe thought that the "normal user" is to dumb to repair it's OS).
So to repair only the MBR form the windows partition I turned to linux. Instaled on an 8 GB usb memory stick from my main computer, plugged it in my net-book, pressed f12 booted from it, worked like a charm.
Installed Bit Defender, ran an anti-virus check and nothing returned, jut an IO error.
After a ton of google-ing I learned about lilo (not to much apparently) so i started to put some codes in the terminal, rebooted my computer and surprise...BkSD when loading windows (not even trying actually to load windows)....
To make things even worse I installed then ms-sys... after messing with that a bit I can access my "service partition" but i can only reset my computer to it's factory defaults... this means I'll loose all my data and stuff (and I have a lot of homework, projects, and books for my university, not to mention a ton of pictures, and other important stuff on it). The problem is now I can't mount my drive anymore in linux, I tried "testdisk" (it has a gui witch I understand a bit) it does not help allot the only thing it did it removed the BkSD and replaced it with a "No OS is installed" (or something like that).
 I'll attach to my post some screen-shots of what i did so you can see with your own eyes what's the problem. If windows is not solvable, I would actually just want to be able to mount the drive (/dev/sda2) so I can recover my data from it.

Thank You for your time, 


Serghei.



[[IMG]http://thumbnails46.imagebam.com/16152/fa7253161514766.jpg[/IMG]]("http://www.imagebam.com/image/fa7253161514766") [[IMG]http://thumbnails57.imagebam.com/16152/e14246161514770.jpg[/IMG]]("http://www.imagebam.com/image/e14246161514770") [[IMG]http://thumbnails54.imagebam.com/16152/8493e3161514772.jpg[/IMG]]("http://www.imagebam.com/image/8493e3161514772") [[IMG]http://thumbnails33.imagebam.com/16152/bfe078161514774.jpg[/IMG]]("http://www.imagebam.com/image/bfe078161514774") [[IMG]http://thumbnails29.imagebam.com/16152/4e918d161514776.jpg[/IMG]]("http://www.imagebam.com/image/4e918d161514776") [[IMG]http://thumbnails45.imagebam.com/16152/2b1b6e161514779.jpg[/IMG]]("http://www.imagebam.com/image/2b1b6e161514779") [[IMG]http://thumbnails67.imagebam.com/16152/bf99b9161514781.jpg[/IMG]]("http://www.imagebam.com/image/bf99b9161514781") [[IMG]http://thumbnails61.imagebam.com/16152/28f970161514782.jpg[/IMG]]("http://www.imagebam.com/image/28f970161514782")

---

### Post by lechien73 on 2011-11-27
Hi Serghei & welcome to the forums,

It sounds like your NTFS partition table may be corrupt. In these situations, I usually use TestDisk to recover data. You can download it from [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I hope that helps!

---

### Post by westie457 on 2011-11-27
Hello first things first. Go to [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
and download a recovery .iso for windows 7, not free but worth the cost.

Then go to 
[http://windows.microsoft.com/en-us/windows7/installing-windows-7-on-a-netbook](http://windows.microsoft.com/en-us/windows7/installing-windows-7-on-a-netbook) and follow the instructions to create a bootable USB of the file you downloaded.

This should be able to repair your Windows installation.

If it cannot then the best thing to do is use a Live Ubuntu USB in try mode to copy and paste your personal files to an external hard drive and then factory restore.

Hope this helps.

---

### Post by serghei on 2011-11-27
Thanks for the help, the thing is that I have windows xp installed (It's weird I know because I bought it in December 2010, it should  have been 7 but ...) on it, so the thing with windows 7 is excluded. 
I run ubuntu from a 'persistent' usb stick, but the thing is that I'm not being able to mount the "broken" drive, the thing is that before I messed it up, with lilo or ms-sys or whatever I messed it up with, it appeared just like any other drive. But I was stubborn and tried to fix it.

I tried rebuilding my boot sector with TestDisk but no results... 
This is what TestDisk says: 
[[IMG]http://thumbnails54.imagebam.com/16154/17d02d161531501.jpg[/IMG]]("http://www.imagebam.com/image/17d02d161531501") [[IMG]http://thumbnails65.imagebam.com/16154/0e0082161531509.jpg[/IMG]]("http://www.imagebam.com/image/0e0082161531509") [[IMG]http://thumbnails21.imagebam.com/16154/5806c3161531513.jpg[/IMG]]("http://www.imagebam.com/image/5806c3161531513") [[IMG]http://thumbnails20.imagebam.com/16154/47045b161531520.jpg[/IMG]]("http://www.imagebam.com/image/47045b161531520") 

I tried photorec to recover my data, the problem is that it recovers everything... i need it to be a little more selective, and another problem about it is that it puts everything in locked folders in my home folder, witch will surely get full (the usb stick is only 8 GB, the hard drive is 160).

So, any other ideas?

Thank you again for your time.

---

### Post by westie457 on 2011-11-27
Use the desktop pc to make a USB of your XP cd using the instructions in the second link that was posted by me. That should be able to repair the netbook.

Another plan of action to consider if it cannot be repaired is to connect the netbook hdd to the desktop pc if there is SATA connections on the motherboard then copy and paste to the desktop pc's hard drive.

---

### Post by rng on 2011-11-27
You have got a tough problem. Following links may be useful to you: 

[http://ubuntuforums.org/showthread.php?t=1883722](http://ubuntuforums.org/showthread.php?t=1883722)

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by serghei on 2011-11-27
Can't open it to access the hard-drive, the net-book is still in warranty, and to make an usb recovery disk would be an option, but the thing with my desktop computer is that it's a system made by me so it does not have an original (genuine) windows cd.. I'm afraid that if I will use that cd I might have some problems with the warranty.

I can tell you what I did with ms-sys:

[[IMG]http://thumbnails64.imagebam.com/16155/202809161547235.jpg[/IMG]]("http://www.imagebam.com/image/202809161547235") [[IMG]http://thumbnails50.imagebam.com/16155/045ae3161547238.jpg[/IMG]]("http://www.imagebam.com/image/045ae3161547238") [[IMG]http://thumbnails61.imagebam.com/16155/c4e74f161547240.jpg[/IMG]]("http://www.imagebam.com/image/c4e74f161547240") 
 
All the commands were successful but not in my interest apparently.

With lilo I have no idea what I did, just copy-pasted some codes found on google.

It is clear that i did something wrong, as long as before I intervened the drive was mounted, and I was seeing it in linux like any other drive..

Rng, I'll read the links in your post and see what I can do.

Thank you.

---

### Post by serghei on 2011-12-09
Problem solved. 
The only solution that I had to recover my data was to buy an 500 GB external hard disk, after that I used photorec to transfer everything, from the internal hard disk, on it (it took 'bout 5-6 hours on my netbook), and then it took me about 3 days to sort everything from the hundreds of auto-generated folders and because of the different file names. :lolflag::lolflag:
After that I used the system recovery partition (before I've made it bootable with testdisk). 
Thanks a lot for your time and advice.

---

