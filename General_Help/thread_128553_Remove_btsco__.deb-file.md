---
title: "Remove btsco / .deb-file"
date: 2006-02-11
forum: General Help
---

### Post by Garyu on 2006-02-11
I have been trying to make my bluetooth headset work without prevail (Jabra BT-110). Now I have given up and want my system restored...

Something REALLY annoying is that btsco is always running, and the bluetooth sound is default which means that all of my games are muted and every time I install something that uses sound I have to change the audio settings to use my soundcard instead IF there is such a setting. In games this means no audio which is really boring. 

So, how do I remove btsco? I tried "sudo modprobe -r btsco" but that gave the response that btsco is in use. And the problem is, I installed it from a .deb file, and I don't know how to remove those. (makes you appreciate apt-get/synaptic SO much)

Alternatively, how do I change default audio device from bluetooth to soundcard?

---

### Post by dcstar on 2006-02-11
[QUOTE=Garyu]I have been trying to make my bluetooth headset work without prevail (Jabra BT-110). Now I have given up and want my system restored...
......
Alternatively, how do I change default audio device from bluetooth to soundcard?[/QUOTE]
System-Preferences-Sound
System-Preferences-Multimedia Systems Selector

---

### Post by Garyu on 2006-02-12
I have already tried this. It works for system sounds, like for error popups and the like, but my games are still muted. (americas army has no sound device selector)

---

### Post by Garyu on 2006-02-14
```
dan-erik@minotaur:~$ kill 5040
bash: kill: (5040) - Operationen inte tillåten

```

The error above means "operation not allowed" and refers to the "snd-bt-scod" daemon. Same response to "kill -9 5040". I really want this off of my system. Any ideas as to what I might try? Anyone?

---

### Post by gremlin hunter on 2006-02-14
sudo kill 5040

and dpkg -r packagename

---

### Post by angkor on 2006-02-14
If btsco is always running, does that mean you added it to /etc/modules? If so, remove it and reboot.

I've installed the driver but I didn't add it to /etc/modules, so I need to start it manually each time I wanna use it. No problems with sound here. It also isn't set to default sound device on my system, don't know what went wrong there.

btw, what made you decide to quit trying to get your headset to work? My problem was a bluetooth usb dongle with a Broadcom (the bastards!) chipset. :cry:

---

### Post by Garyu on 2006-02-14
[QUOTE=gremlin hunter]sudo kill 5040

and dpkg -r packagename[/QUOTE]

Actually, using sudo doesn't seem to do anything, the only difference is that I don't get an error, but snd-bt-scod is still running. I tried several times and triple-checked that I used the right PID. But no matter now, Angkor helped me. :)

---

### Post by Garyu on 2006-02-14
[QUOTE=angkor]If btsco is always running, does that mean you added it to /etc/modules? If so, remove it and reboot.

I've installed the driver but I didn't add it to /etc/modules, so I need to start it manually each time I wanna use it. No problems with sound here. It also isn't set to default sound device on my system, don't know what went wrong there.

btw, what made you decide to quit trying to get your headset to work? My problem was a bluetooth usb dongle with a Broadcom (the bastards!) chipset. :cry:[/QUOTE]

Of course! Hah, now I'm getting to be too used to the linux way... I can actually reboot the system... Didn't think of that. I guess I'm over my windozeness, and it only took like a month to get out of that habit. =P

Thank you for your post, I just rebooted and the damned thing wasn't running any more. Still annoying that I couldn't kill it, but hey, it's gone now. And that means I don't really have to uninstall it, so I can give this a try at a later time when I am not so frustrated. :)

I decided to quit because I tried everything that everyone said and it just didn't work. Or, actually, I just found a post suggesting to set security to "none", but they also suggested only to use it shortly until problem was fixed, and when I read it I was already sick of trying. I might try again at a later time though. But the main thing is that I got my phone working with gnome-obex-server instead of kbluetoothd, so I'm happy anyways. And now that my sound is working again I feel like I have reached Ubuntu nirvana - at least for a few minutes more. :cool:

---

### Post by angkor on 2006-02-14
[QUOTE=Garyu]Of course! Hah, now I'm getting to be too used to the linux way... I can actually reboot the system... Didn't think of that. I guess I'm over my windozeness, and it only took like a month to get out of that habit. =P
[/QUOTE]

:D

Well there probably is clean geeky way of removing modules but I don't have a clue.

I also tried to get my headset to work, no luck yet probably due to the above mentioned Broadcom chipset in my dongle. I'll try again soon with another one.

The obex-server works perfectly with gnome-bluetooth. But just today I found out that using kbluetooth and konqueror you can actually browse the contents of you phone....really nifty!

Well, glad I could be of help and I'll post back if I get the headset working.

---

### Post by angkor on 2006-02-18
Finally succeeded in getting my Jabra BT205 headset to work with skype! After trying 3 different dongles, the fourth one was the winner. It's a Sitecom CN-520 in case anyone is interested. Just make sure you get yourself a dongle with a CSR  
(Cambridge Silicon Radio) chipset and avoid Broadcom's.

---

### Post by Garyu on 2006-02-18
I actually tried once more to pair my Jabra BT-110 headset, and set the security to "none" as suggested before, and this time I got a different error message. Kbluetoothd pops up a small box with: Bluetooth monitor, Problem connecting to Jabra_BT110. LMP response timeout.

-----

EDIT: I changed security from "none" back to "auto" and suddenly it worked. Now, I tweaked around a lot of strange stuff tonight and I don't know at all what I did, so don't ask me. But amongst other things I followed an old howto on how to get nokia phones working with bluetooth. Maybe some of that did the trick, but it didn't work completely until security was set to "auto". Now it works though, and that's just great. :cool:

---

### Post by s0lid on 2006-03-25
ha! the perfect info how to remove btsco. tnx for the info. I can't make my logitech h02-v07 worked too with btsco im still waiting for newer version of btsco.:)

---

