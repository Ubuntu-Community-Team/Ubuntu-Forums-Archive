---
title: "Ubuntu is using resources, but for what?"
date: 2011-10-21
forum: General Help
---

### Post by mastablasta on 2011-10-21
Ubuntu 10.04 LTS, fully updated. 
 
Computer keeps doing something, some process but i don't know what in order to stop it (if at all possible).
 
Ok System specs are 
Athlon4 1,2Ghz, 
224 MB RAM (the rest is reserved for graphics card), 
20 Gb hard disk with little over 11 GB free space.
 
Using lighter theme and less desktops and few other tricks (eg. no background image) there is plenty of RAM left for runnign a few basic programmes.
 
Now on to the problem - computer is slow, but it wasn't used to be so slow. System monitor as well as top command show there is still ram left after i turn on FF and Skype. System monitor is even showing CPU as being used only about 40-60%. simialr situation in top command.
 
However disk is constantly working. and the whole thing slows down to a crawl. it came to this that even when i only launch Cromium it can't even display Google.com. It used to work well before. it is obvious to me that something is running in background that is bringing down the OS. but how to find out what that is? i tried turning off the programmes leaving just desktop open and it kept on doing something. Again system monitor doesn't show any activity and shows over 100MB ram free. but when i move the mouse (via pad) it doesn't move smoothly as it should.
 
 
I've tried XFCE before and at first it was working faster than Gnome, however after some time it was slow. and now that i think about it it was same thing. doing something in background even when nothing is on. I though it was due to XFCE (it wasn't optimised in that version) so i removed it. then i though it is because of wifi PCMCIA card, bu tnow i was connected only via wire (no card). what is going on with this LTS? Used to be super stable and much faster on this maschine than XP?

---

### Post by crazy bird on 2011-10-21
Open a terminal and type this command: **top**. Make sure you maximize your terminal.
Make a sreenshot of the output of this command and post it here.

---

### Post by mastablasta on 2011-10-21
OK here we go.

