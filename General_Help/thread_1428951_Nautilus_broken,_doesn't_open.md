---
title: "Nautilus broken, doesn't open"
date: 2010-03-13
forum: General Help
---

### Post by Pott on 2010-03-13
Tried to dual XFCE/Gnome, but it totally failed. Not sure why. Some things simply didn't work. I went back to pure Gnome and since then Nautilus has refused to work. Simply doesn't open, even from the terminal. I tried reinstalling it, to no avail. Nothing. Just doesn't work :s
A full reinstallation or even removal using Synaptic didn't work either. I can't even check my files at all! 

I'll use Thunar meanwhile but this is just weird... I can't find out how to make Thunar default either.

Any idea what I need to do..?

EDIT:  some more details

I tried three times to get XFCE through Synaptic. All the times there were issues and I uninstalled it and went back to pure gnome as per Psychocat's tutorial's instructions. Then when I got back into my usual Gnome session, File Manager was broke and it started repetively opening on my panel Window List app... Not sure how to explain this one really. Really broke. Then going to Places, Documents, Music etc... didn't do anything. Eventually it started working but there are still broken bits (it still freaks out on my panel and doesn't work 100%).

So I have no idea what could have broken this. I removed it/reinstalled it both through synaptic and the terminal, and marked it for reinstallation through synaptic. Still not quite right...

---

### Post by Pott on 2010-03-14
Well I still get the freak out at startup which eventually ends, but it's working now.

---

### Post by Leischa on 2010-03-14
Nautilus has stopped working for me as well, and I wasn't playing around with XCFE either.

I was working one day when suddenly my desktop disappeared and now I can't open anything from the 'places' menu.

I have tried reinstalling through synaptic but it doesn't work.

I am using Dolphin in the meantime.

I am totally fed up with Ubuntu, which I have been using since Dapper. With every new release, something that used to work breaks.

This time, for me, it was Nautilus and 3G. I haven't been able to fix either.

---

### Post by bgrove on 2010-03-17
So tired of this behavior in WinDoze, switched and was happy ... for a time!
When there is a flaw in the basic file system browser, it is beyond irksome ...

Symptom: can't open any Places via simple click (I believe it's called "Nautilus" on a good day)

On deadline, my workaround yesterday was to open Firefox, enter file:// and browse for stuff I needed,
or to open OpenOffice and use that to access/edit files, then Save As ... to my pen drive.

[I]Editorial outburst: What a time-suck!
[/I]
My (next) move is switch from gdm to kdm and look for some sort of Dolphin creature, so that I can *GET BACK TO WORK!*

I take no comfort in seeing that this has affected others who have posted in this forum, and also wonder about the casuality of these observations:
[http://ubuntuforums.org/showthread.php?t=1379050&highlight=nautilus+open+places](http://ubuntuforums.org/showthread.php?t=1379050&highlight=nautilus+open+places)

As in: the timing of fail compared to other systemic changes
Rebooting now, hopefully with a shiny, new KDE

---

### Post by eholcroft on 2010-03-25
I reinstalled Nautilus when I had this issue. That fixed it.

---

### Post by Mike_tn on 2011-01-07
I had similar menu problems with Ubuntu 10.04 and 10.10
In 10.04 - Nautilus totally stops working and can't open any folders through any menu until running nautilus manually.
In 10.10 - after running Shotwell once the Nautilus under "Places" tries to open the wrong folder (Shotwell) and fails.

My fix was done badly for the second instance, and I deleted nautilus and then my whole desktop and couldn't get it back because of my modest Linux knowledge and was crippled by my access on-line being only public library wireless...getting a root shell connection was a problem. Also during the fix I tried installing a second desktop and didn't know how to access both but I do now! 

In the first instance (up top) I upgraded to 10.10 as a solution and in the second I reinstalled, so I never found a real fix. If it happens again I will dig around but in the mean time I found some solutions that might help any new problem. This might help someone: Until you figure out the solution to such problems through the forums or however you do it, get some backup solutions inplace early>

1)I installed a kde-plasma-desktop using aptitude to resolve the depends. That's the minimal desktop. It won't mess up your Gnome desktop with extra apps.  You can get to it at the login screen by clicking the fly-out menus you see there. It won't be in-your-face obvious, you have to poke about the login screen.  This would have come in handy for me when I deleted my ubuntu gnome desktop and couldn't get online to restore. I could have logged onto the kde to restore.

2)The second thing I do now is use Acronis True Image Home to back up my Ubuntu partition.  Acronis TIH is available at BestBuy and is well worth it.  The version I have is 2010 and it does ext3 filesystems, the newer 2011 does ext4. So I installed this time with ext3 for Ubuntu so I can backup a full image. Acronis uses compression with your partition and also lets you restore the MBR alone, both the MBR & partition together or only the partition without the MBR if desired.

---

