---
title: "frequent system freezes after update 11.10"
date: 2011-10-15
forum: General Help
---

### Post by dlee2654 on 2011-10-15
hello, I have seen some reports about this but so far no resolutions.  ever since updating to 11.10 I have had very frequent freezing of my system.  the only thing I can say I was doing at the time is web browsing in firefox and it almost always happens while in the midst of moving mouse.  the first few times it happened it appeared I still had some control and could use keyboard shortcuts to reboot.  Now it seems when it happens the system totally freezes up and I can do nothing other than to hold the power button down.  I would think this is some kind of graphics glitch but I dont know where to start.  I have a HP nc6400
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
when I look at the driver under system info, it shows up as 'unknown'.  this has been the case even when running 11.04.  graphics still look really good and very responsive.  I have found that if I boot into Ubuntu 2D it seems to happen less frequently but its still happening.  if I stay out of firefox it happens even less.  still quite frustrating to power down half dozen times a night while working.  Has anyone found a fix or work around to keep this from happening?
thanks.

---

### Post by mörgæs on 2011-10-16
Have you thought of a fresh install? There is a link below explaining how.

---

### Post by dlee2654 on 2011-10-16
I am considering it, but I have discovered today that if I don't use Firefox it doesn't happen very much at all.  I have used Opera all day today and I don't think its frozen once for me even once.  so I am thinking its a Firefox problem but not positive.  I'm going to stick it out for a while and wait on a few updates.  A reload would be a real hassle on this laptop for some reason the wireless was difficult to get going.  
thanks for the reply!:popcorn:

---

### Post by Mouldy97 on 2011-10-18
Hi  I have exactly the same problem on an nc6400.  It seems to be worse on battery rather than AC.  As you mentioned I noticed most of the freezes seemed to be within Firefox, I've tried chromium and it is exactly the same.  I've read a few posts suggesting the problem may be with the Broadcom wireless driver.  I've tried a complete reinstall and up to now only been using a LAN connection and so far no lockups.  The lack of wireless is not entirely through choice I'm new to Linux and struggled to get the wireless working initaly.  I now can't find the post that originaly worked.  Are you able to point me in the right direction?  Have you experienced any lockups in Opera?

---

### Post by dlee2654 on 2011-10-21
Actually I have pretty much confirmed that my freezups are increased with firefox use.  In Opera I can go a few days without freezing (but it eventually happens).  in firefix I might only be in for 10 minutes and I will get frozen.  the first thing I notice is the little busy indicator starts happening on the mouse cursor, but I can still move the mouse.  I try to do things like alt-tab or ctrl-alt-f1 but no go.  it then completely freezes even the mouse and all I can do is hit the power button.  I have not tried to do a complete re-install I was holding out for updates that might fix but after 200+ updates the problem still exists.  In my case I had a major time getting wireless working as well.  this is one of the main reasons I don't do the fresh install.  if you have the non-free (proprietary) wireless drivers they are the problem.  Just use the free ones that come with Ubuntu.  I remember my wireless working after removing these.  I might try a fresh install over the weekend but as long as it works with Opera, I'm not all that concerned.  I can deal with a lockup every few days.:D

---

### Post by dlee2654 on 2011-10-27
just an update: probably wont bother with this anymore but I ventured a fresh install last night and problem did not resolve.  As a matter of fact I think it made the freezes happen even more frequently than before.  it now freezes in Opera at about the same rate as it did with Firefox.  It happens a little less in Ubuntu 2D but still happens.  I'm probably going to back rev to version 10.  I really liked 11.10 it fixed the mouse offset problem I was having in 11.04. At this point I doubt it has anything to do with any packages I have installed since this is a plain vanilla install of ubuntu.  Thanks to those who tried to help, it was appreciated.

---

### Post by mörgæs on 2011-10-27
Have you tried Xubuntu?

---

### Post by mbn18 on 2011-10-31
After I upgrade my Ubuntu from 11.04 to 11.10 I had the following issue.
[LIST]
[*]My upgrade Ubuntu 11.10 kept freezing randomly.
[*]Had long delays while booting.
[*]Shutdown kept freezing from time to time
[/LIST]

I have no idea why. I explored the forum and net with no luck and the syslog was not useful in discovering the cause. My hardware is quite decent. Intel 930 I7 and gigabyte MB + 8GB RAM.

I did solved the problem by installing the server kernel
```
sudo apt-get install linux-image-3.0.0-12-server linux-headers-3.0.0-12-server
```

Now its the second day without any freeze. The boot still has long delays, though I can live with it.

Hopes it helps :D

---

### Post by fleamour on 2011-12-14
> **mörgæs said:**
> Have you tried Xubuntu?

Xubuntu 11.10 upgrade, same problem.  Xubuntu fresh install, same problem.



:confused: :( :confused:

---

### Post by mörgæs on 2011-12-15
Fleamour, your posts are very brief. 

Help people to help you: Please begin with a detailed description of the problem and the hardware used. 

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by fleamour on 2011-12-15
Soz:

[http://www.thinkwiki.org/wiki/Category:T21](http://www.thinkwiki.org/wiki/Category:T21)


The problem being:

Random freeze where the mouse pointer will disappear & no HDD activity.  Caps Lock/Num Lock will not respond.  (I have yet to try Alt+SysRq+K to log in again.)

Can give sudo lshw output if requested.

EDIT: Tooooo...many...bugz.  Switching back to LTS.

---

### Post by ZootHornRollo on 2011-12-16
I have had very similar issues with my NC6400 since switching to 11.10.  Have tried both 32 and 64 bit flavours of Ubuntu, upgrade install and fresh installs, still get the issues.  

I'd echo the thought that firefox increases lock up and have been using chromium with slightly reduced no. of lock ups but still very annoying.  Will try opera after trying the server kernal suggested earlier - an update from mbn18 would be good?

Have run earlier versions of OpenSuse 12.1 and Fedora 16 with no isses at all...  but i like ubuntu so would prefer to get that fixed!

---

### Post by Barpfotenbaer on 2011-12-21
After updating from Xubuntu 11.04 to 11.10 yesterday I had up to 10 freezes of my xfce-system. I was still able  to log in via ssh and to reboot the system cleanly. But prior I always took a look to the process list (top) and discovered, that "tumblerd" was always eating up the resources, e.g. a CPU-load of 100%.

After removing the tumbler-package, the freezing problem seems to have gone.

Edit one day later: Oh no, the freeze occurred again and this time "tumblerd" is definitely innocent. Problem must have another reason.

---

