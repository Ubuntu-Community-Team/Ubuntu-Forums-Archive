---
title: "Repairing virus in Window 7 32bit"
date: 2011-04-11
forum: General Help
---

### Post by Tomween1 on 2011-04-11
We recently installed v10.04 on my sons desktop pc. This computer is set up as a dual boot system, having Ubuntu on one hdd and windows on another. Recently my son had a virus infect Windows 7 and I am now trying to clean it out. I've done some reading on how to accomplish this but have failed miserably. 

Done so far; tried installing avast free but unfortunately can't get beyond AVAST ERROR  *An error occurred in avast! engine: invalid argument.*

So now I ask, 1) how do I remove avast, 2) was this the right thing to try and 3) how do I attempt to remove the virus from windows.

---

### Post by Enigmapond on 2011-04-11
Without knowing exactly what's being effected, it's difficult. I have had very good luck with a programme called Combofix which can be got here [http://www.bleepingcomputer.com/download/anti-virus/combofix](http://www.bleepingcomputer.com/download/anti-virus/combofix)

However great care should be taken in using this programme. It can do harm if not careful. So I do tell you about it but really state use at own risk. I have never had any repercussions but from what's been said, there can be some.

Good Luck...

Also if you know where the file is located, it's possible to access it from the Ubuntu side and removed with no adverse effects to THAT OS...

---

### Post by dragonfly41 on 2011-04-11
You could try AVG free edition ..

[http://free.avg.com/gb-en/homepage](http://free.avg.com/gb-en/homepage)


[EDIT]

p.s. I've just read about this one which could run in ubuntu and scan windows partition .. perhaps?

[http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html](http://linuxhelp.blogspot.com/2005/10/clamav-free-anti-virus-solution-for.html)

---

### Post by howefield on 2011-04-11
Is Avast installed to Windows or Linux ?

If it were mine, I guess I'd install Bitdefender (for unices) on Ubuntu and scan the windows disk from it.

---

### Post by Spyderkid on 2011-04-11
just get a norton free trail then remove it with that

---

### Post by Tomween1 on 2011-04-11
> **Enigmapond said:**
> Without knowing exactly what's being effected, it's difficult. I have had very good luck with a programme called Combofix which can be got here [http://www.bleepingcomputer.com/download/anti-virus/combofix](http://www.bleepingcomputer.com/download/anti-virus/combofix)

However great care should be taken in using this programme. It can do harm if not careful. So I do tell you about it but really state use at own risk. I have never had any repercussions but from what's been said, there can be some.

Good Luck...

Also if you know where the file is located, it's possible to access it from the Ubuntu side and removed with no adverse effects to THAT OS...

It's an age old one.... he opened "a virus has been detected, click to repair" No matter what one does, you can't get kids to listen! What I do know is his computer can take up to 15 minutes to boot into windows.

---

### Post by Tomween1 on 2011-04-11
> **howefield said:**
> Is Avast installed to Windows or Linux ?

If it were mine, I guess I'd install Bitdefender (for unices) on Ubuntu and scan the windows disk from it.

I was trying to install through Ubuntu.

---

### Post by Tomween1 on 2011-04-11
> **Spyderkid said:**
> just get a norton free trail then remove it with that

Load it through Ubuntu? He already has norton installed on his Win 7 pc

---

### Post by Kirboosy on 2011-04-11
I use [Malwarebytes]("http://www.malwarebytes.org/") for virus removal.

The free version is on-demand only but thats really all you need in this situation. I have always had good luck with it removing viruses and malware. Its what we used in my IT department to quickly remove viruses.

For a always on Anti-Virus I would recommend Microsoft Security Essentials. My IT department always jokes that there is only two things that Microsoft has ever done right. Microsoft Office and Microsoft Security Essentials. :)


If the virus is not allowing you to install programs you will need to reboot the computer into safe mode and install then scan it while in safe mode. Safe mode can be accomplished after selecting the windows from GRUB and tapping F8 a few times. 


~Caboose

---

### Post by Enigmapond on 2011-04-11
Here's another option. Boot into Ubuntu. Install Clamav and Clamtk. When done scan the windows partition with it to see if it finds anything. Easy way is open a terminal and do:

```
sudo apt-get install clamav clamtk
```

See if it can be fixed from the Ubuntu installation first.

---

### Post by beew on 2011-04-11
> **Tomween1 said:**
> It's an age old one.... he opened "a virus has  been detected, click to repair" No matter what one does, you can't get  kids to listen! What I do know is his computer can take up to 15 minutes  to boot into windows.

Malwarebytes would fix it. Boot into safe mode, install malwarebytes and run it. I have used it to fix the same problem in someone's Vista.

Now the only catch is that after cleaning out the virus you wouldn't be able to start any program. The virus changed the registry so that whatever you clicked the popup was triggered. Now after the virus is removed the registry entries have to be manually reset to restore the proper file association.
(Sorry I cannot give you a definitive link but there are many if you google "restoring file association" or something like that.)

---

### Post by beew on 2011-04-11
> **Enigmapond said:**
> Here's another option. Boot into Ubuntu. Install Clamav and Clamtk. When done scan the windows partition with it to see if it finds anything. Easy way is open a terminal and do:

```
sudo apt-get install clamav clamtk
```See if it can be fixed from the Ubuntu installation first.

Doubt it. Clamav is only good for scanning email (if it is good at anything). Moreover it doesn't remove the virus if I remember correctly, it just tells you you are infected and you would need to manually remove it (if it can find the virus in the first place) 

IMO you don't normally need an AV in Linux, but if you have to get one use a real one like Bitdefender. ClamAV is garbage, it is slow, clunky and ineffective.

Edited: for this particular problem, running malwarebytes in Win is the way to go, it is easy to set up and fast.

---

### Post by Duncan Williams on 2011-04-11
First off be very very carefull if you use combofix > dangerous as it will delete things and mangle your system.

If you want to sort it out go to my website:
[http://my.opera.com/internetsecurity/archive/](http://my.opera.com/internetsecurity/archive/)

There are a number of free malware scanners. Use 2 or 3 of them to do a full scan.

Setup the `**core**' security programs.

Use the cleaners and registry repair tools to speed up the pc and further remove any problems.

If you want any specific advise feel free to ask me.

This is obviously using and checking/securing windows.
All software/applications available are free.

---

### Post by Kirboosy on 2011-04-11
To keep it simple I would just use a Windows program to fix the Windows problem. No sense in dirtying up Ubuntu to fix Windows.

---

### Post by Timmer1240 on 2011-04-11
If you work through this guide it will clean up your windows install   [http://forums.majorgeeks.com/showthread.php?t=139681](http://forums.majorgeeks.com/showthread.php?t=139681)

---

### Post by crispy_420 on 2011-04-11
Working from the Ubuntu side? Try BitDefender for Linux:

[http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/](http://download.bitdefender.com/SMB/Workstation_Security_and_Management/BitDefender_Antivirus_Scanner_for_Unices/Unix/Current/)

---

### Post by bodhi.zazen on 2011-04-11
> **Tomween1 said:**
> We recently installed v10.04 on my sons desktop pc. This computer is set up as a dual boot system, having Ubuntu on one hdd and windows on another. Recently my son had a virus infect Windows 7 and I am now trying to clean it out. I've done some reading on how to accomplish this but have failed miserably. 

Done so far; tried installing avast free but unfortunately can't get beyond AVAST ERROR  *An error occurred in avast! engine: invalid argument.*

So now I ask, 1) how do I remove avast, 2) was this the right thing to try and 3) how do I attempt to remove the virus from windows.

It has been a while since I have removed such things mind you, but ...

Ubuntu (Linux) is not really the way to go about this, at least IMO.

Removal really depends on what exactly you are trying to clean. You need to identify the virus and then google search it's removal. Often this means deleting infected files , cleaning files (sometimes possible), and editing the windows registry.

All this will be difficult with Linux.

I believe there are several live CD designed to do this, clean windows, but I have not run anything like that in many years. You might also wish to check on a Windows forums.

With that I am going to close this thread now as it is more windows support then Ubuntu support. Good luck to you.

---

