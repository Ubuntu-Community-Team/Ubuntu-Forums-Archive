---
title: "Super duper hot CPU"
date: 2011-07-22
forum: General Help
---

### Post by Kingcapone on 2011-07-22
[SIZE=3][FONT=Calibri]Ubuntu 11.04 is making my AMD Phenom 2 P920 Quad-core 1.6 GHz run really hot the fans are going at full speed and things are just running really slow, I wouldn’t mind if I was transcoding the universe but the fact I’m not actually doing anything and it’s still doing it is what’s P---ing me off literally I’ve closed all running programs and left my laptop for 40 mins while I walked to shop I got back and the fans are still at full speed? I’m running the 32bit version by the way and it’s not the room temperature or anything because when I go back to windows 7 it doesn’t do it.[/FONT][/SIZE]

---

### Post by altometer on 2011-07-22
Does this happen when you boot to the live CD?

Go into a terminal and type "sudo top" and see what's using the CPU.

Also, you need to set the CPU governor to "ondemand" in power management settings.

---

### Post by pqwoerituytrueiwoq on 2011-07-22
powernowd may help
sudo apt-get install powernowd

also take a at this 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
search for this near the bottom:
> Disable the check of power state or changes the OS compatibility  reported to the BIOS. Necessary on some broken BIOSes to make  temperature/fan control work. 

food for thought:
manufactures tend to use cpu scaling on windows to cap the cpu speed
they can make the laptop look good my putting a 3Ghz processor is in but use that to make the real speed only 1Ghz max so they can cheap out on the cooling system

---

### Post by makcbe on 2011-07-24
In System>Preferences>Power Management, select 'spin down hard disks when possible'. It helped for me.

---

