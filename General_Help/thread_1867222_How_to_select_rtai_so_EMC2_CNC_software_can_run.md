---
title: "How to select rtai so EMC2 CNC software can run"
date: 2011-10-22
forum: General Help
---

### Post by dsoodak on 2011-10-22
I used the Ubuntu software center to install EMC2 and rtai  version 2.6.32-122 (typed "CNC" as software search string)  I got the message: "EMC2 requires the real-time kernel 2.6.32-122-rtai to run. Before running EMC2, reboot and choose this kernel at the boot menu"  As I didn't already have a windows partition, it doesn't go into a boot menu. I honestly don't know enough about Linux to tell if grub is even installed, or to check which kernel is currently running.

---

### Post by gsmanners on 2011-10-22
I think if you have more than one kernel you'll get the grub menu, though it will still automatically start the latest one after a certain amount of time. You can have as many kernels as the space on your drive allows.

---

### Post by dsoodak on 2011-10-22
I'm pretty sure its installed. 
In the "ubuntu software center" (maverick, 10.10) I installed "Linux kernel image for version 2.6.32 on x86/x86_64"  (linux-image-2.6.32-122-rtai in small text underneath). It now only shows the option "uninstall".
However, it still just goes right to the GUI login screen on startup.

---

### Post by gsmanners on 2011-10-22
/me kicks grub in the shins

Okay, here's how you fix [that bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/669481"):

Open /etc/default/grub in a text editor:

```
gksudo gedit /etc/default/grub
```

Change:

```
#GRUB_HIDDEN_TIMEOUT=0
```

to

```
GRUB_HIDDEN_TIMEOUT=0
```

(Coderspeak for do not hide timeout (I think).)

Then do:

```
sudo update-grub
```

That should fix it.

---

### Post by dsoodak on 2011-10-22
This is the grub file (looks like it has already been fixed):


# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




ran the update command:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-122-rtai
Found initrd image: /boot/initrd.img-2.6.32-122-rtai
Found memtest86+ image: /boot/memtest86+.bin
done

---

### Post by dsoodak on 2011-10-22
The file didn't need editing, but I ran the update command anyway.
Now I have a "boot menu" option(F11).
First time I tried it, it asked what device (hard drive, cdrom, usb) to boot from, then gave a list of linux kernel version. I chose rtai and everything worked.

Except that the wireless wouldn't connect. Usually it connects automatically but this time it didn't and "connect to network" was grayed out even though "wireless enabled" was checked and it still had the network settings in memory (name, password, etc.).

I logged out so I could log back in with the normal kernel and post the results on line. This time it gave me the device option but never went to the kernel choice screen. It did, however, load the previous non-real-time kernal and wireless was working as usual.

---

### Post by gsmanners on 2011-10-22
Well, at least you don't have to rebuild the kernel. :/

---

### Post by dsoodak on 2011-10-22
yeah...I start a new search every time a set of instructions includes "recompile kernel" as a step(as the first rtai installation instructions did).
After you pointed me to the grub file, I some more searches and someone said that you had to comment out that line (not remove comment) to make the kernel menu appear. Also, holding SHIFT is supposed to make you enter it, though I didn't try this myself.

I still have to figure out why the wireless isn't working in rtai kernel mode (in regular mode right now), but I'll leave that for later.

Thanks for your assistance!
Now time to get back to setting up my CNC hobby kit (just finished putting together a kit from mydiycnc.com)

---

