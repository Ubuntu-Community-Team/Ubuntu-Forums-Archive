---
title: "Audio Problems With Ubuntu 9.10"
date: 2009-11-02
forum: General Help
---

### Post by Gp. on 2009-11-02
Basically, the audio is stable for about 5-10 seconds, then it just turns to static. If I go to the volume slider and change the value, or enter the sound preferences area, the static stops but then comes back again after a short while. This keeps repeating and it's driving me insane.

To explain, if my stereo has no input or whatever from my computer, static noise just comes out. It's almost like Ubuntu is putting my sound output into standby because there is no sound coming out.

I don't know what it is, but it won't stop. I'm giving up on another round of Ubuntu if I can't fix this.

Bloody hell, they just fixed the softreset bug for my motherboard and I was impressed by that, and the new UI for the loading and all that, then I get in here and I have a lovely new issue which probably won't be fixable so I'll have to give up until the next release...

Can anybody help me? :(

---

### Post by P4man on 2009-11-02
what soundcard do you have?
If you're not sure post the output of lspci

You could try installing gnome-alsamixer and mute all channels you dont need, but it sounds like its something else than that. Perhaps try this.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

If the last line looks like this:
```

# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

comment the last line out:

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N

```

save, reboot, cross fingers.

---

### Post by Giblet5 on 2009-11-02
Bring up a terminal window and enter ```
alsamixer
```

(use arrow keys to navigate)

Turn down the volume on "CD Input", "Mic", "Aux", "Line", and any other input that is not "PCM", "Front", "Balance", or "Master".

Let it sit a bit.

Did that fix it? If so, you owe me coffee now. That's the law.

---

### Post by Gp. on 2009-11-02
P4man, you are a legend. That fixed the problem!

Giblet5, coffee another time? lol

---

### Post by kyuubi777 on 2009-11-03
P4man, arigato gozaimashita!!!! had the same issues, worked perfectly, was a little hesitant on boot up because my login screen didn't make the usual noises, but once in the system i just had to turn the sound up ...lol 
many thanks

---

### Post by suzypeppercorn on 2009-11-04
> **P4man said:**
> what soundcard do you have?
If you're not sure post the output of lspci

You could try installing gnome-alsamixer and mute all channels you dont need, but it sounds like its something else than that. Perhaps try this.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

If the last line looks like this:
```

# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```

comment the last line out:

```
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N

```

save, reboot, cross fingers.

worked like a charm! Thanks for the help! :p

---

### Post by P4man on 2009-11-05
Everyone that has this problem and gets it solved by disabling  "options snd-hda-intel power_save=10" is kindly requested to report in this bug:


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)

And post your machine specs (attach output of lspci) so this bug can be properly fixed for your machine, and everyone else who has the same machine.

gracias.

---

### Post by rexmo on 2009-11-13
Reported.

Thank you very much P4man!

---

### Post by berserkpi on 2009-11-27
Hi there, my problem is the same, the sound is just death. This is my situation:

1) I installed a fresh Ubuntu 9.10. Firstly there was no problem with the sound, but sometimes happened that it just not worked, so just reboot and if I'am in a lucky day it works, but most of the time it doesn't :(. There is no error message on this.

2) My alsamixer
[http://picasaweb.google.com/lh/photo/IEKKl2ksg1GZYecfjzTJxA?feat=directlink]("http://picasaweb.google.com/lh/photo/IEKKl2ksg1GZYecfjzTJxA?feat=directlink")

[IMG]http://lh3.ggpht.com/_PMwNetnvoRA/SxBs7HJ-7oI/AAAAAAAAADU/xfSezktgdCQ/s400/snapshot2.png[/IMG]

3)Multimedia - System Settings
[http://picasaweb.google.com/lh/photo/qBsHQjAvQnxvPfuGVpAEEw?feat=directlink]("http://picasaweb.google.com/lh/photo/qBsHQjAvQnxvPfuGVpAEEw?feat=directlink")

[IMG]http://lh4.ggpht.com/_PMwNetnvoRA/SxBs7SJGEFI/AAAAAAAAADY/EVQEUlG1S28/s400/snapshot1.png[/IMG]

Sometimes when I click the test buttom it works!!, but sometimes not :( -and I get no error message at all-. So, it is extrange.

4) I've already changed my **alsa-base.conf**

```
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Power down HDA controllers after 10 idle seconds
# options snd-hda-intel power_save=10 power_save_controller=N
```

5) ```
lspci -v
```

output:

```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Device 01f1                                                      
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes                                                                
        Interrupt: pin A routed to IRQ 21                                                                    
        Region 0: Memory at febfc000 (64-bit, non-prefetchable) [size=16K]                                   
        Capabilities: <access denied>                                                                        
        Kernel driver in use: HDA Intel                                                                      
        Kernel modules: snd-hda-intel 
```


I hope u can help me. Life is an error without music :P. Wut can I do to solve this problem guys?

Thanks in advance.

---

### Post by c0rrupt0r on 2010-04-23
I have been trying to fix this for weeks now and nothing seemed to have worked till today, 
with my crackling and popping sound on ubuntu 9.10, using logitech usb head set.
I have even had this problem on my Intel sound card.

If I right click on my speaker icon on my panel and go to sound preferences then to output tab, go down to the balance bar and move it a little to the right side and it does fix the crackling and popping and messed up sound on all music files/youtube/games and etc.
hope this helps others also. 

seems something is wrong with that setting.

---

