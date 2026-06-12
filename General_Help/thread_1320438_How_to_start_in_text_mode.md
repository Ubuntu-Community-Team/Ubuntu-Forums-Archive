---
title: "How to start in text mode?"
date: 2009-11-09
forum: General Help
---

### Post by Nicovdd on 2009-11-09
Hi,
 
I'm using SUSE already for many years, and tried my hand now at Ubuntu server (9.10).
 
I had the server running perfectly, but wanted to add Gnome as a GUI - just to try it.
 
But, whenever I now boot, the Gnome desktop starts.
 
As there is no inittab anymore to set runlevels, how do I get my server to start without Gnome popping up?
 
Thanks

---

### Post by Giblet5 on 2009-11-09
The easiest way that I know of is to remove /etc/rc2.d/S30gdm.

It's just a symlink.

```
sudo rm /etc/rc2.d/S30gdm
```

Reboot and it will stop at a console login prompt.

---

### Post by Nicovdd on 2009-11-09
Hi,
 
There is no such file...
 
nico@Knoffel:/etc/rc2.d$ ls
README S20clamav-freshclam S20qemu-kvm S21fam S50cups S70pppd-dns S88lsassd S99laptop-mode
S16ssh S20dkms_autoinstaller S20samba S23ntp S50pulseaudio S86dcerpcd S90binfmt-support S99ondemand
S19mysql S20exim4 S20speech-dispatcher S24dovecot S50rsync S87eventlogd S91apache2 S99rc.local
S19spamassassin S20kerneloops S20virtualbox-ose S25bluetooth S50saned S87netlogond S99acpi-support
S20clamav-daemon S20likewise-open S20winbind S28libvirt-bin S70dns-clean S87npcmuxd S99grub-common
 
Edit:  Apologies if my response sound rude - intended to be friendly with many smiles :-)

---

### Post by Giblet5 on 2009-11-09
Sorry. I was looking at a Jaunty box.

Gdm gets started on line 20 of /etc/init/gdm.conf

```
sudo vi +20 /etc/init/gdm.conf
```

Or you could just move it to a backup folder.

---

### Post by scragar on 2009-11-09
I figure there are 2 ways, the first would be to edit grub and make the init level stop at 3 by default.```
sudo nano /boot/grub/menu.lst
```Copy your ubuntu lines, call it something obvious like "Ubuntu command line" and insert a 3 at the end of the line(My arch setup uses this method).
```
# (1) Arch Linux
title  Arch Linux Command Line
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/a28eabe1-9088-4e13-9d6f-6f082b79e17e ro 3

```
Advantages: Easy to switch between the two if you want to.
Disadvantages: Ubuntu tends to rebuild the grub file every kernel update, which will ruin your changes.


Option 2, edit inittab.
```
sudo nano /etc/inittab
```
Near the top you will see 3 lines:
```
# Boot to console
#id:3:initdefault:
# Boot to X11
id:5:initdefault:
```
I think you can guess what to do here.

Advantages: Changes will remain pretty much perminantly
Disadvantages: If you screw up the file you'll need a liveCD to fix it, you can't choose at boot, you'll always have to startx manually, installing a new desktop enviroment may cause conflicts.

---

### Post by Giblet5 on 2009-11-09
> **scragar said:**
> I figure there are 2 ways


Great ideas, but there is no menu.lst or /etc/inittab on 9.10...

9.10 uses grub2 and does not use sysv init.

---

### Post by scragar on 2009-11-09
> **Giblet5 said:**
> Great ideas, but there is no menu.lst or /etc/inittab on 9.10...

9.10 uses grub2 and does not use sysv init.

Oh, well I wasn't aware of that, I will have to try the latest ubuntu before poking my nose in again.

---

### Post by sisco311 on 2009-11-09
Edit the /etc/init/gdm.conf file to look like this:

```

...
description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

start on (**runlevel [3]**
          and filesystem
          and started hal
          and tty-device-added KERNEL=tty7
          and (graphics-device-added or stopped udevtrigger))
stop on runlevel [0**2**16]
...

```

to start gdm type:
```
sudo service gdm start
```

---

### Post by jimezam on 2010-01-05
Hello @sisco311.  I followed your advice and works fine but I am still getting some kind of graphical splash screen (black background with white Ubuntu's logo on the center) before go into the text console.

It looks like it is starting X/GDM and then stopping it.  Am I right ?

I would like to avoid any load of X/Gnome and only load it if I call it with startx/service.

Thank you for your help.

jimezam.

---

### Post by evaitl on 2010-02-17
[INDENT]Hello @sisco311. I followed your advice and works fine but I am still getting some kind of graphical splash screen (black background with white Ubuntu's logo on the center) before go into the text console.

It looks like it is starting X/GDM and then stopping it. Am I right ?

I would like to avoid any load of X/Gnome and only load it if I call it with startx/service.[/INDENT]


I don't think it is starting X, just the splash. 

If you look at /etc/init/gdm.conf in 9.10, you should see: 

 ```

   # Check kernel command-line for inhibitors
    for ARG in $(cat /proc/cmdline)
    do
        case "${ARG}" in
            text|-s|s|S|single)
                exit 0
                ;;
        esac
    done
```

It looks like adding the kernel command line parameter "text" will keep gdm from starting. 

Assuming you are using grub 2, it looks like the place to go to change the kernel command line is /etc/default/grub. 

I would change the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to 

```
GRUB_CMDLINE_LINUX_DEFAULT="text"
```

then run "sudo update-grub" to get rid of the splash screen, see what is going on during the boot, and bring up console mode.

---

