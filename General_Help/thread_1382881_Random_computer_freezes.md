---
title: "Random computer freezes"
date: 2010-01-16
forum: General Help
---

### Post by lexe-cc on 2010-01-16
Hi,

I'm using ubuntu for over 4 years now and i'd like to say I love it! :)
However, I'm experiencing a little problem. 

Recently I bought a new computer which runs on 9.10 64bit. It's the first time I'm using the 64bit version.
It sometimes happens that my image gets all screwed up. The mouse starts to stutters as well as the audio of my system. It doesn't happen that much, but it starts to annoy me :) I googled for days now and I really can't locate the problem. If it happens again, I'll try to take a picture (or screenshot) to show you guys. I have no clue at all of what's happening. It happens really random. 

Could you guys help me to track this one down? I have a little experience with linux so I'm not a total noob, however I don't know where to look this time. Are there any useful logs I can check?

My system is:
- Ubuntu 9.10 Karmic Koala 64 bit
- Asus P6T SE motherboard (1366 socket)
- Intel i7 920 @ 2.66 ghz
- Nvidia GTX 260
- Corsair 6gb ddr3 @ 1333mhz

I haven't overclocked any of the hardware. If the system starts to stutter I usually press ctrl+alt+F1 and try to restart gdm. Sometimes if I wait too long the system hangs completely so I need to reset the computer.
I'm guessing the problem lies with Compiz Fusion but then again I've never had any problems with compiz over 4 years. I can say however that gnome-do occasionally hangs but that didn't crash the system once.

Any help would be greatly appreciated.
Thanks in advance!
Lexe

---

### Post by n0dix on 2010-01-16
If you disable Compiz has any problem? Have a error in any log file? Check the xsession-errors in $HOME.

---

### Post by gabo.cr on 2010-01-16
There could be many reasons why this is happening.
But you can read this guide in order to troubleshoot the problem:

[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

I hope that helps.

---

### Post by lexe-cc on 2010-01-17
Ok, first of all thanks for your help :)

Second, I think i may have found something. If I start to play multiple movies at the same time I get the same symptoms. I just started 6 vlc applications to play 6 divx movies. This causes the system to be almost useles. Considered my system specs this shouldn't be a problem I guess? I tried this with compiz fusion off, so I guess it's not a compiz problem .. When I try the same thing with compiz fusion on, this doesn't happen .. I'm very confused right now :)

Xsession-errors doesn't help me find the problem. 

Cheers!

---

### Post by gabo.cr on 2010-01-17
If you type this code in Terminal what service is taking more ram?

```
top
```

Or you can use the GUI under System > Administration > System Monitor.

---

### Post by lexe-cc on 2010-01-20
I haven't had the error since a while now, so I haven't been able to check the programs using the most memory. But I can tell you I probably can't check it if it happens because the system locks up pretty fast. 
Anyhow, let's hope the error has been solved by installing the automatic updates ..

---

### Post by lexe-cc on 2010-01-27
Hi, sorry for my late reply but i I haven't been home a few days. 
I've been having a lot of freezes again. After googling an searching on the forum I saw people posting their syslog. So here is mine:
(my system frooze @ +-18:25 sharp)

```
Jan 27 18:22:53 lexe-desktop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="832" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Jan 27 18:22:58 lexe-desktop anacron[1849]: Job `cron.daily' terminated
Jan 27 18:22:58 lexe-desktop anacron[1849]: Normal exit (1 job run)
Jan 27 18:24:09 lexe-desktop kernel: [  949.071484] NVRM: Xid (0003:00): 13, 0001 00000000 00008397 00001b0c 1000f010 00000080
Jan 27 18:24:10 lexe-desktop kernel: [  949.273686] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 000002ac 00000003 00000040
Jan 27 18:24:20 lexe-desktop kernel: [  959.737983] NVRM: Xid (0003:00): 8, Channel 00000003
Jan 27 18:24:20 lexe-desktop kernel: [  959.741857] NVRM: Xid (0003:00): 6, PE0001 
Jan 27 18:24:20 lexe-desktop kernel: [  959.760432] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 000002ac 00000003 00000100
Jan 27 18:24:20 lexe-desktop kernel: [  959.779073] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 000002ac 00000003 00000140
Jan 27 18:24:25 lexe-desktop kernel: [  964.792136] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 000002ac 00000003 00000100
Jan 27 18:24:25 lexe-desktop kernel: [  964.812729] NVRM: Xid (0003:00): 13, 0001 00000000 0000502d 000002ac 00000003 00000040
Jan 27 18:24:48 lexe-desktop gdm-binary[3079]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan 27 18:24:48 lexe-desktop gdm-binary[3079]: WARNING: Unable to find users: no seat-id found
Jan 27 18:24:48 lexe-desktop gdm-simple-slave[3085]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan 27 18:24:49 lexe-desktop acpid: client 1475[0:0] has disconnected
Jan 27 18:24:49 lexe-desktop acpid: client 1475[0:0] has disconnected
Jan 27 18:24:49 lexe-desktop acpid: client connected from 3086[0:0]
Jan 27 18:24:49 lexe-desktop acpid: client connected from 3086[0:0]
Jan 27 18:24:52 lexe-desktop pulseaudio[3151]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Jan 27 18:24:53 lexe-desktop pulseaudio[3151]: last message repeated 6 times
Jan 27 18:24:53 lexe-desktop pulseaudio[3242]: pid.c: Stale PID file, overwriting.
Jan 27 18:24:55 lexe-desktop pulseaudio[3242]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 6.00 dB to 6.00 dB which makes no sense.
Jan 27 18:26:24 lexe-desktop pulseaudio[3242]: last message repeated 6 times
Jan 27 18:28:58 lexe-desktop avahi-daemon[865]: Invalid query packet.
```

I guess trouble began with the first line @ Jan 27 18:24:09.

any help on tracking this down would be greatly! appreciated.
thanks in advance,

lexe

---

