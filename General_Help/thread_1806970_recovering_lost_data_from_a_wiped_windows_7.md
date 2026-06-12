---
title: "recovering lost data from a wiped windows 7?"
date: 2011-07-18
forum: General Help
---

### Post by sarahwpen on 2011-07-18
ok, here's the deal:

I bought a new dell studio 1555 from best buy about a year and a half ago. Got the warranty because I have 4 kids and something is bound to be dropped, spilled or smashed at some point. True to my visions, something did get dropped smashed and spilled, and pennies got stuck in the dvd slot. So I took it in when the screen stopped coming on because of a loose connection in the hinge and they did apparently fix that problem, but also were benevolent enough to wipe out my entire hard drive, operating sytem and all, totally free of charge. I guess they figured since I like accidents so much, I would just LOVE having 18 months of data and programs disappear into thin air. I know all about how I should have backed it up, and I am not whining too much over this. I will roll with the punches. But there are just a FEW things on that hard drive I will really miss. Like a few crucial spreadsheets that I was not able to save to my external drive before the screen went south. Now that windows 7, I am not planning on missing at all. In fact I am loving running my new Ubuntu 11.04 from my usb and knowing that those idiots will not be able to screw this one up next time. But I would really like to be able to recover those files if I can. Is there any way to get those back? And I also cannot figure out how to find device manager. Do I have to install to hard drive to use that? I know these are all probably total newbie questions. But hey, i got here as soon as I could. Everybody has got to start somewhere.

---

### Post by Cybie257 on 2011-07-18
You can using Runtime software called GetDataBack. Likely you would want the NTFS version. You would have to have another windows operating system to hook the drive up to and I would suggest hooking up internally as USB can take forever, but still works if that's the only option. 

