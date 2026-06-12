---
title: "Monitor problems"
date: 2010-08-17
forum: General Help
---

### Post by GBJoker on 2010-08-17
I have recently upgraded to version 10.04, and it was working well until last night.  I had deleted several megabytes worth of random pictures and word documents that I never use anymore to clean up my computer, and then ran Ubuntu's Janitor thingy.  After that, I was just looking around to see what else my Ubuntu could do (since I'm still relatively new to it.), and did I believe some sort of computer test thing or something like that.  When it tested what resolutions my computer and monitor could handle, it got through all of them, but right before I could hit the "Next" button, my screen went black.  I couldn't do anything, and ended up manually restarting the computer.  After restarting several times, I found that whenever I login with either the "GNOME" or "failsafe-gnome" settings, I get the same thing, of the computer running, but the monitor going into suspension mode that does not go away with anything I do.
I put in  my PuppyLinux cd so I could surf the internet for answers and found only a few things that related to my problem.  Upon testing various solutions, I found when I logged in, monitor suspends, but hitting "Ctrl-Alt-F1" I get into a sort of terminal area where I log in again and can do any coding I need to do.  When I login there, it gives me a message saying that I'm missing certain security features in "/usr/bin/check-bios-nx --verbose".  When I go to that file it tells me that it can't recognize anything about my computer at all and that I don't have NX activated in the file "/proc/cpuinfo".  When I go to that file, it won't let me modify it all, but is able to determine all the information about my computer the first file doesn't see.
Is there anything I can do about this?  I'm seriously debating just reinstalling Ubuntu all over again.  Thanks in advance.

EDIT:  My dad was able to do some research while he was at work and found that my most likely problem was the Janitor deleting some of my files... I didn't see what files it got rid of, so should I go ahead and reinstall Ubuntu and delete my whole drive?

---

### Post by realzippy on 2010-08-18
Welcome to the forum!
Honestly,a fresh install is done in 30 minutes...solving your problem
is not done in this time.Backup some files can be done with your puppy or ubuntu liveCD.

Unfortunately you not seem to be the only victim of this janitor tool...
use it with care or,better:
uninstall it.   ;-)

---

### Post by michaelg81 on 2010-08-18
I'm also having a boot problem and have used a 10.04 Live CD to boot. It worked like a charm. I just had to make sure to put the CD in the first drive in the (IDE?) chain and to configure the boot sequence to look at the CD for a boot system (F2 or F12 in the upper left of the computer's startup screen, I don't remember which). 

What's the best way to  backup the home folder on the old installation before wiping it out?

I have several applications that I installed from downloads (vs. Synaptic), one of which is my e-mail in Thunderbird. I want to be able to migrate my entire home folder to the fresh install and have the file permissions and executables all work.

Hope that is some help.

Michael

---

### Post by michaelg81 on 2010-08-18
I'm also having a boot problem and have used a 10.04 Live CD to boot. It worked like a charm. I just had to make sure to put the CD in the first drive in the (IDE?) chain and to configure the boot sequence to look at the CD for a boot system (F2 or F12 in the upper left of the computer's startup screen, I don't remember which). 

What's the best way to  backup and restore the home folder on the old installation before wiping it out? 

I have several applications that I installed from downloads (vs. Synaptic), one of which is my e-mail in Thunderbird. I want to be able to migrate my entire home folder to the fresh install and have the file permissions and executables all work.

Hope that is some help.

Michael

---

