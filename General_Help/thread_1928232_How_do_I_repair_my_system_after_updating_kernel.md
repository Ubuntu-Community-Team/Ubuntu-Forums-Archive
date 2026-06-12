---
title: "How do I repair my system after updating kernel?"
date: 2012-02-19
forum: General Help
---

### Post by bobdobbs on 2012-02-19
I'm running maverick on a 64bit amd system.

Every time I update the kernel, parts of the system break. It takes me hours or days to figure out how to repair my system. It's always the same parts.

I'd like to know if there are guides for fixing these parts of my system.

Most importantly: when I update the kernel, X breaks.

I'm using nvidia drivers. I believe that these have to be compiled against the current kernel. There seems to be no automatic way to do this when upgrading the system. So, when I upgrade the kernel I have to figure it out from scratch again. 

The last time I upgraded, it took me a couple of days to get my system working again. But even now, if I log out or restart, I don't have X. I have to type 'startx' from the command line.

So, is there a guide somewhere for repairing the damage to my system setup after a kernel upgrade? How can I fix X after upgrading the kernel?

---

### Post by Paqman on 2012-02-19
> **bobdobbs said:**
> 
I'm using nvidia drivers. I believe that these have to be compiled against the current kernel. There seems to be no automatic way to do this when upgrading the system.

Actually there is. If you get the Nvidia drivers using the Additional Drivers tool, the modules will be automatically rebuilt whenever you upgrade your kernel. Don't install the drivers direct from the Nvidia site.

---

### Post by gordintoronto on 2012-02-19
+1

I'm also running maverick on a 64bit AMD system with Nvidia graphics. I installed "version current" of the Nvidia driver in Additional Drivers.

When there is a new kernel, my webcam breaks, everything else is hunky dory.

---

### Post by bobdobbs on 2012-02-26
Is there a way to access the additional drivers tool from the command line?

It looks like it can be accessed from within gnome. But I can't use gnome after updating the kernel.

Also, is there a way to get X to start automatically? (Since a kernel upgrade a while ago, I have to typy 'startx' from the terminal to start gnome).

---

### Post by gordintoronto on 2012-02-26
> **bobdobbs said:**
> Is there a way to access the additional drivers tool from the command line?

No, it's a graphical program.

---

### Post by snowpine on 2012-02-26
DKMS will automagically recompile your modules when you upgrade your kernel.

```
sudo apt-get install dkms
```

You can also always choose your functional older kernel from the GRUB boot menu.

---

### Post by Paqman on 2012-02-26
> **gordintoronto said:**
> No, it's a graphical program.

Actually, you can. It has a CLI interface. To launch it:
```
jockey-text
```
To list the available drivers:
```
jockey-text --list
```
To enable a driver:
```
jockey-text -e DRIVER
```

---

### Post by bobdobbs on 2012-02-27
Cool.

A gui is no use to me. Once the kernel gets upgraded, I have to reboot and I have no access to X.

I'm about to do a dist-upgrade now. The upgrade includes new kernel headers, so there must be a kernel update in store.

I'll try to repair my system using jockey-text after I reboot following the upgrade.

If I manange to get X working again, is there a way to get gnome to start when the system boots? (Insteading of having to type startx)

---

### Post by bobdobbs on 2012-02-27
> **snowpine said:**
> DKMS will automagically recompile your modules when you upgrade your kernel.

```
sudo apt-get install dkms
```

You can also always choose your functional older kernel from the GRUB boot menu.

Using an older kernel would make updating pointless in the first place.

Does dkms really work automatically? 

I just checked, and it looks like I already have dkms on my system. But I've always had to go through a painful and difficult process to get the drivers working after kernel upgrades.

---

### Post by snowpine on 2012-02-27
Using an older kernel temporarily might give you a GUI for troubleshooting purposes, your call.

Sorry I am not a Nvidia expert. I'm surprised this is not documented on the Ubuntu wiki.

---

### Post by bluexrider on 2012-02-27
Guess I've been lucky....took Natty to kernel 3.2.4-030204-generic-pae without issues. Glad it didn't break

---

### Post by raja.genupula on 2012-02-27
Hi I hope this thing may help .
[https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)
[http://ubuntuforums.org/showthread.php?t=1036788](http://ubuntuforums.org/showthread.php?t=1036788)

---

### Post by gordintoronto on 2012-02-27
> **Paqman said:**
> Actually, you can. It has a CLI interface. To launch it:
```
jockey-text
```
To list the available drivers:
```
jockey-text --list
```
To enable a driver:
```
jockey-text -e DRIVER
```

Thanks for the correction.

---