[http://www.runtime.org/](http://www.runtime.org/)

I don't know of any Linux based NTFS data recovery programs as I am assuming they have a fresh Windows installation on your computer. So, the GetDataBack program will scan the entire drive and allow you to recover (copy) any found 'lost' data to another drive. There is a Linux software that will recover partitions for a windows drive, but I don't see that as an option since they installed a fresh copy of windows. 

My suggestion to anyone that ever sends in a computer to be repaired (for hardware/damage reasons) is to remove the hard drive prior to sending in. I had to send a dell laptop in once for a warranty issue and told the rep that I was going to remove the hard drive and they said that was perfectly fine, so should never be an issue. It's also a security feature so your private data isn't able to be viewed by just anyone.

Hope this helps. Oh, and if they just replaced the drive itself, then you are out of luck with the recovery. So, be sure that you check to see if they replaced the drive or just refreshed it.

-Cybie

---

### Post by cgAtom on 2011-07-18
Hey, welcome to the forums. 

You didn't mention if after the wipe they reinstalled win 7 or any other  OS on there, in case that they didn't and left you with a blank hard  drive theres a very good chance you could retrieve the data that you  need by using [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

for the device manager question, as far as my knowledge reaches there is  no equivalent tool in linux. But you can use the following to list all  the devices from a terminal.

To list pci devices enter lspci

To see your USB devices enter lsusb.  
 
 To see your disk usage enter df.  
 
 To see your memory usage enter free.
 
 To see your directory structure and files enter ls.
 
 To move around in the file system enter cd.
 
 Use "man command" to reach help for any text based tool.

---

### Post by Allavona on 2011-07-18
Do you have all the connectors that you need to hook up the laptops HDD to another computer? If not your going to need them. There is a plethora of recovery software out there that you can use to recover data off of wiped drives.

That being said...The best advice I can give is to take it to some "geek squad" type business and tell them what you need.

You won't recover programs or such, but some files, such as pics, docs, etc... maybe recovered in this way.

It also depends on how they wiped your drive. Was it a simple format, or a complete forensic wipe?

This is beating a dead horse, but I can't stress enough the importance of backing up data.
Clonezilla, Remastersys, AptonCD all work great.

---

### Post by philinux on 2011-07-18
> **sarahwpen said:**
> ok, here's the deal:

I bought a new dell studio 1555 from best buy about a year and a half ago. Got the warranty because I have 4 kids and something is bound to be dropped, spilled or smashed at some point. True to my visions, something did get dropped smashed and spilled, and pennies got stuck in the dvd slot. So I took it in when the screen stopped coming on because of a loose connection in the hinge and they did apparently fix that problem, but also were benevolent enough to wipe out my entire hard drive, operating sytem and all, totally free of charge. I guess they figured since I like accidents so much, I would just LOVE having 18 months of data and programs disappear into thin air. I know all about how I should have backed it up, and I am not whining too much over this. I will roll with the punches. But there are just a FEW things on that hard drive I will really miss. Like a few crucial spreadsheets that I was not able to save to my external drive before the screen went south. Now that windows 7, I am not planning on missing at all. In fact I am loving running my new Ubuntu 11.04 from my usb and knowing that those idiots will not be able to screw this one up next time. But I would really like to be able to recover those files if I can. Is there any way to get those back? And I also cannot figure out how to find device manager. Do I have to install to hard drive to use that? I know these are all probably total newbie questions. But hey, i got here as soon as I could. Everybody has got to start somewhere.

You could try this. [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

It's in ubuntu repo so you can install via synaptic and your live usb. Part of it is a utility called photorec. It's only a small set of apps.
I've successfully used photrec to recover Gigs of accidentally deleted files.

Good luck.

---

### Post by sarahwpen on 2011-07-18
Wow, that was amazingly fast responses! you guys are awesome! 

I am still digesting everything you have said, but to clarify a few things here while I am chewing:

1. Nothing was reinstalled after the wipe. They asked me for the recovery disks, which have disappeared like a left sock in the dryer. I have not reinstalled ANYTHING back to the hard drive yet. Running from usb flash drive right now.

2. I have a very old dell inspiron laptop running win xp is the only other computer available to me currently. I am pretty sure I am not capable to connect this hard drive to it. 

3. Yes. I will keep my hard drive next time. I was nervous about leaving it in this time, and am really kicking myself for it, but was in a hurry, lazy and figured a simple hardware fix of a loose connection would not require anyone to mess with that, so I just crossed my fingers and hoped for the best. Paying for that now for sure. Won't do it again.  

4. Most of the data WAS backed up, with the exception of a few things. I usually back up once a month. There was only 1 or 2 spreadsheets that were in odd folders that I never had time to reorganize and put where they should be that got missed. If I have to let them go, I will live, but I would rather not. 

5. It is possible that they did replace it. That is what they said they did. It is the same size and type as my old one. I have no serial numbers from the old one to be able to tell, but I am suspicious. I kinda think maybe I just pissed them off and they decided to spit in my burger. Because as far as I can tell there was absolutely NOTHING wrong with my old hard drive.

---

### Post by Cybie257 on 2011-07-18
> **sarahwpen said:**
> 

2. I have a very old dell inspiron laptop running win xp is the only other computer available to me currently. I am pretty sure I am not capable to connect this hard drive to it. 


Not true. Although it would be a very Slowwwww process, you should still be able to hook the drive up through USB using a universal USB adapter or even put the drive into a USB external case. 

If you choose to give RunTime GetDataBack a shot, it does work with XP. And, I think that you can also download a trial version that will scan, but not save found data. It's not one of those trickery pieces of software that says it found all sorts of things, then you pay for it and it isn't able to recover. It's been about 5 years since I bought my program, but that's how it worked. I still use that version with Windows 7 with the only problem being that when I close it, I get an exception error, but at that point, don't care as the process itself worked every time prior to closing. 

And, if you go that route, be sure to save EACH step of the scanning process. That way, should you lose power, need to shut down the computer, or whatever else, you can continue from where you left off, saving you hours, if not days of scanning time.

-Cybie

---

### Post by sarahwpen on 2011-07-18
> **cgAtom said:**
> Hey, welcome to the forums. 

You didn't mention if after the wipe they reinstalled win 7 or any other  OS on there, in case that they didn't and left you with a blank hard  drive theres a very good chance you could retrieve the data that you  need by using [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

for the device manager question, as far as my knowledge reaches there is  no equivalent tool in linux. But you can use the following to list all  the devices from a terminal.

To list pci devices enter lspci

To see your USB devices enter lsusb.  
 
 To see your disk usage enter df.  
 
 To see your memory usage enter free.
 
 To see your directory structure and files enter ls.
 
 To move around in the file system enter cd.
 
 Use "man command" to reach help for any text based tool.


ok, this helps a little. I am trying to understand how I can look for my hard drive to even make sure that it physically exists anymore first of all (preferably without having to take my laptop apart). 

Aside from all this, even if I can't get my data back. I can't seem to figure out how to save files to the hard drive when running the OS on the flash drive. My external hard drive shows on the "computer" screen, but my internal HD does not. UNLESS, it is what they are calling "file system" in which case I can't figure out how much space has been used and what is free, where to save things and what to not touch. 

I am reminded of a post I saw last week saying "windows is like a cheap car, macs are like foreign cars, and linux is like a tank." I am totally loving my tank. It blows away the features of the competition, is fast, for most purposes it seems just like what I have always wanted. I just can't figure out how to drive it. 

I really am trying to learn here. I am googling everything, I don't expect you guys to just magically pour all the answers in my brain or anything. Thanks for taking the time.

---

### Post by sarahwpen on 2011-07-18
oh, and I know it is the same size and type as the old one because I started to install ubuntu onto the hard drive, and it found it, and gave the info on it, and at that point I though, hmmm. Maybe I should check to see if they only erased it all instead of actually replaced it. Maybe I am just wishful thinking here.

---

### Post by sarahwpen on 2011-07-18
AHA AHA!!!!! "Applications". DUH. found my hard drive. Apparently I was missing a whole massive section of necessary stuff when I was looking. Applications, system, disk utility. So. Now I am assured that all my working parts are there. I feel better. LOL. So now I can move on to trying to find out what is on it like my original quest.

---

### Post by Mark Phelps on 2011-07-18
My own experience at using Linux utilities to try to recover MS Windows files from former NTFS partitions has been really bad!  I have always resorted to using GetDataBack and it has never failed me.

That said, if you STILL want to use GetDataBack to try to recover the files from your drive, you will need to be able to do the following:
1) Remove the drive from your PC
2) Connect the drive to a different PC, one running MS Windows.  To do this, you will need either a kit containing the different adapters needed, or a external drive enclosure (in which you will have to insert the drive).
3) Download and install the TRIAL version of GetDataBack for NTFS on that pc
4) Run GetDataBack against the old drive, letting it run overnight.
5) Check the log and see if it found the files you want.  If it did, you will have to purchase it to do the actual file recovery. But, all that does is require you enter a serial number to activate the software.

---