nothing running: 
[http://ubuntuone.com/50rwoIX6czIDwuzNiQYhBJ](http://ubuntuone.com/50rwoIX6czIDwuzNiQYhBJ)

added chromium, ups google news crashed (apparently not enough memorry or something like that): 
[http://ubuntuone.com/5R0vcBeNRwKiZQV04hGrUF](http://ubuntuone.com/5R0vcBeNRwKiZQV04hGrUF)

added skype and firefox (instead of chromium): 
[http://ubuntuone.com/5ev1wpNuAjGYJ5J3TpmEnT](http://ubuntuone.com/5ev1wpNuAjGYJ5J3TpmEnT)

system monitor google news in FF+ skype: 
[http://ubuntuone.com/3FzAcYzr3xQSvKXZMkJeoi](http://ubuntuone.com/3FzAcYzr3xQSvKXZMkJeoi)

added tab in FF: [http://ubuntuone.com/5jxjfawjsGpMbph7Q91klu](http://ubuntuone.com/5jxjfawjsGpMbph7Q91klu)

everything off again: [http://ubuntuone.com/3E6Jt9BDQpIWfwv2jvMOdI](http://ubuntuone.com/3E6Jt9BDQpIWfwv2jvMOdI)

another take with chromium and skype this time with gkrelm monitor: 
[http://ubuntuone.com/6JWlncKTtiDsFXI95UnJDa](http://ubuntuone.com/6JWlncKTtiDsFXI95UnJDa)
 
Skype alone with gkrelm: [http://ubuntuone.com/0NdFkEF9J7PjcPARXRb0mI](http://ubuntuone.com/0NdFkEF9J7PjcPARXRb0mI)

Everythign off with gkrelm monitor: [http://ubuntuone.com/6L8VyklZH4WfXVnOQ855uV](http://ubuntuone.com/6L8VyklZH4WfXVnOQ855uV)

The disk wokring again and then suddenly update manager decided it might be a good idea to launch. but i clicked close and after some time (a couple minutes passed) something was still running on the disk so i went to terminal to do the top thing again:
[http://ubuntuone.com/3Tuv676Lrnv4cbyjPYnU91](http://ubuntuone.com/3Tuv676Lrnv4cbyjPYnU91)

i restarted the computer, re-run the update manager (no packages updated) and it seem after some time it went back to like the first "top" picture.


HEre is what i dont' understand why this computer sometimes works relatively fast (considering th4 ram and CPU) while other times you can't do anything on it and the disk light keeps going on and off like it's doing somehthing. or sometimes it is on for some time.

---

### Post by K4NEB on 2011-10-21
mine is doing the same, one minute its like lightening next it falls a sleep or something 

i updated to 10.11  from 10.04 

10.04 was fine for me but since i updated im getting exactly the same symptoms :(

---

### Post by Gyokuro on 2011-10-21
Hi,

looking at your numbers I can see that you are using swap space. That indicates that your system has too few RAM to keep everything in memory and is swapping apps to your HD which make your system slow. The LTS release is fine but you have to use a much leaner window manager as the current one (Gnome is memory hungry), XFCE is small but you can safe more memory if you use a leaner window manager like wm2, firefox is using also some amount of memory, try dillo or use a distro which is tailored for small systems (Lubuntu) but the easiest task would be to get more RAM.

@K4NEB: how much RAM is in your system, in case your system is swapping to disk it indicates that you have to few RAM

---

### Post by mastablasta on 2011-10-21
i know more ram would be best, but firstly it is not sensible (for such an old computer) and secondly even if i could find and buy this ram it can only upgrade to 384 MB (i wonder who the idiot that designed this computer was as it originaly ran WinXP).

i've tried chrunchbang and it seems to run fine. new lubuntu doens't even boot without boot manager. while XFCE (10.04) didn't work out as it had same symptoms. one minute it is workign fine the next it has issues and slow. what i mean by this is that soemtimes it all works well i can surf the web normally, watch a movie... but sometimes it acts like this - slugginsh. The chromium issue for example was never there before. it started just recently.

what i wonder is if i am not doing anything on it why does it work with swap then? surely it can hold it all in memorry. also why would LiveCd work well (ok it loads it all in RAM) but why doesn't the installed ubuntu do the same if there is free ram available? i mean why use disk if there is free ram? 

all liveCDs that i could try work well. for example Debian (and Chrunchbang), Xubuntu and Lubuntu (if i get to boot them with boot manager on floppy), mint LXDE was a bit slow. But that's about the only one that gave me issues in live mode.

---

### Post by Gyokuro on 2011-10-21
> **mastablasta said:**
> i know more ram would be best, but firstly it is not sensible (for such an old computer) and secondly even if i could find and buy this ram it can only upgrade to 384 MB (i wonder who the idiot that designed this computer was as it originaly ran WinXP).

i've tried chrunchbang and it seems to run fine. new lubuntu doens't even boot without boot manager. while XFCE (10.04) didn't work out as it had same symptoms. one minute it is workign fine the next it has issues and slow. what i mean by this is that soemtimes it all works well i can surf the web normally, watch a movie... but sometimes it acts like this - slugginsh. The chromium issue for example was never there before. it started just recently.

what i wonder is if i am not doing anything on it why does it work with swap then? surely it can hold it all in memorry. also why would LiveCd work well (ok it loads it all in RAM) but why doesn't the installed ubuntu do the same if there is free ram available? i mean why use disk if there is free ram? 

all liveCDs that i could try work well. for example Debian (and Chrunchbang), Xubuntu and Lubuntu (if i get to boot them with boot manager on floppy), mint LXDE was a bit slow. But that's about the only one that gave me issues in live mode.

Ok - you can try following when this symptoms occur:

in a terminal enter following (you have to install sysstat in case you haven't: sudo apt-get install sysstat)

iostat -dkx 60

and

ps -A --sort -rss -o comm,pmem  | head -n 11

and please post the output or watch the system monitor if you find the commands to complicated. 

Well a LiveCD will oops after some time in case you do not have any free memory available and the kernel begins to kick out apps of the memory. On an installed system the kernel will swap (that the process which make your system acting slow; memory get written out of your RAM on your HD) as long you have memory + swap space available, after that the kernel kicks in again and begin to kill apps to gain memory back. So you can try to play around with some kernel knobs so that the system swaps earlier or later and the kernel knob is called swappiness which you can check via:

cat /proc/sys/vm/swappiness

and you will see a number and now try to lower it so you can work without problems:

sudo sysctl vm.swappiness=10

which is a temporary change. If you found a value where you can work as expected you have to save this value in /etc/sysctl.conf

vm.swappiness=10

save the file and reboot. I think Ubuntu have somewhere a FAQ about Swap in general but I think I have mentioned most to get a usable system back.

-HTH

---

### Post by K4NEB on 2011-10-22
@K4NEB: how much RAM is in your system, in case your system is swapping to disk it indicates that you have to few RAM[/QUOTE]


if by RAM you mean memory i have 1.7gb  its using about 500mb with firefox, htop and system moniter open

and 0mb of 1.7gb swap

yet everything is still sluggish

---

### Post by mastablasta on 2011-10-23
This is what computer gave out:
```
iostat -dkx 60
Linux 2.6.32-34-generic (tatie-laptop)     23/10/11     _i686_    (1 CPU)

Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda              86.97    79.26   74.84   14.83  1597.43   376.45    44.03    13.38  149.26   9.07  81.35

ps -A --sort -rss -o comm,pmem | head -n 11
Device:         rrqm/s   wrqm/s     r/s     w/s    rkB/s    wkB/s avgrq-sz avgqu-sz   await  svctm  %util
sda             111.56    46.57  132.97   27.36  1169.45   295.75    18.28    10.97   68.46   5.69  91.21

```
i am not sure what they mean. :)

---

### Post by mastablasta on 2011-10-26
Time for a BUMP!!!!

---

