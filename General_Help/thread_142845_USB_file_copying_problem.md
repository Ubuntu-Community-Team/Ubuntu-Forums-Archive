---
title: "USB file copying problem"
date: 2006-03-11
forum: General Help
---

### Post by sargonx on 2006-03-11
Hello there. I've been searching the forums and google for a bit now and haven't found anything on this, so here goes my problem: I cannot copy files from my hdd to a USB pendrive. More precisely, I can copy them and everything will seem to be OK, and when I insert the pendrive on another computer (or mine, for that case), the pendrive seems to be empty, so that nothing has been copied. Nautilus or any other program will "read" what I have copied into the pendrive in my computer when I just copied it, but if I unplug and replug the usb even my computer will see the drive as empty!!

I've tried this on two different computers (desktop and VAIO notebook), with different Ubuntus (Breezy and Dapper Flight5 respectively), and with three different pendrives of different sizes from different manufacturers (Kingston, Memorex and I don't remember the third). Oh, I have tried plugging the USB on several ports of each computer. And Windows computers will also see the drive empty! :confused: 

Hope this was clear. Is there any possible solution? Thanks in advance!

---

### Post by kittycatsexycat on 2006-03-11
make sure you 'unmount' the USB, or do it through root

hope that helps

:KS

---

### Post by closeyourwindows on 2006-03-11
I have been having the same issue.  I used sudo to copy and that seemed to work.  are you using the terminal or the GUI to do this?  I noticed this problem once I installed kubuntu-desktop and it started when I tried it it Konquerer and would not work after that even in gnome.  some times it did not work using sudo in the terminal either, it looked like it was in there and when I did searched to make sure it was in there before I put it in another computer I did show.  However once I took it out and put it in another computer it was not there.  I uninstalled kde and it started working again.  

I am not saying that it was kde, but it helped for me.  another thing I noticed is that if I use the terminal to copy, the LED in the jumpdrive will blink as normal but once it is done copying I have to wait a bit longer becuase the light is still blinking.  I have three jumpdrives and they all do the same thing and I had the same problem with all of them. 

I also found that some one had the same issue on linuxquestions.org and their solution was much different.  If I come across it I will post it in here.  hope this helps.

---

### Post by sargonx on 2006-05-12
Open, good advice. Had already thought of waiting until the LED stopped blinking, but didn't work. And definitely it is not a hardware problem. Anyway, it seems to be solved in Dapper Beta (give it a try). Thanks for the answer!

---

### Post by Serguei_89 on 2006-05-12
Similar problem here. I use an ifp-190T Mp3 player with UMS firmware, which makes it appear anywhere as a simple usb mass storage device. And it works fine in windows.

In Ubuntu however, device shows up on the desktop when I plug it in and turn it on. I copy files and folders to it. Everything looks ok on the PC. I unmount it from the desktop and unplug the device. I look at the device and it doesn't see any files on itself. 

How to fix this on current 5.10 Ubuntu?

---

### Post by ypout on 2006-10-03
I had no issue on 5.10, but have put Dapper on a new PC and I'm getting the same problem, very frustrating.

I just tried using the Eject option (on Dapper) and a little popup came up saying please wait while writing data to device - or words to that effect, and all seems well...

---

### Post by freddan83 on 2006-10-23
Im having the exact same problem in edgy, so if someone has a nice solution that would be great

---

### Post by TiredBird on 2006-10-23
I encountered the same problem and found it was a matter of delayed writing. On small writes it wasn't much of a problem but if I transferred a large amount of data in with a command like 'cp' or 'rsync', (100 MB or more), I found it took forever, (as much as five minutes), for all of the delayed writes to take place. I found the way to verify what it was doing was to issue a 'sync' command from the command line and wait until it returned a command prompt, (often many minutes), before removing the thumb drive. Otherwise, the data didn't get there but because other programs use the data in the buffer it would appear to have been written.

I now mount all of my USB drives with a 'sync' in the options to make sure that data is not accumulated in a buffer. However, when I am going to transfer a significant amount of data to the thumb drive, (say 25 MB or more), I remount the drive without the 'sync' option. (If you don't do that the writes can take as much as 10 times as long. Not a problem with small amounts but hell on large transfers.)

---

### Post by freddan83 on 2006-10-23
that pretty much sucks, must be a better solution??

---

### Post by TiredBird on 2006-10-23
I might be wrong but that's my experience.

---

