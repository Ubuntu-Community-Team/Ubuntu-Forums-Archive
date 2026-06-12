---
title: "strange screen freeze after long idle time"
date: 2006-04-16
forum: General Help
---

### Post by henon on 2006-04-16
hi,
ubuntu worked well for me since i upgraded to breezy badger. but lately it often freezes after long idle time. when i leave it running over night ... independent from the apps that are running ... sometimes in the morning the screen is frozen (but i can still move the mouse). i cannot ALT+CTRL+F1 to login on tty1 but i can login via ssh and the processes are still running normal. i don't know if [FONT="Courier New"]/etc/init.d/gdm restart[/FONT] helps because i did not know that yet. so i did a [FONT="Courier New"]shutdown -r now[/FONT] which helped of course.
next time i get a frozen desktop where i can move the mouse i will try restarting gdm and if it does not help i will ask here again. the actual reason why i am posting is the strange freeze i had today: 

the system has been running for 2 days alone (doing some downloading) and when i came back the monitor did not want to come back from standby no matter what i tried. "gdm restart" did not solve it and i was forced to reboot. :evil: 

what do you think is the problem? has anyone encountered similar problems?
any clues on a system which can be logged on to via ssh but the desktop is frozen? 

thanks in advance for any help!!
-- henon

SYSTEM INFORMATION:
Ubuntu Breezy Badger on Athlon 1800 XP / ATI Radeon 9600 / 512mb RAM

---

### Post by henon on 2006-04-16
ok, just an hour after writing this post it froze again. had azureus and xchat running. logged in via ssh and restarted gdm. then the xserver responded again. this is very anoying and i don't know what is going on. any hints?
-- henon

---

### Post by em0maha on 2006-04-17
I'm having the same problem. I have been using Ubuntu for about a week, and this happens to me almost every day.

The system runs just fine when im working on it, but after i let it sit for an hour or so and come back to it, its just terrible. when it freezes, I notice the following behavior:

-The mouse works pretty well, however it completely freezes sometimes. 
-Whenever I try to do something (close a window, type in a command, open a website, shut down the computer) it will take about 1-5 minutes for the action to happen. It seems like It freezes for a few minutes, then runs fine for about 2 seconds, then goes back to freezing.

If anyone could lend a hand, Id be very greatful. 

I was origionally planning on building a dualhead, one screen with mythtv running all the time, and the other for my other computer needs, but I decided to just try and get the basics working first. If im having this problem theres no sense in running mythtv because it will be up for a long time just idleing and I dont want to have bad recordings.

](*,) ](*,) ](*,)

---

### Post by em0maha on 2006-04-17
I forgot to mention, the hardware that i am using:

P4 2.8Ghz
256 MB RAM
Onboard Intel graphics and sound

---

### Post by acefreely on 2006-09-21
I have the same problem...xwindows freezes after being left alone for a while.  Here is lspci from my machine...

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
0000:00:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
0000:00:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
0000:00:0b.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 03)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
0000:00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
0000:00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
0000:00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
0000:01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
```

---

### Post by acefreely on 2006-09-22
Looks like my system has stabilized thanks to updated nvidia drivers and tseliot.  Have a look at this post and follow the link to install the envy script and update nvidia drivers.  X has not locked up since I installed the updated drivers...

[http://www.ubuntuforums.org/showthread.php?t=262782&highlight=envy]("http://www.ubuntuforums.org/showthread.php?t=262782&highlight=envy")

---

