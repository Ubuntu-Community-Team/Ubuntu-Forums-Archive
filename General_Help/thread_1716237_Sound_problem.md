---
title: "Sound problem"
date: 2011-03-28
forum: General Help
---

### Post by caneraris on 2011-03-28
Hello. I am pretty new at Ubuntu. The reason I started to use Ubuntu is I had a sound problem of my laptop with w7. but today ( the second day of using Ubuntu 10.10 64 bit ) i had the exact same problem. the problem is OS doesn't see my sound card or something. it's that dummy output problem.

Note: i use HP dv9620us with conexant card. 

i was listening to music today and the sound went somehow. the sound icon was normal but there was no sound then i rebooted the system and i saw 3 lines disappearing on the sound icon and in preferences it says dummy output. before using Ubuntu, i have searched a lot for the problem but couldn't find any real solution. I don't even know if it is a software or hardware problem. but if it was hardware, it wouldn't be any sound at the first place, right? 

Note: in hp forums, it is being said by some that the problem might be caused because of flash player.
some says it's hp and some says it's windows.

I really need a real solution, there must be one instead of using a USB sound card.

---

### Post by mastablasta on 2011-03-28
you can have a look here on how to trouboleshoot and solutions to sound issues:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
 
Otherwise post the output of the following command in terminal 
 
```
 
lspci

``` 
this will list the PCI devices.
 
It could be you are the "lucky" user of HD intel sound chip :-)
 
similar thing happened to me before in 10.04. And sitll does sometimes in 10.10. But reboot usually solves it. sometimes also this command will solve the issue:
 
```
 
sudo alsa reload

``` 
this reloads the module for sound drivers.

---

### Post by caneraris on 2011-03-28
Yes, i think i am lucky in that way :)
i haven't yet tried the solutions you suggested because i uninstalled flash plugin and sound came back after i rebooted. but still i don't know if it's permanent. i am gonna use it without flash for a while and see what will happen. then i will try your solution.

---

### Post by caneraris on 2011-03-28
suod alsa reload gives this:

lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/caner/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1578(pulseaudio). 
Unloading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc (failed: modules still loaded: snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-hda-codec-conexant snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
caner@ubuntu:~$

and the command slpci gives this:

caner@ubuntu:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7150M / nForce 630M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)

The sound went again. the sound icon appears normal this time. but after reboot, it will change i think.

---

### Post by mastablasta on 2011-03-28
ok so this is your sound chip:
 
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

 
You can see if there are any error messages during boot by using 
 
dmesg
 
command. mine shows how intel HD doesn't load propperly (sometimes) so i need a reboot to fix it occasionally.
 
sudo alsa reload you use when sound is gone. in your case it seems you were using the sound. don't know if this is true.

---

### Post by caneraris on 2011-04-01
as I am a new user of Ubuntu, i need somebody to show me how to reload my sound.

the sound icon appears with 3 lines. 

right click/properties/hardware - (no any hardware listed)
                                /output       - dummy output, stereo

isn't there anyone willing to show me how to fix it step by step ?

---

### Post by Crazedpsyc on 2011-04-01
Open up that terminal again and run:
```
sudo apt-get install padevchooser
```
That will install a tool useful for finding and fixing sound problems. It has fixed every single sound problem I have ever had ;)
Open it up from Applications>S&V>PulseAudio Device Chooser
Then it will appear as an icon in the top right corner of your screen.
Left-click on that icon and choose "Volume Control" from the menu.
In the "Output Devices" tab, are there any speakers listed? If so, make sure the "Port" option is set to "Analog Speakers". Then make sure everything is *UN*muted and try playing some sound. (also, try a different application like rhythmbox or banshee)

---

### Post by caneraris on 2011-04-01
Thank you for your advise. it seems to be working now. but it either might be solved by your solution or it came back temporarily after i rebooted the system. we will see..

---

### Post by caneraris on 2011-04-02
No no.. it's gone again. and this time it didnt come back after restarting. this time in sound preferences, output tab, it shows simultaneous output device. and the sound icon at the right top, the icon is normal ( not with these stupid three lines ) but there is no sound.. in hardware tab, nothing listed. I am really going crazy.. 

i think a running background program  is causing this sound issue at the moment it starts running. but i don't know which one. because sometimes after i restart there is sound. and after about half an hour or less sound goes by itself. the icon doesnt change. but no sound. and after i restart again, either the icon appears normal but no sound or the icon apears with these three lines and no sound again or it comes back temporary. i really need a solution before i throw this idiot machine and break it.

---

### Post by Crazedpsyc on 2011-04-03
Yikes! Ok, it sounds like it might be a hardware problem. have you tried with headphones or other speakers? If that doesn't work, it is probably the sound card itself. The things do wear out and quit eventually. :(
One more thing you can try (if you haven't already) is to reboot and not open firefox (or anything else using flash) to make sure it isn't flash causing the problem. If the sound seems to be working fine without flash running, open a terminal and run:
```
cd
mkdir .flash
sudo mv /usr/lib/mozilla/plugins/libflashplayer.so .flash/
```
to remove the mozilla flash plugin (it is still in a folder called .flash in your home folder if you want to restore it)
Then install gnash (follow the instructions in your other thread) and hope that it works for everything you need it for. (I believe it works with youtube)

Good luck.

---

### Post by caneraris on 2011-04-04
&#304; believe i don't need to install gnash because i think it's not flash causing the sound problem. I disabled it from firefox and chrome before i rebooted system. there was no sound again after reboot. the icon is normal as if there is sound but in preferences in hardware tab, nothing listed. in output tab, a simultaneous output ( stereo ) is listed. 

I tried with headphones and speakers, no sound.

---

### Post by Crazedpsyc on 2011-04-04
Well a cheap-o soundcard runs about $1 in the US, so I don't think that is such a bad thing ;)

---

### Post by caneraris on 2011-04-04
i might have found something ! [http://ubuntuforums.org/showthread.php?t=1558143](http://ubuntuforums.org/showthread.php?t=1558143)

Temujin wrote this in the link above.

"*When you update the kernel, you must run the AlsaUpgrade script again (with -i option)*"

Can you tell me how to do this?

I have the same sound card. i don't think any update caused my sound issue but maybe it will work with me too.

---

### Post by Crazedpsyc on 2011-04-05
I'm not exactly sure how to use the script, or how safe it is, but I can tell you how to get it

open your terminal and run:
```
git clone git://github.com/simos/alsa-upgrade.git
```
That will make a folder in the current directory (probably your home folder) named "alsa-upgrade"
cd to that directory and run:
```
sudo bash AlsaUpgrade-1.0.x-rev-1.17.sh -di
```
Make sure when it starts running that you are not downgrading alsa
it told me > You'll be upgraded from 1.0.23. to 1.0.20.
so I stopped it. (by pressing Control+C)

Another possible solution that I forgot about is 
> Actually, this appears to be a bug with permissions, I had to add myself to the audio group. I'm not sure what's causing it, but it doesn't appear to be kernel related. 
Open System>Administration>Users and Groups
then click the "Manage Groups" button, find "audio" in the list, click properties, and check your user
Although.. mine is not checked there, and audio works fine.

---

