---
title: "Help! Removed gnome, can't acces login screen"
date: 2012-01-03
forum: General Help
---

### Post by ubuntu27 on 2012-01-03
**EDIT:** Ok. Let's forget recovering. **How do I backup my files from the Recovery Mode**? I want to move/copy them to an external hard drive. After that I will re-install the OS.


Original:
Salut everyone!

I just installed Xubuntu. And decided to get rid of gnome.
I follow Psychocat's instruction for [pure Xfce]("http://www.psychocats.net/ubuntu/purexfce")

Now, whenever I turn on the computer, it shows the following  message and blinks repeatedly. 

```
*Stopping cold plug devices
*Stopping log initial device creation
*Starting enable remaining boot-time  encrypted block device.
*Starting configure network device security.
*Starting bluetooth
*PulseAudio configured for per-user session
                                 saned disabled; edit /etc/default/saned
*Stopping enable remaining boot-time encrypted block devices
*Stopping mount file-system on boot.
```

When it blinks it seems as if it is trying to load LightDM for a mini-second and then returns to the previous message.

Perhaps something that shouldn't be removed has been removed.

Please help me.

PS: My /home is encrypted, and there is only one user installed.
PS II: I am currently running Xubuntu Live USB.
PS III: I am running Oneiric Ocelot

Thank you all in advance! ^_^

---

### Post by ubuntu27 on 2012-01-03
ok. I just re-learned how to go to Recovery Menu in Grub.

And tried to install gnome:

```
sudo: Can't open /var/lib/sudo/MyNanme/console read-only filesystem
W: not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt
```


*************

Ok. Let's forget recovering. **How do I backup my files from the Recovery Mode**? I want to move/copy them to an external hard drive. After that I will re-install the OS.

---

### Post by Catharsis on 2012-01-05
There are a bunch of things you can try to repair your system.

See if you can switch to a tty with Ctrl+Alt+F2. You can login and run commands.
If you can't switch ttys, add 'text' to the GRUB command line (hit 'e' to edit during the grub prompt).

Try running:
```
sudo apt-get update && sudo apt-get install -f
```
```
sudo apt-get update && sudo apt-get install xubuntu-desktop
```

If you don't feel like repairing, you can run a LiveCD and try to copy your info (not sure if this will work with an encrypted partition though).

You can also enter into text-mode and mount your external harddrive, where sdX# is the drive and partition you want to copy the files to (i.e. sdb1) (run 'sudo fdisk -l' to get a list of drives and partitions, and find the one you want, most likely on sdb if you only have one internal harddrive).
```
sudo mkdir /mnt
sudo mount /dev/sdX# /mnt
cp -r path/to/whatever/folder/you/want/to/copy /mnt
```
Might have to run that last one as root depending on what you're copying.

---

### Post by Basher101 on 2012-01-05
if all else fails, pop in a Live CD/USB and copy from the CD/USB boot session all your files you want to keep and then reinstall..

---

### Post by ubuntu27 on 2012-01-06
I just accessed my encrypted ~/home with a Live USB, and reinstalled the OS.

[How I accessed my encrypted home]("http://ubuntuforums.org/showthread.php?t=1904059")

Thank you all!

---

