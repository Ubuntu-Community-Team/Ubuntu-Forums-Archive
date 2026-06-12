---
title: "I hate GRUB...Help me, please."
date: 2006-04-17
forum: General Help
---

### Post by Newb Noob on 2006-04-17
I just got this computer last night. I didn't reboot it until I shut it down, and slapped another harddrive out of a computer with Windows XP in it. It started booting up, acting like its' fine, but it tells me there's no Primary/secondary master/slave drives, and then it goes to loading GRUB, and I get an error seventeen. I tried entering the BIOS while it was booting, but it would refuse to do that, and just keep booting up until the error. I couldn't enter the settings, either. I didn't set the partitions or anything for this computer, I bought it from one of my friends, and he's the one that set it all up. I'd get help from him, but he's in class right now. Anybody want to help me? Please?
And after I booted it up when I put the new harddrive in it, it went through a bunch of stuff, I assume it was for the harddrive, but I don't know. When I got the error 17 with that harddrive hooked up, I unhooked it and still got the same error.

And I DON'T have Windows on that computer. Only Ubuntu.

---

### Post by presentt on 2006-04-17
Error 17 means GRUB cannot mount the selected partition.  If inserting your second HDD caused the problem (did it boot correctly before placing the drive in?), then GRUB may be getting confused over which partition contains the boot information, because it isn't sure which drive it is on.

Seeing as you just got the computer from a friend yesterday, I'd take the cheap/lazy/no-brainer way out and reformat the entire thing as ext3 and reinstall the newest version of Ubuntu.  Because the problem seems to be with the bootloader, maybe you can retrieve any information you need off of the computer using a LiveCD distro before formatting--this shouldn't be damaged.

Otherwise, try searching [Google]("http://www.google.com") for something like "GRUB error 17."  I didn't read any of the results, but I'm sure someone has had a similar problem.

---

### Post by Newb Noob on 2006-04-19
Okay, I got the LiveCD working, but the instructions on [this](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub) site, don't work.  It says to type "grub" in the terminal, but it says "command not found" after that.  Help?

---

### Post by Newb Noob on 2006-04-19
I thought I was supposed to get help from this so-called forum called "support".

---

### Post by presentt on 2006-04-19
Hmm, I'm not sure why grub wouldn't load from the LiveCD (I assume it's the Ubuntu LiveCD).  Are you running it as a SuperUser?  Make sure you type:
```
sudo grub
``` 
Otherwise, I'm not sure what to do.  If all else fails, try using the LiveCD to backup any important data, and reformat the entire machine with a clean install.  Before that course of action is taken, however, does anybody else have an idea?  I'm not particularly familiar with GRUB; I troubleshooted it when I needed to install Ubuntu, but nearly to this extent.

[quote=Newb Noob]I thought I was supposed to get help from this so-called forum called "support".[/quote] Yes, you are, but everybody does this on a volunteer basis and cannot always drop what they are doing to help out.  It probably isn't too much to ask to wait at least a day before pushing the thread along.  I've found the Ubuntu community, and most forums and USENET groups, extremely willing to help out, as long as you give people time to think about your problem and post a response.

Good luck.  Post back if you find a solution.

---

### Post by Newb Noob on 2006-04-19
Command not found, again.  Grrr.


And sorry about my impatience, I'm used to getting much faster responses on, apparently, much larger forums.

---

### Post by presentt on 2006-04-19
When I searched for "error 17" on these forums, I found you posted the same message in two other places.  Perhaps keep it to one thread so others know what path the conversation has taken.

A plausible suggestion in [**this**]("http://ubuntuforums.org/showthread.php?t=161736") thread was to check if
[quote=localzuk]all power cables plugged in correctly, similarly, are all ide cables plugged in at both ends[/quote] 
Otherwise, I'm stumped, anyone else?  It looks to me like there is some major corruption, but I don't know why the LiveCD wouldn't work.  Try the LiveCD in another machine to see if it is the 'puter or the disc.   Good luck.

---

### Post by Newb Noob on 2006-04-19
Eh?  The LiveCD works, but the GRUB command doesn't.  And I can't really use it on a different machine, unless I could use it on this one, that only has XP on it.

EDIT:  I tried "apt-get install grub" and some other commands that I forgot already, and they didn't work, so I downloaded the install cd.  We'll see how that goes when I get back tonight.

---

### Post by Newb Noob on 2006-04-19
Yeah, um, I tried the Install CD method, and it didn't work. When I went to rescue mode, and it asked me which device to mount as my root file system, I selected one, and it said it couldn't mount it.  This computer is seriously messed up.

---

### Post by Leopard on 2006-04-27
Have you tried physically removing the hard drive that was added?

---

