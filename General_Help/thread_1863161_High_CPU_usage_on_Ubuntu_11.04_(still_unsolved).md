---
title: "High CPU usage on Ubuntu 11.04 (still unsolved)"
date: 2011-10-17
forum: General Help
---

### Post by Cordess on 2011-10-17
I have a fresh Install of Ubuntu 11.04 on my Core2Duo computer, but i have a high CPU load of over 60 % on both cores in IDLE mode.
No process shows up in top or htop that takes up 60 % of the two cores.


There was another thread yesterday, but the solution that were mentioned, **DOESN'T solve the problem**. So the problem is still unsolved.
[http://ubuntuforums.org/showthread.php?t=1746327](http://ubuntuforums.org/showthread.php?t=1746327)


It doesn't help to remove gnome-system-monitor, top and htop still show a high CPU load of 60 %, but no process running with that high load.


Someone mentioned in the other thread to update the NVidia driver to driver version 173, but that won't help, because i have a Geforce GTX 550 TI video card in my computer that requires a NVidia driver version 270 and newer.
At the moment driver version 270.41.06 is installed.
This is the driver that get's installed, when using the Ubuntu additional hardware install tool.
So if this is still a driver problem, then it must be fixed in the repository when a newer driver is required.

---

### Post by oneadvent on 2011-10-17
Odd question: did you watch top for a few minutes, sometimes it doesn't immediately organize itself. 

If the CPU is being used it should be able to see it on top

---

### Post by Cordess on 2011-10-17
Yes, i did.

I also can hear the CPU higher load, because the CPU fan is spinning on max rotation speed.

This is not the case, when the CPU is really idle.
To make the CPU idle i have to logout from the Desktop and login on a console without X. Then top shows normal CPU loads of < 2 % in IDLE mode and the CPU fan is quiet.

Here's an example output of top. 
Look at the CPU(s) and %id Value.
```

top - 19:41:47 up 41 min,  2 users,  load average: 0.58, 0.68, 0.60
Tasks: 162 total,   5 running, 156 sleeping,   0 stopped,   1 zombie
Cpu(s): 50.2%us,  9.7%sy,  0.0%ni, 39.3%id,  0.2%wa,  0.0%hi,  0.7%si,  0.0%st
Mem:   8192796k total,  2244580k used,  5948216k free,    58664k buffers
Swap:  9454216k total,        0k used,  9454216k free,  1160244k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1734 cordess    20   0  757m 169m  27m R    8  2.1   3:16.62 nautilus           
 6357 cordess    20   0 1021m 243m  36m R    6  3.0   2:29.70 firefox            
  999 root      20   0  165m  48m  19m S    4  0.6   2:58.20 Xorg               
 1723 cordess     9 -11  306m 7456 5012 S    3  0.1   0:27.34 pulseaudio         
28257 cordess    20   0  153m  14m 6164 R    3  0.2   0:00.09 evince-thumbnai    
 6606 cordess    20   0  216m  51m  17m S    2  0.6   0:22.77 npviewer.bin       
 1720 cordess    20   0  387m  40m  23m R    2  0.5   0:30.63 compiz             
 1692 cordess    20   0 26044 2348  660 S    1  0.0   0:25.71 dbus-daemon        
  833 root      20   0     0    0    0 S    0  0.0   0:00.16 kjournald          
 1654 cordess    20   0  235m 8672 6584 S    0  0.1   0:04.68 gnome-session      
 1708 cordess    20   0 57760 2740 2156 S    0  0.0   0:03.40 gvfsd              
 1737 cordess    20   0  443m  21m  14m S    0  0.3   0:06.82 gnome-panel        
 1766 cordess    20   0  183m  19m 7148 S    0  0.2   0:03.20 zeitgeist-daemo    
 1881 cordess    20   0  333m 7004 5356 S    0  0.1   0:10.63 indicator-sound    
 1883 cordess    20   0  202m 4764 3680 S    0  0.1   0:02.02 indicator-appli  
```


And this is the output of htop sorted by CPU load. 
The processes only consume < 7 %, but both cores of the CPU are up at over 60 %.
I assume it is a kernel or driver related problem.
```


  1  [||||||||||||||||||||     63.4%]     Tasks: 110, 175 thr; 2 running
  2  [|||||||||||||||||||      59.5%]     Load average: 0.39 0.57 0.57 
  Mem[||||||||||          991/8000MB]     Uptime: 00:43:55
  Swp[                      0/9232MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 1734 cordess    20   0  757M  169M 27940 S  7.0  2.1  3:27.34 nautilus
  999 root      20   0  166M 50236 21240 S  4.0  0.6  3:07.78 /usr/bin/X :0 -nr
25790 cordess    20   0  757M  169M 27940 S  3.0  2.1  0:17.83 nautilus
 6357 cordess    20   0 1002M  227M 37660 S  3.0  2.8  2:40.36 /usr/lib/firefox-7
 1723 cordess     9 -11  306M  7456  5012 S  3.0  0.1  0:31.89 /usr/bin/pulseaudi
 1768 cordess    -6   0  306M  7456  5012 S  3.0  0.1  0:26.91 /usr/bin/pulseaudi
 6606 cordess    20   0  216M 52312 17608 S  1.0  0.6  0:25.49 /usr/lib/nspluginw
29008 cordess    20   0 19864  1624  1180 R  1.0  0.0  0:00.59 htop
 1720 cordess    20   0  390M 41616 23996 S  1.0  0.5  0:32.71 /usr/bin/compiz
 1692 cordess    20   0 26044  2348   660 S  0.0  0.0  0:27.16 //bin/dbus-daemon
28007 cordess    20   0  395M 16988 12140 S  0.0  0.2  0:00.72 gnome-terminal
28292 cordess    20   0  435M 25100 16248 S  0.0  0.3  0:01.38 gedit
    1 root      20   0 24116  2188  1336 S  0.0  0.0  0:00.56 /sbin/init
  330 root      20   0 17184   904   588 S  0.0  0.0  0:00.07 upstart-udev-bridg
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

```

the following modules are loaded:
```

lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
vesafb                 13761  1 
snd_hda_codec_hdmi     28167  4 
snd_emu10k1_synth      17244  0 
snd_emux_synth         42834  1 snd_emu10k1_synth
snd_seq_virmidi        13525  1 snd_emux_synth
snd_seq_midi_emul      13706  1 snd_emux_synth
lnbp21                 12938  1 
stb6100                13791  1 
stb0899                41335  1 
snd_emu10k1           156895  12 snd_emu10k1_synth
snd_ac97_codec        134270  1 snd_emu10k1
snd_hda_intel          33176  0 
nvidia              10709116  38 
snd_usb_audio         112426  1 
ac97_bus               12730  1 snd_ac97_codec
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_hda_codec         103804  2 snd_hda_codec_hdmi,snd_hda_intel
ir_lirc_codec          12898  0 
snd_seq_midi           13324  0 
lirc_dev               19232  1 ir_lirc_codec
snd_pcm                96391  9 snd_hda_codec_hdmi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_rawmidi            30486  4 snd_seq_virmidi,snd_emu10k1,snd_usbmidi_lib,snd_seq_midi
ir_sony_decoder        12549  0 
snd_util_mem           14074  2 snd_emux_synth,snd_emu10k1
snd_hwdep              13604  4 snd_emux_synth,snd_emu10k1,snd_usb_audio,snd_hda_codec
snd_seq_midi_event     14899  2 snd_seq_virmidi,snd_seq_midi
joydev                 17606  0 
ir_jvc_decoder         12546  0 
snd_seq                61621  5 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_midi,snd_seq_midi_event
snd_timer              29602  6 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14462  5 snd_emu10k1_synth,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17113  0 
snd                    67382  33 snd_hda_codec_hdmi,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_pcm,snd_rawmidi,snd_hwdep,snd_seq,snd_timer,snd_seq_device
ir_rc6_decoder         12546  0 
lp                     17825  0 
uvcvideo               72195  0 
mantis                 23328  0 
mantis_core            40423  1 mantis
parport_pc             36959  1 
parport                46458  3 ppdev,lp,parport_pc
dvb_core              110487  1 mantis_core
videodev               82052  1 uvcvideo
emu10k1_gp             12646  0 
wacom                  42238  0 
soundcore              12680  1 snd
gameport               19652  2 emu10k1_gp
ir_rc5_decoder         12546  0 
v4l2_compat_ioctl32    17078  1 videodev
ir_nec_decoder         12546  0 
rc_core                26918  7 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,mantis_core,ir_rc5_decoder,ir_nec_decoder
snd_page_alloc         18529  3 snd_emu10k1,snd_hda_intel,snd_pcm
firewire_ohci          40370  0 
firewire_core          62646  1 firewire_ohci
usbhid                 46956  0 
hid                    91020  1 usbhid
crc_itu_t              12707  1 firewire_core
pata_jmicron           12747  0 
r8169                  48022  0 
ahci                   25951  4 
libahci                26642  1 ahci

```

and glxinfo shows:
```

glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
...
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCI/SSE2
OpenGL version string: 4.1.0 NVIDIA 270.41.06
OpenGL shading language version string: 4.10 NVIDIA via Cg compiler

```


EDIT:

I also want to mention, that i also tested Ubuntu 11.04 in classic mode without effects by using Metacity instead of compiz, but this also didn't help.
So compiz is not the reason for the high CPU load.

---

### Post by oferfrid on 2011-10-19
had the same problem, fixed it by removing the Google desktop.

```

sudo apt-get remove google-desktop-linux 

```

---

### Post by Cordess on 2011-10-19
I don't have google-desktop installed.
So this isn't the problem.


But i found it by switching to XFCE, the problem is **nautilus**.

But if i start XFCE, nautilus get's started too and then it raises the CPU usage again.
To solve that i needed to login into a command line console and delete the files with the name:
/home/USERNAME/.config/session-state/nautilus*


I also needed to delete all nautilus entrys in the files in the /home/USERNAME/.cache/sessions folders.
Try this to find them:
grep -i nautilus ~/.cache/sessions/*


Now i have a XFCE session with a low CPU usage and no nautilus process running.


But i don't like this circumvention very much, it is not a real solution, because i can't use the Gnome 2 desktop anymore.

It's definitly a bug in Ubuntu 11.04 and the nautilus packet.

---

### Post by andisl on 2011-10-20
> **oferfrid said:**
> had the same problem, fixed it by removing the Google desktop.

```

sudo apt-get remove google-desktop-linux 

```

Hello!

For me it was also a problem of Google desktop. When I stopped it, CPU use dropped to 10-20%. However, it is only XUBUNTU and LUBUNTU desktop relevant. In Ubuntu 2D desktop (11.10) on the same machine (Acer Aspire 7736ZG) use of CPU is normal with Google Desktop launched.

---

### Post by Cordess on 2011-10-20
Keep in mind that Ubuntu 11.10 is a completly different version and different system.

Ubuntu 10.10 is running Gnome 3 with new APIs like gtk+ 3.0.
Ubuntu 10.04 is running Gnome 2 with the older 2.x gtk+ API.

This thread is about Ubuntu 10.**04**

---

### Post by SingingBush on 2012-12-30
I know this thread is ancient but the gnome-system-monitor issue that is causing problems for some other users still exists in Ubuntu 12.10 (quantal).

I've added a comment on [the launchpad bug report that was reported in 2007]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/93847"). Like a few of the other users that have reported the problem, I am using a system with a Core2 Duo processor so it could possibly be hardware specific.

If anyone else has this issue please add to the launchpad bug as this problem has been known about for over 5 years.

---

### Post by mloayza on 2013-04-20
Hello. 
I have a similar issue with my ubuntu 12.10. Firstly I installed a previous version of xorg because another thread says it could help because of video drivers were not prepared for the current version of xorg in 12.10. but the problem araise when I use Firefox,  opera,  eclipse+java or other application who depends of gnome3 desktop. Also I'm using openbox desktop because initially gnome desktop heat my laptop very quickly. 
I think the problem is related to video driver and kernel version, so the solution will be use another linux box or previous version of ubuntu like < 10.04.
Warm regards.

---

### Post by overdrank on 2013-04-20
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

