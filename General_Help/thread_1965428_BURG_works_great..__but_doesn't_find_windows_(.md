---
title: "BURG works great..  but doesn't find windows :("
date: 2012-04-25
forum: General Help
---

### Post by libspero on 2012-04-25
Hi guys,

Just installed Precise 12.04 and have to say it is great..  no problems at all with installation.  Just works.  Period.

Soo...   I've set about trying to break it :D

The first thing I wanted to do was install BURG so I could dual boot into either Ubuntu or **cough**  [SIZE="1"]windows[/SIZE].

I found and installed it with Terminal no problem thanks to an online guide.
Rebooted and it comes up beautifully..  the only issue is that it only gives me the option for ubuntu.   I am guessing it is because I have Windows installed on a different hard-disk..  but I don't know how to tell it to direct there (or if it is even possible).

If anyone can offer any guidance I'd be very grateful  :)


Libs

---

### Post by libspero on 2012-04-25
shameless bump.

I discovered the BERG (grub) customizer tool..  but this doesn't seem to provide an obvious solution.

Should Berg be detecting it automatically even if in a separate HD,  or am I just missing something obvious :???:

---

### Post by rk0r on 2012-04-25
Hi 

Install GRUB customiser 

sudo apt-get install grub-customizer


This may work.

---

### Post by libspero on 2012-04-25
Hi rk0r,

Installed that and ran it..  don't know how to do a screen dump in Ubuntu yet but basically there is no reference to other drives in it (as far as I can see) or any obvious way to tell it where to look for other operating systems.

At the moment I can sort of dual boot by manually going into the bios each time I want to boot Ubuntu and telling it which disk to boot from..  but there's got to be an easier way than that!

---

### Post by rk0r on 2012-04-25
Check this 

[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_From_A_Second_Hard_Disk](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_From_A_Second_Hard_Disk)

it may help grub recognise there is a second disk.

Let us know how it goes.

---

### Post by libspero on 2012-04-26
Hi rk0r,

Thanks for that..  found "Super Grub2 Disk" and burned the iso to a DVD.

From Bios I booted to the DVD and it started "Super Grub2"

I got the list:

Detect any OS
Detect any Grub2 
etc...

So I selected "detect any OS"..   all I got was the message:

"Error: unrecognised fs."
"Error: unrecognised fs."
"Error: unrecognised fs."
"Error: unrecognised fs."

Then nothing..

Is it because I'm running BURG not just Grub2?   

**bangs head against wall**

---

### Post by libspero on 2012-04-26
Ok I was a little impatient.

"Super Grub2" when left long enough does provide a list of OSs..  but all four it found were variations on the Ubuntu I've just installed.  No sign of Windows.

I'm wondering whether the fact it is giving me an "unrecognised FS." message is part of the reason it can't find windows though.

Also,  just tried to boot direct from the "windows drive" and discovered that BURG has taken it over as well  (I thought I only installed it on the "Linux drive").  So now I can't boot windows at all..  both disks direct to Ubuntu!  Help!

---

### Post by libspero on 2012-04-26
Managed to work out how to do a screen dump in Ubuntu :)

This shows the results of Fdisk


[IMG]http://img62.imageshack.us/img62/4536/snapshot1bv.jpg[/IMG]

Does this shine any light on the situation?  It appears to find both disks ok :?

---

### Post by libspero on 2012-04-26
Last bump just in case anyone knows.

I'm amazed more people haven't encontered this!

---

### Post by libspero on 2012-04-26
Finally solved it.

Thanks rk0r for your help..  what an effort that was!

---

### Post by ElEdwards on 2012-04-26
Please post the solution :)

---

### Post by rk0r on 2012-04-26
> **libspero said:**
> Finally solved it.

Thanks rk0r for your help..  what an effort that was!

How did you fix it after ?  :)

---

### Post by libspero on 2012-04-26
Well..  it's not a great solution but I was getting fed up of tweaking around the edges.

Essentially I backed up all my data,  put my windows disk in and reinstalled windows on the first disk.  This gave me the option to delete all of the partitions on all of my disks and start from scratch.

So I did.

I then did a fresh install of Ubuntu on the second drive,  and being a bit of a masochist I tried installing BURG again.

Second time it worked straight off the bat and automatically detected both operating systems with no issues.

I don't really understand what was different,  which is why I didn't originally post a solution as it wouldn't have been much help to anyone else.

I suspect it was just the way the partitions were arranged on my original windows installation that caused it to throw a wobbly.  It seems it's one of those things that either works perfectly,  or perfectly *****s everything up.

Happy now though..  BURG looks great on boot up and both Ubuntu and Windows boot perfectly from their respective drives.

I'm going to celebrate with a well deserved beer :)

---

### Post by rk0r on 2012-04-26
Sounds like the best method there..
Glad you got it sorted out!

I am going to have a task shortly of installing some OS on different drives, i was thinking of using ESXI to manage all the OS...

[http://ubuntuforums.org/showthread.php?p=11876387#post11876387](http://ubuntuforums.org/showthread.php?p=11876387#post11876387)

:P fun times!

---

### Post by dcstar on 2012-04-27
> **libspero said:**
> Well..  it's not a great solution but I was getting fed up of tweaking around the edges.

Essentially I backed up all my data,  put my windows disk in and reinstalled windows on the first disk.  This gave me the option to delete all of the partitions on all of my disks and start from scratch.
........

And let me guess - Windows is now **not** on a GPT partition?

---

### Post by libspero on 2012-04-27
> **dcstar said:**
> And let me guess - Windows is now **not** on a GPT partition?

I have no idea (what one of those is or why BURG can't handle them or why no one knows how to fix the issue)..  nor frankly do I care right now.

Everything is working fine and I'll be waiting another couple of months before I try breaking things again :)

---

### Post by Papex on 2012-04-28
> **libspero said:**
> Hi guys,

Just installed Precise 12.04 and have to say it is great..  no problems at all with installation.  Just works.  Period.

Soo...   I've set about trying to break it :D

The first thing I wanted to do was install BURG so I could dual boot into either Ubuntu or **cough**  [SIZE="1"]windows[/SIZE].

I found and installed it with Terminal no problem thanks to an online guide.
Rebooted and it comes up beautifully..  the only issue is that it only gives me the option for ubuntu.   I am guessing it is because I have Windows installed on a different hard-disk..  but I don't know how to tell it to direct there (or if it is even possible).

If anyone can offer any guidance I'd be very grateful  :)


Libs

Hey libspero,
Where did you find that online guide for installing BURG on 12.04 in the first place. I'm considering doing it also but must confess I'm a bit uncertain about the hole thing in the first place (eventhough I've only got two OS on one harddrive.) 
The only guide I could find was for older versions of Ubuntu.

---

### Post by libspero on 2012-05-02
> **Papex said:**
> Hey libspero,
Where did you find that online guide for installing BURG on 12.04 in the first place. I'm considering doing it also but must confess I'm a bit uncertain about the hole thing in the first place (eventhough I've only got two OS on one harddrive.) 
The only guide I could find was for older versions of Ubuntu.

Hi Papex..  sorry,  I've not visited recently to see your question.

You've probably found the answer yourself by now..   I'm not sure if this is the exact page I used,  but if not the instructions look pretty much identical to the ones I followed.

[http://www.unixmen.com/how-to-install-burg-in-ubuntu/](http://www.unixmen.com/how-to-install-burg-in-ubuntu/)

Good luck..  it works really well when it works (and looks great),  just be prepared to wipe everything and start from scratch if it doesn't!

---

