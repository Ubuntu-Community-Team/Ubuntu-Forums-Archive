---
title: "Having issues in 9.10"
date: 2010-01-05
forum: General Help
---

### Post by ShadowRavenWings on 2010-01-05
I'm currently running Ubuntu 9.10 and I've been having problems with it since I upgraded (in November). Programs have been crashing and my computer froze completely a few times and I had to restart it. It also seems to think that I have no free space on my hard drive, even though a few days ago I had over 20 GB and I've hardly changed anything. As of today, I can't seem to watch videos online either. Usually I can do it, but sometimes the sound doesn't work and I have to restart Firefox to fix it. It was also having problems earlier with loading images, but restarting seems to have solved that as well.

I've suspected for a while now that there might be a problem with the onboard graphics on my motherboard, because the colors on the screen always seem wrong and I've switched the monitors twice, but it doesn't make a difference. Could that be related to my other issues? Is there any way I can test that? Should I try installing a new video card? Reinstall Ubuntu?

---

### Post by ticthak@AOL.com on 2010-01-05
crashing after updating seemms for 1 thing to frequently have to do w/ drivers- your graphics problems seem diagnostic. Try to install the correct drivers for your hardware (check System>>Administration) before abandoning hope.

---

### Post by fancypiper on 2010-01-05
What is your video card?  If you don't know, try this command:

sudo lshw | less

Scroll down to find the video chipset.

Please report the result of this command:

df -h

You may recover space by removing the cached .deb files in /var/cache/apt/archives.  Launch synaptic and explore the options and you should find an option to remove the cached files after installing.

---

### Post by Cue2 on 2010-01-06
> **fancypiper said:**
> What is your video card?  If you don't know, try this command:

sudo lshw | less

Scroll down to find the video chipset.

Please report the result of this command:

df -h

You may recover space by removing the cached .deb files in /var/cache/apt/archives.  Launch synaptic and explore the options and you should find an option to remove the cached files after installing.

I too get a complete freeze now and then. 9.04 worked fine until the 9.10 upgrade I performed. My graphics card is an ATI 3870X2. 

Shadowravenwings does your mouse also turn off? My laser mouse turns off when ubuntu crashes and I'm contemplating whether to get a new mouse or not just in case it's the usb mouse.

Don't know if this was the part you are looking for
```
 *-display UNCLAIMED
                      description: Display controller
                      product: R680 [Radeon HD 3870 x2]
                      vendor: ATI Technologies Inc
                      physical id: 0
                      bus info: pci@0000:03:00.0
                      version: 00
                      width: 64 bits
                      clock: 33MHz
                      capabilities: pm pciexpress msi bus_master cap_list
                      configuration: latency=0
                      resources: memory:c0000000-cfffffff(prefetchable) memory:fe8f0000-fe8fffff ioport:b000(size=256) memory:fe8c0000-fe8dffff(prefetchable)
```

```

/dev/sda5              30G  3.6G   25G  13% /
udev                  4.0G  320K  4.0G   1% /dev
none                  4.0G  220K  4.0G   1% /dev/shm
none                  4.0G   84K  4.0G   1% /var/run
none                  4.0G     0  4.0G   0% /var/lock
none                  4.0G     0  4.0G   0% /lib/init/rw
```

---

### Post by fancypiper on 2010-01-06
Cue2, You still have 25 GB free space on your / partition. You can check to see if you have the video card driver installed with:

lsmod | less

---

### Post by Cue2 on 2010-01-06
> **fancypiper said:**
> Cue2, You still have 25 GB free space on your / partition. You can check to see if you have the video card driver installed with:

lsmod | less

seems like radeon drivers are installed. Other than the general freezing after a 9.10 upgrade my and ShadowRavenWings' problem are probably unrelated so my apologies for somewhat thread hijacking. I will still follow this thread just in case it turns out to be something else other than the disk space or graphics drivers. I'll also be sure to post here if I find the cause of my machine freezing.

thanks for the help fancypiper.

---

### Post by ShadowRavenWings on 2010-01-07
This is what comes up for sudo lshw | less:

    ```
 *-display
          description: VGA compatible controller
          product: C61 [GeForce 6150SE nForce 430]
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list rom
          configuration: driver=nvidia latency=0
          resources: irq:22 memory:fb000000-fbffffff memory:e0000000-efffffff(prefetchable) memory:fc000000-fcffffff memory:40000000-4001ffff(prefetchable) 
```

and df -h:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G  108G     0 100% /
udev                  438M  280K  438M   1% /dev
none                  438M   55M  384M  13% /dev/shm
none                  438M  200K  438M   1% /var/run
none                  438M     0  438M   0% /var/lock
none                  438M     0  438M   0% /lib/init/rw
/dev/sdb1             299G   24G  275G   8% /media/TOSHIBA EXT_
```

I actually deleted almost 20 GB of files from my hard drive yesterday and moved some stuff to my external drive, which seemed to work, but today it says I have no space again. And I'm pretty sure I have the video drivers installed as well.

---

### Post by fancypiper on 2010-01-07
You should have the nVidia graphics drivers

Clicky System>Administration>Hardware drivers
should guide you through the installation (after you recover some disk space).

Have you tried these tips?

[HOWTO: Recover Lost Disk Space]("http://newyork.ubuntuforums.org/showthread.php?p=7053432")

These commands remove unnecessary .deb files:
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

---

### Post by ShadowRavenWings on 2010-01-07
I do have the Nvidia drivers, and I tried all of those commands and moved some more files over to the external hard drive, but I'm still getting messages saying I have no free disk space.

---

### Post by fancypiper on 2010-01-07
I'm out of ideas.

Examine your logs carefully and see if you can find any hints.

Clicky System>Administration>Log File Viewer

---

### Post by ezsit on 2010-01-07
You could try the du command - disk usage:

sudo du /tmp -h
sudo du /var -h

Those are the two most likely candidates for filesystem growth beyond reason.

---

### Post by Sawer on 2010-01-07
I'm trying to get my Brother MFC-495CW scanner to work in 9.10. The  Brothers website said to add 2 lines to udev rules.d rule 40 libsane. There are only 2  rules in /etc/udev/rules.d where cane I get  the ones I need  or how do I generate them?
Thanks

---

### Post by fancypiper on 2010-01-07
> **Sawer said:**
> I'm trying to get my Brother MFC-495CW scanner to work in 9.10. The  Brothers website said to add 2 lines to udev rules.d rule 40 libsane. There are only 2  rules in /etc/udev/rules.d where cane I get  the ones I need  or how do I generate them?
ThanksPlease make a new post and don't hijack threads.

---

