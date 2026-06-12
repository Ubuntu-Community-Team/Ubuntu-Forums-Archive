---
title: "Fresh installation of Kubuntu takes too long to boot"
date: 2006-02-14
forum: General Help
---

### Post by octopus on 2006-02-14
Hello eberybody.

I've recently istalleng Kubuntu on my desktop and realized, that it takes to much time to boot (form selecting what to boot in grub to kdm login screen). Examining dmesg gave me nothing, there are no errors or something. I must notice, that booting process does not stall on some stage and then continue, it is slow all the time.

Where should I seek cause of this unpleasant thing?

P.S. Sorry for my bad english

---

### Post by syklitengutt on 2006-02-14
what is too long time?

---

### Post by octopus on 2006-02-14
[QUOTE=syklitengutt]what is too long time?[/QUOTE]
two or three times longer than my laptop with kubuntu installed, something about 4-5 minutes

for example my gentoo system takes about 1,5 minutes to boot on the same desktop

---

### Post by ace2005 on 2006-02-14
[QUOTE=syklitengutt]what is too long time?[/QUOTE]

Anything slower than windows :twisted:

but seriously its slow and very annoying, just sitting there waiting for it to startup

---

### Post by Brando569 on 2006-02-14
id say either disable the splash and see what it stalls on or if anything goes wrong and/or enable the bootlog daemon, also in the customization section theres a thread that tells you what to disable so that your system will boot quicker. hope that helps

---

### Post by octopus on 2006-02-15
I've read the thread you've mentioned, thank you, but I knew how do that before reading it. It's not a problem to speed up the booting process a little bit, problem is that I just can't understand why it is initially so slow.

---

### Post by octopus on 2006-02-15
[QUOTE=ace2005]but seriously its slow and very annoying, just sitting there waiting for it to startup[/QUOTE]

Sounds strange - all linux installations I've evere had booted much faster than windows. Maybe you have the same problem?

---

### Post by ace2005 on 2006-02-16
[QUOTE=octopus]Sounds strange - all linux installations I've ever had booted much faster than windows. Maybe you have the same problem?[/QUOTE]

Its the opposite for me, Windows XP with only graphics card, soundcard and USb Modem drivers and the rest being microsoft's with a trimmed set of services running with NOD 32 for antivirus and Sygate (stupid symantec) as a firewall works very well and its fast.

Time for Win XP to boot to desktop and load all apps running on boot and for me to click on the sygate icon in the sys tray and for the window to come up: 

41!!!! seconds

Time for Kubuntu to boot to desktop (autologin so i never typed the password) 

1 min 43 seconds

At 41 seconds ubuntu was just starting to load hotplug

:cry:

---

### Post by K0LO on 2006-02-16
> [SIZE="1"]Its the opposite for me, Windows XP with only graphics card, soundcard and USb Modem drivers and the rest being microsoft's with a trimmed set of services running with NOD 32 for antivirus and Sygate (stupid symantec) as a firewall works very well and its fast.

Time for Win XP to boot to desktop and load all apps running on boot and for me to click on the sygate icon in the sys tray and for the window to come up: 

41!!!! seconds

Time for Kubuntu to boot to desktop (autologin so i never typed the password) 

1 min 43 seconds

At 41 seconds ubuntu was just starting to load hotplug[/SIZE]

Agreed!

For me, Windows XP boot time -- 30 sec
Kubuntu boot time -- 3 minutes

One of the reasons for the slower boot time with Linux is that I'm using Reiser File System on 2 large HDDs, so it takes time to check the journal at startup.

But... we're not being helpful to the original poster. One thing I'd do is measure the transfer rate of your boot hard disk:

sudo hdparm -tT /dev/hda  (or sda, or whatever your disk is named).

A good 7200 rpm hard drive should measure near 60 MB/sec. If the transfer rate is slow, then maybe it's not using DMA properly. It's something to check....

---

### Post by figueiravasco on 2007-10-22
I do have this problem with Kubuntu 7.10 as well (nearly 3 minutes to boot). I can't figure out what happened :(
Almost downgrading to Feist, unfortunately...

---

### Post by figueiravasco on 2007-10-23
I have found a palliative to this problem: alterate "splash" directive on boot to "nosplash". You lose the fancy screen written "(k)ubuntu", but the horrible bootload time issue gets normal again...

---

