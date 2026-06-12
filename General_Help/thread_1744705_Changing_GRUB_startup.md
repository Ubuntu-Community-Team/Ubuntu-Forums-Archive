---
title: "Changing GRUB startup"
date: 2011-04-30
forum: General Help
---

### Post by Bobrm2 on 2011-04-30
I've 11.04 installed in it's own partition. It is not setup to my idiosyncrasies; so until it is to my way of doing things I'd like to start with 10.10 loading, instead of waiting to select it from GRUB.

  Is there a way just to automatically start 10.10? Maybe move the pertinent line to the necessary startup position?  Thanks for your help.

---

### Post by stinkeye on 2011-04-30
From your Natty install,
In a terminal run..
```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```

Use the entry [COLOR="#ff00ff"]number[/COLOR] from this to edit grub...
```
gksudo gedit /etc/default/grub
```


changing the line(should be near the top)
```
GRUB_DEFAULT=[COLOR="Magenta"]0[/COLOR]
```
to the [COLOR="#ff00ff"]menu entry number you want to use[/COLOR]


Then run ...
```
sudo update-grub
```

---

### Post by oldfred on 2011-04-30
Some more ways.

Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I assume this still works with 11.04
Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

Example is for windows, but you can use any exact name.

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by Bobrm2 on 2011-05-01
Have installed "Startup Manager" and ran it, with the following result:

bob@Ubuntu:~$ startupmanager
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) /usr/sbin/update-grub: line 1089: read: read error: 0: Bad file descriptor
Grub2 detected
Usplash not detected
Splashy not detected
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.1/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)
bob@Ubuntu:~$ 

  I am attempting to boot into 10.10, not 11.04 as is currently happening, unless I sit on startup.  Have made an attempt to reset from "0" Ubuntu 11.04 to "3" for Ubuntu 10.10. There two memory tests between the different versions.

  It is obvious that I need to edit "GRUB", but I see major problems ahead due to my lack of understanding.

  What is the error message mean, or did I trash the grub in my earlier attempt to correct the above description. Also, where do I start making the correction.  I wasn't given time to reply to: "Would you like /boot/grub/menu.lst generated for you? (y/N)"
  Thanks for the assistance.

Bob R

---

### Post by oldfred on 2011-05-01
You do not want menu.lst as that is old grub.

The new grub 1.99 must be enough different that Startup manager cannot deal with it. There are a lot of new things in the latest grub2.

I would just do the manual change.

If you know the line number you want:

gksudo gedit /etc/default/grub
GRUB_DEFAULT=0

I have some custom entries including blank lines. I forgot to count those and trying to boot a blank line does not work well.:)

---

### Post by Bobrm2 on 2011-05-01
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=775 splash"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

bob@Ubuntu:~$ sudo update-grub
[sudo] password for bob: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Found kernel: /vmlinuz-2.6.35-28-generic
Found kernel: /vmlinuz-2.6.35-22-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done


Fred, will try once more, and see if vs. 10.10 will load instead of 11.04.
Bob R

---

### Post by Bobrm2 on 2011-05-01
bob@Ubuntu:~$ GRUB_DEFAULT=4
bob@Ubuntu:~$ sudo update-grub
[sudo] password for bob: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.35-28-generic
Found kernel: /vmlinuz-2.6.35-22-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

bob@Ubuntu:~$ 


Trying to change to position 4 Grub-Default 4. 4 is Ubuntu 10.10

---

### Post by oldfred on 2011-05-01
This is not good:

Updating /boot/grub/menu.lst ... done

Did startup manager create your menu.lst? You want grub.cfg to be updated. I would delete (or rename if concerned) the menu.lst in /boot/grub and rerun the update.

---

### Post by Bobrm2 on 2011-05-01
Grub still loads: Linux 2.6.38-8-generic or Ubuntu 11.04 which shows in my grub to be "0".  ???

Bob R

---

### Post by drs305 on 2011-05-01
When you boot are you seeing the Grub 2 (Ver 1.98 or 1.99) or Grub legacy menu? If it's G2, you will see the version number at the top.

In your last post, when you ran update-grub it appears to have written to Grub legacy's menu.lst.

