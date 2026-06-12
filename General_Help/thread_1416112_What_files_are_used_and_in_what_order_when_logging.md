---
title: "What files are used and in what order when logging in"
date: 2010-02-25
forum: General Help
---

### Post by cforput on 2010-02-25
I have written a shell script and I want to include it so when I log in, it automatically runs. I have tried creating .bash_profile and putting it there. I have deleted this file and tried putting it in .profile. I even tried system>preferences>Startup Applications.

None of these are working. In fact, I tried to just put in the following line in both the .bash_profile and .profile files and that didn't' even work. 

PATH ="$PATH:/media/ShareDrive/Documents/Computing/ShellScripts"

Then after booting, I open a terminal, give it the echo $PATH command and the above path is not listed.

After the path is ammended, I want to run my shell script and I use the following

MozMiscFiles.sh

What file do I need to use?

Here is my .profile 
***********************
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

PATH ="$PATH:/media/ShareDrive/Documents/Computing/ShellScripts"

MozMiscfiles.sh
*********************

I made sure the .bash_profile and .bash_login files were not present on my computer when running trying .profile 

I am using Karmic and the path is pointing to a logical drive I am automounting.

---

### Post by blueridgedog on 2010-02-25
Ways to have things run at "start"

1. When booting all files in /ect/init.d/rc.local are run. This file also calls and runs /etc/rc.local. These are the equivalent to the DOS autoexec.bat file system, but if you are under 30, you don't know what that it is and it seems like silly reference.

2. In /etc you will find various directories named /ect/rcn.d where n is a number from 0 to 6. These numbers represent the different Linux run levels. The default Ubuntu run level is 2, so if you look inside /etc/rc2.d you will see symbolic links back to files in /etc/init.d. Files with a capital S are run when the system starts to that run level, others are not. Note that Ubuntu/Debian defaults to run level 2 and uses a GUI at that point which is contrary to most Linux configurations.

3. The window manager also starts applications when the user logs in, running these applications as the user, not as system level applications. The gnome applications you configure to run at start are setup as files in the directory /home/USER/.config/autostart. Gnome applications also start based upon the entries in /etc/xdg/autostart/ and if you use the gui to disable them, a negating entry is placed in your /home/USER/.config/autostart directory.

4. Applications can be started via entries in the files /home/USER/.bashrc and /home/USER/.bash_profile.

5. A script called "Default" can be placed in /etc/gdm/PostLogin, /etc/gdm/PostSession and /etc/gdm/PreSession. The sripts will be run as root at the time implied by thier directory name. (note the capitals in the file names and path names)

If you have a script that is supposed to run via one of these methods and it seems to not run, you need to build in some debugging so that you can see what is working or failing. This can include logging, or simply checking logs for errors. A simple approach is to have the script create a log file of its actions so you at lease know that it was run and can then focus on either figuring out why it is not running or why it is running, but not working. If you know the script is running, perhaps something else is changing the settings after it runs.

---

### Post by PoHandle on 2010-02-25
Have you *chmod +x*'d it?

---

### Post by cforput on 2010-02-26
Thanks to both of you for your help. 

PoHandle, I did do a chmod +x on the file but a good suggestion. 

blueridgedog,
unfortunately, I am way past 30 and definitely remember autoexec.bat and config.sys. I did something along the lines of what you were suggesting. I let everything boot up and then when I got to the log in screen, I did a ctrl-alt-f1 and went to a command prompt. I then logged in from there. Such a stupid thing I did. With Unix being case sensitive, I missed capitalizing one letter in the file name so I got a "file not found" error. Once I fixed that, poof! the script worked. 

And I want to thank you for your thorough explanations of the files used as the system boots. This will be very helpful to me in my venture down the Ubuntu / Linux / Unix path.

I will change this one to solved.   :D

---

### Post by blueridgedog on 2010-02-27
If you are just starting out, here is my collection of cheat sheet items, some are outdated at this point:

