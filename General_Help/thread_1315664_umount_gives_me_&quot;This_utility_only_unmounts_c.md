---
title: "umount gives me &quot;This utility only unmounts cifs filesystems.&quot; error"
date: 2009-11-05
forum: General Help
---

### Post by john_spiral on 2009-11-05
Hi,

I'm attempting to unmount a windows share that was mounted via the following command:

sudo mount -t cifs //machineName/c$ ~/windowsmachine/ -o credentials=.pass,iocharset=utf8,noexec,ro

The above command is part of script that mounts windows shares on the network and copies their shortcuts to a folder on my Ubuntu box, it's been running fine for ages but somehow it's got itself into a twist.

Windows shares are mounted with an ordinary account that has sudoers rights to the mount/umount commands.

I've deleted and recreated the mount point - ~/windowsmachine
still no luck. 

Keeps giving the below error:

[B][COLOR="Blue"]xxxx:~$ sudo umount ~/windowsmachine/
This utility only unmounts cifs filesystems.
This utility only unmounts cifs filesystems.[/COLOR][/B]

I've tried the -f (force) option still no luck!

I've tried an account that has sudo (root) privileges, still no luck.

I've got a few other mounts to windows shares on the go, so I don't want to kill anything that will make them die.

Shall I just reboot and live with it? I hate rebooting as it brings into question why I switched to Linux in the first place. 

Thanks

John

---

### Post by john_spiral on 2009-11-05
I'm gonna reboot, gedit is even gone sh*ts up.

---

### Post by john_spiral on 2009-11-05
looks like Ubuntu is totally mashed!!!!!!

Can't launch any apps within Gnome not even humble gedit.

Gedit just launches a white screen :-( , does anyone have any 'My Ubuntu system is horibly mashed' URL's I could look at?

problems:

system monitor fails to launch

---

### Post by john_spiral on 2009-11-07
Turns out I had too many (480000) small files on the file system, reboot a few times to check you actually can write files to the file system.

I copied all the small files to an external 1T usb drive, to get my system operational again. 

Search for the term inode, for more info.

---

