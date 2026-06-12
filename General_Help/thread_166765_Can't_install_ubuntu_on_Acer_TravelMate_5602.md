---
title: "Can't install ubuntu on Acer TravelMate 5602"
date: 2006-04-27
forum: General Help
---

### Post by trebor10810 on 2006-04-27
Good day to you all,

I have been running Ubuntu 5.10 on a stationary box for about 4 months and loving it. As I travel a lot I wanted to have my new laptop dual boot. I tried to install ubuntu on my new Acer TravelMate 5602WSMi and it gives me the error cant find the CD ROM drive. In the options section the CD drive is not shown. This is the drive:

ATAPI TSST corpCD/DVDW TS-L6320- (PS)

Any suggestions would be great.

Thanks
Rob

---

### Post by Sef on 2006-04-27
Can you put the install cd in your desktop and see if it picks it up?  (Just reboot after it detects or doesn't detect your cd.)

If it doesn't pick it up then you know that the cd is bad.  if it picks it up, then it is a question that I would have to research.

---

### Post by trebor10810 on 2006-04-27
The CD works fine it boots in the Acer from the CD drive and loads the kernal and gets to a point where it searches for hardware and then tells me it cant find the cd drive.

---

### Post by trebor10810 on 2006-04-28
Hi All,
I am getting just a little worried! Is there some way I can find out the information I need to install this system. I installed 3 other distros yesterday ans all went fine. Why is the one I want not playing ball? It seems that this forum is the only place to get support and that is community only. PLEASE I realy dont want to run another distro. I have ubuntu on my desk top PC and would like it on my laptop.

---

### Post by trebor10810 on 2006-04-28
I am begining to believe why no linux distro will ever be able to even nearly match the market penetration of Windows. The reason is there is no finite support structure. Right now I would pay serious dollars just to find out if I can ever expect to install 5.1 on my new laptop. There is nothing I can find to get even an answer!!!!

I cannot afford to wait days in the hope that someone in this forum who knows the answer will eventually read my post and then actually answer the question. Is there a pay for support structure? Because this level of support just does not work for serious business people. It may be fine for home use and such but it is not any good for industry.

PLEASE how can I get help?

---

### Post by Word on 2006-04-28
For kicks and giggles make a new cd. first also when ever you gonna get a new laptop for any linux version use the live cd on it. thats the break test. If that works then you know this laptop is good. 

[QUOTE=trebor10810]I am begining to believe why no linux distro will ever be able to even nearly match the market penetration of Windows. The reason is there is no finite support structure. Right now I would pay serious dollars just to find out if I can ever expect to install 5.1 on my new laptop. There is nothing I can find to get even an answer!!!!

I cannot afford to wait days in the hope that someone in this forum who knows the answer will eventually read my post and then actually answer the question. Is there a pay for support structure? Because this level of support just does not work for serious business people. It may be fine for home use and such but it is not any good for industry.

PLEASE how can I get help?[/QUOTE]

---

### Post by xgrendel on 2006-04-28
I had the same problem on a desktop PC I once had. Are you using a straight copy burned from an Ubuntu iso, an official CD,  or are you using a CD that came with a magazine? My problems stemmed from one of two things but I'm honestly not sure which one:

Case 1: I have a CD Writer and a DVD writer. If I would put the disk in one drive, Ubuntu would load the base system for the install then throw the error. In a couple of cases, I just switched the disk from one drive to the other and it worked. It was almost as if the initial cdrom drive it booted itself off of was ignored as the installation drive. You may want to slightly modify your BIOS on bootup to boot from the CD first. Although I don't think this would be an issue, it could be looking for the primary boot device which may be set as a floppy in the BIOS.

Case 2: I had a bad burn on a CD-R. The installer would boot but when it got past loading the base and prepared to install, the error was thrown repeatedly. I reburned and the problem was resolved.

---

### Post by 5-HT on 2006-04-28
[quote=trebor10810]I am begining to believe why no linux distro will ever be able to even nearly match the market penetration of Windows. The reason is there is no finite support structure. Right now I would pay serious dollars just to find out if I can ever expect to install 5.1 on my new laptop. There is nothing I can find to get even an answer!!!!

I cannot afford to wait days in the hope that someone in this forum who knows the answer will eventually read my post and then actually answer the question. Is there a pay for support structure? 

PLEASE how can I get help?[/quote] 
These are community support forums, everyone here just volunteers their time.
 If you'd like paid support from Canonical, here's the link:

[Canonical Commercial Technical Support For Ubuntu   ]("http://www.ubuntu.com/support/supportoptions/paidsupport")

[quote=trebor10810]Because this level of support just does not work for serious business people. [/quote] 
It's not meant to be. See link above.

[quote=trebor10810]I have been running Ubuntu 5.10 on a stationary box for about 4 months and loving it. As I travel a lot I wanted to have my new laptop dual boot. I tried to install ubuntu on my new Acer TravelMate 5602WSMi and it gives me the error cant find the CD ROM drive. In the options section the CD drive is not shown. This is the drive:

ATAPI TSST corpCD/DVDW TS-L6320- (PS)

Any suggestions would be great. [/quote] 
As to your question though, there are problems with certain Acer notebooks having similar problems. You did not describe your problem in detail, but if it is an issue where the installation stops at 86% when loading the 'ide-cd' module during hardware detection, the following threads may be of help:

[http://ubuntuforums.org/showthread.php?t=75002]("http://ubuntuforums.org/showthread.php?t=75002")

[http://ubuntuforums.org/showthread.php?t=128987]("http://ubuntuforums.org/showthread.php?t=128987")

Hope you get it working.

---

### Post by trebor10810 on 2006-04-29
Hi All,

I tried an official CD, a downloaded iso CD all the same. I then decided the computer was too new for the 5.10 so I tried ^.06 and it works perfectly

Thanks to those who commented.

I found Canonical and I will be using them for supporting my companies computers. At this stage I am evaluating prior to switching my entyre organisation.

Thanks again
Rob

---