```
Boot
	dmesg	-> view boot messages

Compile
	sudo apt-get install build-essential
	sudo apt-get install linux-headers-$(uname -r)

Disk Commands
	df -> disk usage	
	blkid	-> get id of block devices
	fdisk -lu	-> show logical disks
	e2label -> set disk lables
	baobab -> graphical tool for working with disks
	sudo du --max-depth=1 | sort -g -> shows directory sizes small to large
	sudo sh -c "echo 1 > /proc/sys/vm/block_dump" -> monitor what is using hard drive
	sudo tune2fs -m1 /dev/sda6    -> Set reserved blocks to 1% of total space
	sudo tune2fs -r51207 /dev/sda6 -> Set reserved blocks to 51207 4K-blocks* = 200 MiB
	sudo tune2fs -l /dev/sda6 | grep "Block size"
	dd if=/dev/hdc of=China.iso
	mount -o loop nameofisofile.iso /mnt/nameofdirectory -> mounts an 

ISO
	sudo mke2fs -n /dev/sda1 -> gets backup superblock
	Superblock backups stored on blocks:
	32768, 98304, 163840, 229376, 294912, 819200, 884736
	sudo e2fsck -b 32768 /dev/sda1	-> users superblock identified to repair filesystem
	sudo fuser -cv /dev/sdb1 -> List processes using a drive
	Mounting a file system and changing your root fs to it...good for recovery:
	sudo mount --bind /dev /media/sda2/dev
	sudo chroot /media/sda2
	filefrag FILENAME -> gives number of fragments

Hardware
	lshw	-> list the hardware in the system
	lshw -class cpu
	uname -a -> show kernal info
	sudo dpkg-reconfigure xserver-xorg
	lsusb -> show usb items
	lspci -> show the PCI cards
	# for legacy USB devices	
	sudo vi /etc/modprobe.d/options.conf
	#add this line
	options usbcore use_both_schemes=y

Memory
	free	-> show free memory and swap

Networking
	trickle -> a lightweight userspace bandwidth shaper
	Edit /etc/modprobe.d/aliases - to turn off ipv6 
	#alias net-pf-10 ipv6
	alias net-pf-10 ipv6 off
	alias net-pf-10 off
	alias ipv6 off 
	sudo iptables -nvL -> gives status of all chains

Nvidia settings:
	sudo rm /etc/X11/xorg.conf
	gksu nvida-settings
	go to X server display configuration adjust to the desired resolution>APPLY>SAVE TO XCONFIG
	/etc/X11/xorg.conf

Command Line Tricks
	ls -dal */ -> shows directories only

Graphics
	glxgears -> tests DRI
	
Programs
	ldd /path/to/application -> shows library dependencies

X server setup:
	CTRL+ALT+F1 -> to get to a terminal
	sudo /etc/init.d/gdm stop
	sudo dpkg-reconfigure xserver-xorg
	sudo /etc/init.d/gdm start

Booting to Run Level 1
	1. At the graphical boot screen, press e (for edit), scroll down to select the kernel, and press e again
	2. Press the spacebar, type single or 1 (Ubuntu allows S and s as well), and press Enter
	3. Finally, press b to boot, and you’ll boot into runlevel 1

Gnome Configuration
	gconf-editor
	gnome-color-chooser -> install to select compact
	System - Preferences - Appearance - Fonts - Details then reduce dpi 

Managing applications
	sudo dpkg --get-selections | grep -v "deinstall” >$HOME/Desktop/installed-packages -> creates a list of installed packages

Free news readers
	news.central.cox.net
	news.optonlinr.net

Feh
	feh -rzsZFD 5 /home/USER/Pictures

Package managment
	#These commands will sometimes unstick an update 
	sudo dpkg --configure -a
	sudo aptitude -f install
	sudo aptitude dist-upgrade
	#To save the list of what packages are installed:
	#Originally Posted by lovinglinux
	dpkg --get-selections > ~/my-packages
	sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
	sudo tasksel install lamp-server

Samba
	/var/lib/samba/usershares is the location for user created shares in nautilus

Sensors
	sudo apt-get install lm-sensors
	sudo sensors-detect

Sudo:
	visudo -> to edit sudo actions and users

Grub:
	Updating Grub 1: 
	Bootup a live cd, open a terminal and do the following.
	sudo grub
	This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands
	find /boot/grub/stage1
	This will return a location. If you have more than one, select the installation that you want to provide the grub files.
	Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
	root (hd?,?)
	Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)
	Next enter the command to install grub to the mbr
	setup (hd0)
	Finally exit the grub shell
	quit
	Reinstalling Grub on a chrooted file system:
	sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
	sudo grub-install /dev/sda
	sudo update-grub
	Booting ISO on HD with GRUB 2:
	menuentry "Ubuntu Live 9.10 32bit" {
	loopback loop /boot/ubuntu-9.10-desktop-i386.iso
	linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/boot/ubuntu-9.10-desktop-i386.iso noeject noprompt --
	initrd (loop)/casper/initrd.lz
	}

Firefox	
	firefox -safe-mode 
```

---

