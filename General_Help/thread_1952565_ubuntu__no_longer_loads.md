---
title: "ubuntu  no longer loads"
date: 2012-04-04
forum: General Help
---

### Post by aoniumo on 2012-04-04
Ok.  So I woke up this morning and turned on my pc. I got as far us the option whether I want regular session or recovery mode.  I do nothing since the regular session is autoselected and will load.

Imagine my surprise when nothing --- I mean nothing --- happens.  The screen is BLANK.  the log on screen doesn't even load.  So I press the power button and do the same thing and still nothing.  Presss the power button again and select rd overt mode, still nothing.  Tried it again, and nothing.

I don't have a cd.  My cd installation is a mounted image, so I can't access that either.  I'm very unhappy and frustrated right now since I can't do my work and I'm using my smart phone to post this thread and it's not very convenient.


Any help will be appreciated.  Thank you.

---

### Post by houseworkshy on 2012-04-04
The first thing to do is find out if you have a hardware or software  problem.  So try to get your hands on a distro, almost any compatable  distro, could be a freshly burned Ubuntu but doesn't have to be.   You  may be better with things that are designed to run from the cd/rather  than be installed.  Two stand out for that;  Knoppix is a full DVD but  has most popular drivers on the disk. Puppy linux is splended for being  tiny but functional.  Whichever you choose ( or can get hold of ) boot  up with it.  If they work you have a software problem, if not most likey  it's hardware problem.  I you can't borrow a friends internet then  browse around pc magazines, they are often given away as cover disks.   If you can wait a little longer you can also send of through the post.   As to your work there is a good chance that it is safe ( as long as you  don't overwrite it ).  Remember that it will be invisible to windows so  use a linux distro to find it.  When I was using vista it often went  wrong and I'd boot up with  a Knoppix CD, and use it to copy my work to a  flashstick before reinsallations.  Puppy is so small that one can boot  from it, eject the disk, the whole op runs in ram and includes a  burner.  I'm aware that this isn't exactly push this button to fix type  advice but this question has been unanswered for a while and it sounds  serious so I thought " solve it I can't but bump it I can." Good luck  and don't go formating unless you know you have too, quite likely your  work is still there.

---

### Post by houseworkshy on 2012-04-04
As your on a phone I'd do what should be an edit of the above as a seperate bit.  [http://www.slitaz.org/en/](http://www.slitaz.org/en/)  is a very tiny just enough OS ( it has a GUI, which is impressive for it's size ) which you could get via your phone ( It's only 30MB ).  You will probably have to use another PC at some stage to burn cd/dvd's, stage one may be organising that, friends, library, internet cafe etc etc.  Puppy linux is designed to go on flash sticks too so go with that one if you macine doesn't have a cd/dvd drive but does have a usb.  Also clarify what you mean by "mounted image" which could mean several things, virtualised etc so the experts, if they turn up, can diagnose better.  Should it turn out to be hardware  remember that hard drives can be mounted in other machines, jot down passwords etc in case it is some time away.  If nothing soon best inform client/boss/educator before any deadlines are crossed.  Good luck .

---

### Post by aoniumo on 2012-04-04
Recovery mode was able to load and I was able to select the first three  options - dpkg (Repair broken packages), fsck(File System check), and  grub (update grub bootloader) .  I have to do all three every single  time, so I'm not sure which one is making it work.  Afterwards, it  finishes all three (there's no restart) it would give me another menu  and at the top is normal mode or boot.  I selected normal boot and I'm  able to get to the login screen.

I shut down and select normal and problem is there again.  Power button  press and go through the steps in the recovery menu and it works.  What  is wrong with this?  After spending a whole day, I am considering  throwing away the whole thing.

---

### Post by holycow131415 on 2012-04-04
When  you are able to get in, try checking for updates in the update manager and install them.

If that isnt it, when you are in grub, try selecting an earlier kernel to see if your problem still happens.

---

### Post by aoniumo on 2012-04-04
> **holycow131415 said:**
> When  you are able to get in, try checking for updates in the update manager and install them.

If that isnt it, when you are in grub, try selecting an earlier kernel to see if your problem still happens.

Thank you anyway.
Yes, I installed whatever updates are there and restarted.  That's how I found out it didn't fix itself.

In addition, I thought it would be better to put the pc in suspended state instead of shutting down, but it cannot resume from suspended state same blank screen - no login screen visible.

Edit: I'll try take a video with my phone tomorrow and post.  For now, I am tired.

---

### Post by aoniumo on 2012-04-05
I'm fine with pressing the power button 5 times for now since the appearance of the login screen is hit or miss.  It might just fix itself.  If not, 12.04 is just around the corner.

---

### Post by houseworkshy on 2012-04-08
Which will be an LTS too, this time with five years support :) . I'll be installing that too if I can bung gnome on it.  There's usually a teething period which doesn't matter as the 10.04 has a year  of support left, which is another option if 12.04 starts out too buggy for busy people to make time for OS fiddling.

---

