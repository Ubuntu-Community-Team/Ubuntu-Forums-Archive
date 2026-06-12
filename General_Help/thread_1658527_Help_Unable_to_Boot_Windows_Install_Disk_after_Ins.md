---
title: "Help: Unable to Boot Windows Install Disk after Installing Ubuntu"
date: 2011-01-02
forum: General Help
---

### Post by flekx on 2011-01-02
As said in my title, I'm unable to boot my Windows 7 install disks at startup after installing Ubuntu or more specifically Pinguy OS.  I edited the BIOS to boot the optical disk first but for some reason GRUB always boots first.  What should I do?
Sorry I'm a complete beginner at this and a friend somehow convinced me to install Pinguy OS.  I'm probably bad at searching because I've been searching for the last 4 hours and I have found nothing on the forums or Google.  But please don't say I haven't put in the time and effort in finding an answer.
THANK YOU SO MUCH!

---

### Post by flekx on 2011-01-02
Hi again Ubuntu forums community.  I'm hoping my rephrasing of my topic title will help garner me some more views.  I decided to switch over to Ubuntu (Pinguy OS) after some very persuasive coaxing from my friend.  But after some more careful research (and after having already installed Ubuntu) I realised that I would need to run a dual boot method in order to fulfil my needs.  I also noticed that my computer is actually running slower than it did with Windows 7.
So it would seem that my help post consists of two problems:
1.  I don't know how to reinstall Windows 7.  After changing the boot order on my BIOS to internal optical first, GRUB still loads first, and I have no idea how to boot my DVD copy of Windows 7 Installer when it does.
2.  Is my install of linux faulty.  I've encountered slow response times in the UI and in program loading (opening programs like terminal, firefox, open office are slower than average response times when I had Windows 7 installed).  In addition, several programs are not acting as they should: Wine and PlayOnLinux.  (Not installing my Starcraft II properly and running World of Warcraft with wine results in no video but working audio)
I hope I've given enough details for everyone to work with but please feel free to ask for clarification.
Thanks in advance,
Wiley

---

### Post by cariboo on 2011-01-04
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by mastablasta on 2011-01-04
> **flekx said:**
> Hi again Ubuntu forums community. I'm hoping my rephrasing of my topic title will help garner me some more views. I decided to switch over to Ubuntu (Pinguy OS) after some very persuasive coaxing from my friend. But after some more careful research (and after having already installed Ubuntu) I realised that I would need to run a dual boot method in order to fulfil my needs. I also noticed that my computer is actually running slower than it did with Windows 7.
So it would seem that my help post consists of two problems:
1. I don't know how to reinstall Windows 7. After changing the boot order on my BIOS to internal optical first, GRUB still loads first, and I have no idea how to boot my DVD copy of Windows 7 Installer when it does.

 
The OS has nothing to do with BIOS. if you set BIOS to boot from CD first and then stick your win7 DVD inside and it show up grub there are two possibilities: either bios didn't set CD as first boot or there is some problem with your windows CD. see if oyu can boot it on another computer.
 
another option would be there is somehting wrong with your CD drive and doesn't read the cd propperly so BIOS switches to next option which would be hard disk.
 
strange though you have GRUB showing up, if you don't have dual boot. it's just not necessary. 
 
regarding slowness open the terminal and type in command
 
```
top
```
 
post results here using code tags (use the # icon in forums to get them)
 
Next, did you check if there are any additional drivers necessary (such as for your graphics card) and enabled them? 
PinguyOS has some extra bling that could make it slower. don't know. but Ubuntu needs as little as 256MB ram to run propperly.
 
> 
2. Is my install of linux faulty. I've encountered slow response times in the UI and in program loading (opening programs like terminal, firefox, open office are slower than average response times when I had Windows 7 installed). In addition, several programs are not acting as they should: Wine and PlayOnLinux. (Not installing my Starcraft II properly and running World of Warcraft with wine results in no video but working audio)
I hope I've given enough details for everyone to work with but please feel free to ask for clarification.
Thanks in advance,
Wiley
 
regarding wine not every game works perfeclty. there are tweaks and setting that are needed when instalking them. best to check the wine application database for those instructions.
 
if your graphics card is not installed propperly wine will also give additional problems. bare in mind that wine is not a full substitute for Windows.

---

