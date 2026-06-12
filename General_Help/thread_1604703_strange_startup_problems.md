---
title: "strange startup problems"
date: 2010-10-24
forum: General Help
---

### Post by eeyoreinthesky on 2010-10-24
This is my first post. Not because I'm new but because I haven't been able to find another post with exactly what's going on with my computer. So I'd like to thank the community for all the help in the past. 
 
A few days ago I was playing Cube 2:Sauerbraten and getting around 200 FPS. During the middle of the game the monitor went black and stayed black. The computer stayed on though. And I really don't think it was taxing the machine at all on account of the FPS. And I've checked the CPU temps before this happened but they were only at about 55 degrees. All the fans were/are working properly. 
 
So now when I try to start my computer it will freeze at completely random points. It always makes it past the BIOS screen. A few times I've been able to log-in. One time Conky loaded and everything looked normal. One time a window appeared that said:
 
There is a problem with the configuration server. (usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 9)
 
More than once I've seen "fixing recursive fault but reboot is needed." 
 
I can open the BIOS setup and look at stuff in there. In fact, I tried loading the OS from the Live CD. It was recognized but stayed on the purple screen with the white UBUNTU and the red dots. I think I left it for at least 2 hours. Nothing. 
 
Lastly, this is a pretty new system. I built it a few weeks ago. I'm hesitant to believe the problem could stem from an error when I was building it since everything was running great. 
 
Any help would be greatly appreciated, thanks!

---

### Post by ajgreeny on 2010-10-24
Can you get to recovery mode from the grub menu?  If you can it points to a user problem, or at least a gnome configuration problem of some sort.

Try renaming the /home/user/.gconf folder when in recovery mode, as a backup, with ```
mv /home/user/.gconf /home/user/.gconfbackup
``` and then try loging in again.  If that is successful, you will need to rebuild your gconf configuration again, but that is not usually too much trouble.

If that is not any help, then I would guess hardware in some way being implicated.  Start by running a memtest86+ from grub.

---

### Post by eeyoreinthesky on 2010-10-24
I wasn't able to pull up the GRUB menu. And I'm not sure why. After several tries though I was able to get to the log in screen and log in under the GNOME failsafe mode. When I tried to start the Terminal it initialized but never opened. I logged out and logged back in using xterm. I renamed the folder but still have the same problems. 
 
I'll try to find a way to do the memtest now. 
 
Thank you very much for the help though. I really really appreciate it!

---

### Post by efflandt on 2010-10-24
Try running memtest86+ for a few hours or overnight.  Although, you might try first removing and reseating you video card and memory chips to make sure that everything is making good contact.

Sometimes memory is almost compatible with a new type of cpu, but not quite.  That happened with a home PC when I upgraded RAM on what was then new early Athlon64 3200+ (OCZ exchanged it for memory that worked).  We also had rare BSOD's with a P4 work PC with Crucial RAM that I did not even test until the PC was being retired (memtest85+ found errors on that PC, but that RAM works fine in another PC).

Sometimes an overrated power supply (PSU) with what seems like enough wattage rating may not have enough current in the voltages you need.  That happened with that same Athlon64 PC when I upgraded its video card.  After I upgraded its psu I discovered it was only using half the power at the wall outlet of the watt rating of the HP OEM psu (which would not even boot it with that video card).

---

### Post by ajgreeny on 2010-10-25
To get to your grub menu you should hold shift when you start the computer.

It was Esc for legacy grub, and the change has confused many users.

---

### Post by eeyoreinthesky on 2010-10-25
Well that explains why I couldn't get to the grub menu.  In other news, I have tried memtest86+.  I have two sticks of 2GB OCZ RAM.  The first ran for almost 5 hours and passed 12 with no errors.  I tested the second stick all last night and it passed 21 times with no errors.  I've tested the two together and in the past three hours they've passed 4 times with no errors.  
 
I'm happy and sad at the same time.  After reading the symptoms of incompatible memory it sounded like that might be the problem.  Unfortunately, no.  
 
I'm going to triple check all the connections and try the Live CD again.  
 
Do you guys have any other ideas?  Could this be a glitch from a recent update?  I hate to think it could be a virus.  Please tell me I'm crazy.

---

### Post by ajgreeny on 2010-10-26
OK, here goes,

You're crazy!!

Good enough?  To be serious, I don't think there is any way it can be a virus as there are none in the wild for linux.  I would stick with the idea of checking and double checking all connections by disconnecting everything one by one then reconnecting them all.

Other than that I can not really help you with any other ideas.

---

### Post by eeyoreinthesky on 2010-10-26
Alright, I return with good news.  After doing the memtest I took out the CD and let the computer boot normally.  It worked and has been working since.  

The wallpaper is the default wallpaper and the theme is the default though.  I'm guessing that is totally normal for changing the configuration file.  

My last question, is it safe to go back to the old configuration or should I just start over again from scratch?  

The virus thing (I knew I was crazy), the support thing, the somewhat easy fix. All reasons I love this OS.  Thanks guys!

---

