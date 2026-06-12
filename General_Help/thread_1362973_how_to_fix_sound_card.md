---
title: "how to fix sound card?"
date: 2009-12-23
forum: General Help
---

### Post by abhilashm86 on 2009-12-23
i checked my sound, its not playing? itseems no sound card? ```
abhilash@abhilash:~$ sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                                                                      * warning: 'alsactl store' failed with error message 'alsactl: save_state:1502: No soundcards found...'...           [fail] 
 * Setting up ALSA...                                                                                                         * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1608: No soundcards found...'...                   ...done.

```
how do i get it wroking back?

---

### Post by taurus on 2009-12-23
Is it an integrated or an add-on soundcard?  Does it show up when you run this command from a terminal?

```
lspci
```

---

### Post by abhilashm86 on 2009-12-23
> **taurus said:**
> Is it an integrated or an add-on soundcard?  Does it show up when you run this command from a terminal?

```
lspci
```

i think its nvidia, what happened was, headphones were not working, i killed all pulseaudio and then reinstalled. But now there is no sound hardware?
its not recognising........
```
abhilash@abhilash:~$ lspci
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7050 / nForce 610i] (rev a2)
01:06.0 Communication controller: Agere Systems Lucent V.92 Data/Fax Modem
abhilash@abhilash:~$ 

```

---

### Post by abhilashm86 on 2009-12-23
see this attached screenshot, there is no hardware its telling?
i checked with system->administrator->Hardware drivers, but it did not detect........

please help how to detect and settle this sound issue!! i'm going mad without sound:(

```
abhilash@abhilash:~$ aplay -l
aplay: device_list:223: no soundcards found...
abhilash@abhilash:~$ 
 
```
is this means, my kernel is not detecting sound card!! omg, how to make it recognise??

---

### Post by bodhi.zazen on 2009-12-24
Lots of suggestions in this thread :

[[ubuntu] No sound after upgrade to Karmic Koala 9.10 - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1308550") 

If no sound cards are detected, reboot =)

---

### Post by abhilashm86 on 2009-12-24
my pulse audio is not opening because the sound cards is not detected? can anyone tell how to make ubuntu detect sound card and do the job?
```
abhilash@abhilash:~$ pulseaudio & pavucontrol
[1] 3907
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:3908): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
abhilash@abhilash:~$ pulseaudio & pavucontrol
[1] 3923
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:3924): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
abhilash@abhilash:~$ alsamixer -Dhw

alsamixer: function snd_ctl_open failed for hw: No such file or directory
abhilash@abhilash:~$ 

```

---

### Post by bodhi.zazen on 2009-12-24
you are still having problems after rebooting ?

---

### Post by abhilashm86 on 2009-12-24
> **bodhi.zazen said:**
> you are still having problems after rebooting ?

i got oss as default, still there is no sound card detected!! but sound is working with oss as deafult, thanks........

---

