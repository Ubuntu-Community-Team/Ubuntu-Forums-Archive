---
title: "ubuntu 12.04 does not shutdwon/power off"
date: 2012-05-02
forum: General Help
---

### Post by zozonmr on 2012-05-02
Hi,

I have a rather unusual problem with Ubuntu 12.04 LTS. Unusual meaning that I have not met this problem before. I installed Ubuntu 12.04 32 bit next to an existing Windows XP on an HP micro Tower stationary computer with Nvidia graphic card. Everything works like clockwork but the shut down and power off! When I try to shut down it just hangs and typing F2/F1 does not display any errors. I tried couple of things among others the modifying the grub file to "acpi=force" or simply nothing "". But it didnt help. 
When shutting off once it displayed the following message:
"could not write bytes: broken pipe" 

Does anybody have an idea how to solve this?

---

### Post by Steven D on 2012-05-03
Hi! I just had this issue on my ASUS U36JC laptop. By any chance did you install a package called "laptop-tools"? Basically it changes certain hardware settings to get maximum battery life. Not sure if it can be installed on a desktop, but aggressive power management was my issue.
One of the settings it had enabled was "SATA link power management" on dev/sda
It was the culprit for me.
Of course your issue may differ, but you have the same symptoms.
You could try a program called "powertop" either from synaptic or the software center.
Once installed, it runs by "sudo powertop" move to the left tab named "Tunables" with the arrow keys, and look for anything which says "good" basically it's "good" for power saving, but can cause issues. use enter key to change values. If they reset after a logout or restart, there may be something else like the previously mentioned "laptops-tools" re-enabling it.

---

### Post by Zvlwab on 2012-05-03
I have the same problem when I try to shut down using
```
sudo halt
```

But my computer does shutdown correctly when I navigate there using the XFCE menu.

This affects both my laptop and pc.

So have you tried shutting down in several ways?

---

### Post by Zvlwab on 2012-05-03
Take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1968626](http://ubuntuforums.org/showthread.php?t=1968626)

---

### Post by zozonmr on 2012-05-03
Hi,

I tried the powertop power management tool and I changed and I changed the good to bad in the "tunabels" but unfortunatly didn't work. The only thing installed connected to laptops is the laptop-detect. here are the things which didnt work:
sudo poweroff
sudo shutdown -h
sudo halt  
I tried to look for some error message while shutting down but the only thing displayed was that the system is stopping hardware clocks and other things then surprisingly starting them again. So in tty1 I press ctrl-alt-delete twice and strangely enough the system restarted.    checking powertop again the variables were changed back to good from bad so I have to find what changed them back. I will now go through the thread Zvlwab suggested. **Thank you for the help**.

---

### Post by zozonmr on 2012-05-03
Hi again,

So changing the files in 
/etc/rc0.d and rc6.d: - S31umountnfs.sh to S05umountnfs.sh
- S35networking to S15networking
 did not work either. 
'sudo halt -p' didnt work either.

---

### Post by zozonmr on 2012-05-03
Hi,

I found something which worked fine. I typed this into the terminal:

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop


This worked just fine. I wonder whether there is an easier solution to this problem. But for the time being I am going to use this. Thanks for the tips and helps!

---

### Post by zozonmr on 2012-05-03
Hi,

Another issue is what I just realized now that I can not create a launcher for the bash script containing the shutdown command. I am not sure why this is. Has this been removed from ubuntu 12.04?

---

### Post by Steven D on 2012-05-04
A program i frequently use "Ubuntu tweak" [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
has a section "scripts" under admins menu, copy the "create launcher" script. This adds the create launcher to right click again.

---