If Grub2 is installed and usable, you can try to force the update to use Grub 2 with the following command:```

sudo grub-mkconfig -o /boot/grub/grub.cfg
```

This should guarantee grub.cfg is updated, although it won't help if your system is booting with Grub legacy.

---

### Post by Bobrm2 on 2011-05-01
"Did startup manager create your menu.lst? You want grub.cfg to be updated. I would delete (or rename if concerned) the menu.lst in /boot/grub and rerun the update."

 going to have to quit, for a while. Ran "gksu gedit grub.cfg"   Blank, so I a little mixed up now. the menu.lst appears to be blank. Lots of storms here.  

Bob R

---

### Post by Bobrm2 on 2011-05-01
Fred,  Grub 2 (1.99) is the one here. Now, It seems that "all" versions are identified and that 11.04 is "0" position. (not the correct terminology, but I hope understood.).  I have, in terms I understand:
   Ubuntu 11.04
   Memtest
   Memtest etc 
   Version 10.10 etc.

   Position "4" is desired, will gksudo gedit /etc/default/grub and update-grub. 

  That should do it????

Bob R




bob@Ubuntu:~$ sudo update-grub
[sudo] password for bob: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.35-28-generic
Found kernel: /vmlinuz-2.6.35-22-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

bob@Ubuntu:~$ 
bob@Ubuntu:~$ gksudo gedit /etc/default/grub
bob@Ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.35-28-generic
Found kernel: /vmlinuz-2.6.35-22-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

bob@Ubuntu:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
Generating grub.cfg ...
Found memtest86+ image: /memtest86+.bin
Found Ubuntu 11.04 (11.04) on /dev/sda6
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
done
bob@Ubuntu:~$

---

### Post by Bobrm2 on 2011-05-01
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT="0"
GRUB_HIDDEN_TIMEOUT_QUIET="true"
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=775 splash"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


bob@Ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.35-28-generic
Found kernel: /vmlinuz-2.6.35-22-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

bob@Ubuntu:~$

---

### Post by drs305 on 2011-05-01
Your system currently has multiple personalities. First, you appear to have both Grub legacy and Grub 2 installed. 

To further muddy the waters, Maverick uses Grub 2 [noparse](1.98)[/noparse], while Natty uses Grub 2 (1.99), which has a few notable improvements.

Additionally, you have two Ubuntu installations so each has Grub/Grub2 installed, and only one of them actually controls the menu displayed at boot. Even if you update the non-controlling Grub while booted in that system, it won't affect what you see or boot to.

For example, if the Natty Grub2 is controlling your boot, and you boot into Maverick and run 'update-grub', the Maverick grub files will be updated. However, at boot, the MBR is going to look for and use your Natty grub files, which haven't changed.

You set the controlling Grub by booting into the system you want to control the boot. Normally this should be the system you use the most often, and the one you are most likely to run 'update-grub' from. Another consideration is whether you want to use G 1.98 (Maverick) or G 1.99 (Natty), if it matters to you.

To make a booted Ubuntu system the controlling one (as far as grub is concerned), run this command (assuming the BIOS will look at sd**a**'s MBR):
```
sudo grub-install /dev/sd**a**
```
If you run this from Maverick, Maverick's grub files will now control the menu and default settings. Anything you do to Grub while booted in Natty will update Natty's files but won't affect your boot or default selections.

#-o

Next, you should probably purge Grub legacy (grub) and keep Grub2 (grub-pc).

To do this, make sure you have an internet connection (with the first command), then remove the 'grub' package. Reinstall grub-pc (Grub2) just to ensure it's still active:```

sudo apt-get purge grub
sudo apt-get install --reinstall grub-pc
sudo grub-install /dev/sda
sudo update-grub
```
If asked during the reinstallation where you want to install G2, make sure you designate only sda, and not any partition in sda. You use the SPACE bar to select the drive, and TAB to highlight the OK option.

Note also that in your previous posting of /etc/default/grub, those settings only apply when using Grub 2, not Grub legacy.

---

### Post by Bobrm2 on 2011-05-01
Well, Sir(s), thank you. I amazed and your help was very well presented. I don't know if anyone else tried to use the old version while tweaking the newest version. Best to all 

Bob R.

---

### Post by fukngroovn on 2011-05-01
Thanks, this really helped me!

---

