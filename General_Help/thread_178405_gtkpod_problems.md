---
title: "gtkpod problems"
date: 2006-05-17
forum: General Help
---

### Post by shredfitz on 2006-05-17
So I am new to linux/ubuntu and all was going very well for me thus far until today.  I had used gtkpod to manage files on my ipod a couple of times successfully until today.  I was removing some old music adding some new stuff and when I disconnected my ipod and checked the ipod to be sure that the changes were made, none of my files showed up at all.  I connected the ipod back to gtkpod and got the following message :


warning....the following has occured :

iPod Database Import Failed: 'iTunesDB corrupt: hunk length 0 for hunk at -411183876 in file '/media/ipod/iPod_Control/iTunes/iTunesDB'.'



I then looked at my files under the "F01 File Browser that automatically pops up whenever I connect my ipod to ubuntu, and i looked in the music file and all of the files are still on the thing but something drastic has happened and I cannot use my ipod.    Do I need to go onto my windows machine and run itunes to resolve this ?

If anyone knows I would appreciate your input.


Thanks.

---

### Post by mybootorg on 2006-05-17
I'm likely to get flamed for saying so, but with regards to Ipod use and Ubuntu (and Linux in general) prepare yourself for major annoyance.  Because of the database format that Ipod's use, Ipod's only seem to work flawlessly under ITunes.  This has gotten better this year with Windows apps such as Anapod Explorer and a few others. But it's still very much a problme in Linux from what I can tell.

Some observations:

1) Both AmaroK and gtkpod will corrupt your Itunes database from time to time.  After this occurs, the only fix I have found is to put the Ipod in Disk Mode and perform a quick format from a Windows machine to reset things to normal.

2) Of the Linux-based Ipod sync programs I have used so far, "yamipod" seems to work well, and the most consistently.  Google it.  It even has a "repair Ipod" function that will attempt to repair your database if something goes bad.

Some tips:

1) Going back and forth between ITunes and any other Ipod sync app is eventually going to lead to corruption.  Yes , even though some apps promise to sync ITunes database with their own db, you are still likely to see occasional corruption.

2) If you call Apple support, do not tell them you are using anything other than ITunes on your Ipod.  Just tell them you turned it on one day and it wouldn't work. They're used to hearing that :)

3) If you're going to use an alternative Linux-based Itunes sync replacement like gtkpod, yamipod, or AmaroK, make sure you Disk-Mode format your Ipod in Windows.  Then make sure you use ITunes on your very first sync so the intial database gets set up correctly (this is something the other replacements dont seem to do very well on their own.)
[B]
In short: the solution to your current problem is to find a windows machine. Put your Ipod in Disk-Mode.   Quick format it (Fat32).  Then sync it with ITunes once. [/B]

---

### Post by shredfitz on 2006-05-18
thx myboot.  YamiPod seems to be working well.  On a related note, could anymone make a recommendation for the best portable digital music player for use with a linux system ? (other than a cd-walkman)

---

### Post by linuxted on 2006-05-18
[QUOTE=mybootorg]I'm likely to get flamed for saying so, but with regards to Ipod use and Ubuntu (and Linux in general) prepare yourself for major annoyance.  
Because of the database format that Ipod's use, Ipod's only seem to work flawlessly under ITunes.  This has gotten better this year with Windows apps such as Anapod Explorer and a few others. But it's still very much a problme in Linux from what I can tell.

Some observations:

1) Both AmaroK and gtkpod will corrupt your Itunes database from time to time.  After this occurs, the only fix I have found is to put the Ipod in Disk Mode and perform a quick format from a Windows machine to reset things to normal.

2) Of the Linux-based Ipod sync programs I have used so far, "yamipod" seems to work well, and the most consistently.  Google it.  It even has a "repair Ipod" function that will attempt to repair your database if something goes bad.

Some tips:

1) Going back and forth between ITunes and any other Ipod sync app is eventually going to lead to corruption.  Yes , even though some apps promise to sync ITunes database with their own db, you are still likely to see occasional corruption.

2) If you call Apple support, do not tell them you are using anything other than ITunes on your Ipod.  Just tell them you turned it on one day and it wouldn't work. They're used to hearing that :)

3) If you're going to use an alternative Linux-based Itunes sync replacement like gtkpod, yamipod, or AmaroK, make sure you Disk-Mode format your Ipod in Windows.  Then make sure you use ITunes on your very first sync so the intial database gets set up correctly (this is something the other replacements dont seem to do very well on their own.)
[B]
In short: the solution to your current problem is to find a windows machine. Put your Ipod in Disk-Mode.   Quick format it (Fat32).  Then sync it with ITunes once. [/B][/QUOTE]

Flame away if you must, but I agree that linux/ubuntu and ipods don't seem ready for prime time.  I really hope this gets addressed for selfish reasons and because I think it is a major turn off for new users of linux if their mp3 players won't talk to unix.

On a related note, my ipod no longer is recognized by my linux machine no matter what I have tried (part of this is the usb2.0 problems in unix).  I don't even want to use itunes - just to manage a database of my CDs converted to mp3s.  This used to work fine.  

If you haven't noticed, I'm quite frustrated with this and hope these issues are being addressed.

---

### Post by shortsellyhoonow on 2006-11-05
Haha

---

### Post by tortus on 2006-11-05
heh syncing my ipod has pretty much become the only thing my Mac does now. I do everything else in ubuntu on my PC.

---

### Post by bean77 on 2007-11-24
Two problems I am having...

1.  When I try to get my ipod to mount in gtkpod, I get this:

**[CENTER]iPod Database Import Failed: 'Failed to read from file '/media/IPOD/iPod_Control/iTunes/iTunesDB': Input/output error'[/CENTER]**

2.  When my ipod is plugged in, my keyboard and mouse get all wonky.  Barely responsive to clicking, moving, etc.  This has never happened before.  I have synced my ipod before with gtkpod (I've reinstalled Ubuntu since then for various reasons) and for some reason it no longer works.  Furthermore, this mouse issue has only come about in the past few days.  I can't remember what I've updated in the past few days with regards to software...does this issue sound familiar to anyone?

---

