---
title: "rhythmbox error"
date: 2012-10-05
forum: General Help
---

### Post by pmattt on 2012-10-05
hello,
   
   Rhythmbox pop-up frequently when i use ubuntu and my system freezes completly.All actions will freezed including shutdown and restart.I reinstalled ubuntu many times .But the problem remains unsolved.please help me....
thanks in advance

---

### Post by cottfcfan on 2012-10-05
Not really sure i understand your post.
Do you mean that everytime you open Rhythmbox, you system freezes?
If so do you have all the codecs you need installed?
```
sudo apt-get install ubuntu-restricted-extras
```
You could also try another music player, Clementine is excellent, & see if the problem persists.
More info would be helpful though.

---

### Post by JRBASTIEN on 2012-10-05
Try disabling all your plugins.  I had some issues with some third partiy plugins I have installed.  

You can also look at the syslog file with the log viewer application.

---

### Post by pmattt on 2012-10-06
Actually  i never tried to open rhythmbox, it opens automatically while using ubuntu.After that i am not able to close rhythmbox also.when i click close it disappears but it again appears after sometime.

---

### Post by claracc on 2012-10-06
You have to add more information about your hardware specs, and describe the problem in a clearer way.

As I have understood, when you boot in ubuntu 12.04, rhythmbox runs by itself and freezes the system?. Not take as an offence but it has not much sense.

Please, run in a xterm the command lspci in order to have information about your hardware, I have assumed your system is ubuntu 12.04. What desktop?. What is running in your system when it freezes?.

Have you rhythmbox ticked as an app starting at the beginning?

---

### Post by pmattt on 2012-10-06
yes thats the problem i am facing.Am not added rhytmbox in autostart.rhythmbox appears whenever system uses.

os version:ubuntu 10.04
processor: AMD Athlon2
Desktop:GNOME 2.30.0
i got the following details when i used lspci command


00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 7025 / nForce 630a] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control

---

### Post by claracc on 2012-10-06
I have found this thread: 
[http://ubuntuforums.org/showthread.php?t=1376786](http://ubuntuforums.org/showthread.php?t=1376786)

The problem is similar to the one you have and probably the solution also works for you.

---

### Post by pmattt on 2012-10-08
HI,

I already tried to solve my system prob with the following process, but still the problem occurs, is there any other alternate to resolve my problem, please help me out friends

---

