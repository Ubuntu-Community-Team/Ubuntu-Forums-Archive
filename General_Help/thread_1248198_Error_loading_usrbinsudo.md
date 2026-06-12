---
title: "Error loading /usr/bin/sudo"
date: 2009-08-23
forum: General Help
---

### Post by rongyihit on 2009-08-23
Hi!
   I input a command in terminal which should run in sudo  authority, but the terminal says that: Error loading /usr/bin/sudo. What is wrong and how to solve the problem. Please someone can help me. Thanks!

---

### Post by Rocket2DMn on 2009-08-23
Can you please copy and paste the entire error here?

---

### Post by rongyihit on 2009-08-23
> **Rocket2DMn said:**
> Can you please copy and paste the entire error here?
The entire error is Error loading /usr/bin/sudo.

---

### Post by Rocket2DMn on 2009-08-23
Hmm, that's not very helpful.  Did you just install Ubuntu, or is this a new problem on a system that was previously working?  Have you made any recent changes to your system?  We can try running fsck on your partition at boot to see if it detects/fixes anything.  If you want to do that, run
```
sudo touch /forcefsck
```
Then reboot your system and the disk check will run during the boot sequence.

---

### Post by rongyihit on 2009-08-23
> **Rocket2DMn said:**
> Hmm, that's not very helpful.  Did you just install Ubuntu, or is this a new problem on a system that was previously working?  Have you made any recent changes to your system?  We can try running fsck on your partition at boot to see if it detects/fixes anything.  If you want to do that, run
```
sudo touch /forcefsck
```Then reboot your system and the disk check will run during the boot sequence.
How foolish I am. I deleted the executable sudo in /usr/bin, intended to reinstall sudo. However, when I input apt-get install sudo, the terminal said: sudo is already the newest nersionl.:( What should I do?

---

### Post by Rocket2DMn on 2009-08-23
Are you still able to use gksudo?  See if you can access System->Administration->Synaptic Package Manager, then try to reinstall sudo from there (Mark for Reinstallation by right clicking).
Alternatively, if you have a LiveCD, you can to boot from that, mount your real partition (say at /media/realdrive), then copy over the sudo binary from there.

On the LiveCD, where sudo will work:
```
sudo mkdir /media/realdrive
sudo mount -t ext3 /dev/sda1 /media/realdrive
sudo cp /usr/bin/sudo /media/realdrive/usr/bin/sudo
```
Where sda1 is your root partition.  To check your partitions, run
```
sudo fdisk -l
```

For future reference, don't ever just delete binaries.  Programs are almost always uninstalled using a package manager (apt-get or aptitude from the terminal, or Synaptic Package Manager graphically).

---

### Post by Rocket2DMn on 2009-08-23
Oh, and then we need to set the correct permissions on it with suid (in case it doesn't carry over):
```
sudo chown root:root /media/realdrive/usr/bin/sudo
sudo chmod 755 /media/realdrive/usr/bin/sudo
sudo chmod +s /media/realdrive/usr/bin/sudo
```

---

### Post by rongyihit on 2009-08-23
> **Rocket2DMn said:**
> Are you still able to use gksudo?  See if you can access System->Administration->Synaptic Package Manager, then try to reinstall sudo from there (Mark for Reinstallation by right clicking).
Alternatively, if you have a LiveCD, you can to boot from that, mount your real partition (say at /media/realdrive), then copy over the sudo binary from there.

On the LiveCD, where sudo will work:
```
sudo mkdir /media/realdrive
sudo mount -t ext3 /dev/sda1 /media/realdrive
sudo cp /usr/bin/sudo /media/realdrive/usr/bin/sudo
```Where sda1 is your root partition.  To check your partitions, run
```
sudo fdisk -l
```For future reference, don't ever just delete binaries.  Programs are almost always uninstalled using a package manager (apt-get or aptitude from the terminal, or Synaptic Package Manager graphically).
I cannot run gksudo, the terminal saying : bash: gksudo: command not found. I tried to reinstall from System->Administration->Synaptic Package Manager. I marked for Reinstallation by right clicking as you guided, but still cannot run sudo in terminal.
By the way, I don't know what is LiveCD:( and could you tell me that, because I am a layman...

---

### Post by jpeddicord on 2009-08-23
He means the CD that you installed Ubuntu from. You can use that as a recovery disk by following his instructions posted earlier.

Another option: Reboot, and when you see "GRUB is loading" press Esc to open a boot menu. Select an option with "(recovery mode)" next to it (most likely the second option.

Wait for it to start up and you will be presented with a list of options. Select "Drop to a root shell prompt" and try this command:

```
apt-get install --reinstall sudo
```

If that fails, try out Rocket2DMn's advice above.

---

