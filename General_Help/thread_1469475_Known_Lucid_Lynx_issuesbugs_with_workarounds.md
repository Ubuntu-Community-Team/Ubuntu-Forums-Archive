---
title: "Known Lucid Lynx issues/bugs with workarounds"
date: 2010-05-02
forum: General Help
---

### Post by philinux on 2010-05-02
***_Disclaimer :_***[COLOR=DarkOrange]** The purpose of this thread is to list known [SIZE=3][B]Lucid Lynx**[/SIZE] **issues** and bugs, [SIZE=3]_and give the corresponding workarounds and launchpad entries_[/SIZE].[/B][/COLOR]

[SIZE=4][COLOR=DarkOrchid]**Feel free to propose other known Lucid Lynx bugs to be listed here but[B]_ please provide a link to the workaround and a link to the corresponding launchpad _**entry.[/B][/COLOR][/SIZE]

-------------------------------------------------
[B]Warning: Before upgrading or attempting a reinstall make sure you backup essential files.
Please read the Release Notes:-[/B]
[COLOR="darkred"][http://www.ubuntu.com/getubuntu/releasenotes/1004](http://www.ubuntu.com/getubuntu/releasenotes/1004)
[/COLOR]
**[COLOR=darkred]Upgrade 8.04 -> 10.04 can break apt-get.[/COLOR]**
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/429841")

For those not wanting to read the bug report in detail, the fix is :

```
sudo rm /var/lib/dpkg/info/flashplugin-nonfree.prerm

sudo dpkg --remove --force-remove-reinstreq flashplugin-nonfree
sudo dpkg --purge --force-remove-reinstreq flashplugin-nonfree
```

**[COLOR="DarkRed"]Nautilus location bar, bread crumbs vs text based.[/COLOR]**
Breadcrumbs is now the default. The button to switch between the two has been removed. Users can switch with ctrl+l and then esc to revert to breadcrumbs. To permanently switch to text users have to use gconf-editor from a terminal. Note: gconf-editor has been removed from the menus. The key is.
apps>nautilus> preferences> always_use_location_entry


**[COLOR="DarkRed"]Minimize, Maximize and Close button placement.[/COLOR]**
A decision has been taken to move the placement to the left. Mark Shuttleworth explained that this was because "something" is going to be placed in the right hand area in the next release. Moving the buttons now would help enable this change.
**[Update ][http://www.markshuttleworth.com/archives/333](http://www.markshuttleworth.com/archives/333)**

The buttons are in the old location on all default themes apart from Ambiance,Radiance and Dust, If you still want the Ambiance ,Radiance or Dust theme but with buttons on the right, choose one of those other themes and use the Customize button to achieve what you want. e.g.
1. System > Preferences > Appearance
2. Select the theme icon "New Wave"
3. Click the button "Customize.."
4. Select tab "Controls" and select "Ambiance"
5. Select tab "Window border" and select "Ambiance"
6. Select tab "Icons" and scroll down and select "Ubuntu-mono-dark"
7. Select "Save Theme" to your choice.
**Using gconf-editor is not the right approach as this could bork future themes. This change makes it easier for themes to do interesting things with window borders.  Unfortunately, if the wrong approach spreads, they won't be able to do that.**


**[COLOR="DarkRed"]Problem with Huawei and possibly other usb mobile broadband dongles.[/COLOR] **
Please see this bug report and click the affects me button if you have this bug. 
Try this first
```
sudo apt-get install usb-modeswitch
```
A fix is committed. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146).
Also fix/workaround here. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547) See post #32


**[COLOR="DarkRed"]Bootup/Plymouth.[/COLOR] **
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013)

Graphical solution : [http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
```
gksu gedit /etc/default/grub
``` and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXPAYLOAD_LINUX=1680x1050** Save the file and run ```
sudo update-grub
```The resolution chosen should be your monitors native resolution.

Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

If the problem is a slow boot, and you have no floppy drive, disable the floppy in the bios. This has been reported as a fix to this. 
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515) FIX Released.
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/551712)

If the problem is plymouth not displaying, and a black screen from grub to gdm, this could be due to graphics drivers needing to be loaded quicker. This is bugged.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/539787)

Plymouth is installed with 2 themes by default you can install more via synaptic.
To change themes this code is used.
```
sudo update-alternatives --config default.plymouth

```

**[COLOR="DarkRed"]Java. [/COLOR]**
Sun java has been deprecated. Openjdk is now the default, i.e installing ubuntu-restricted-extras with recommends will install openjdk and the icedtea plugin. Openjdk has been certified by Java SE Test Compatibility Kit (TCK) and is compatible with the Java(TM) SE 6 platform on the amd64 (x86_64) and i386 (ix86) architectures. However sun-java is in the partner repo.
There's a bug regarding the icedtea plugin and certain applets.
[https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328](https://bugs.launchpad.net/ubuntu/+source/openjdk-6/+bug/551328).
Not fixed yet. Workaround may be to create a new Firefox profile.


**[COLOR="DarkRed"]Boot options hidden by default on Desktop and Netbook LIVECDs[/COLOR]**
The Ubuntu 10.04 LTS Desktop and Netbook CDs feature a new boot interface that is non interactive by default. 
To configure advanced boot options, press any key at the first boot screen.


**[COLOR="DarkRed"]Scrolling with ALPS Laptop Touchpads[/COLOR]**
Various users who have ALPS touchpads have reported that scrolling no longer works in the final release. A [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554050") is already open on the case, and the current workaround is to run:
```

sudo rmmod psmouse
sudo modprobe psmouse proto=imps

```

If this works, you can make it permanent by putting:
```
options psmouse proto=imps
```
At the bottom of the file **/etc/modprobe.d/options**


**[COLOR="DarkRed"]Ubuntu shuts down after unplugging Laptop power cord[/COLOR]**
A problem known with MSI wind and some Vostro users.

Current workaround is to open **gconf-editor** and browse to:
```
/apps/gnome-power-manager/general
```
And de-select the option **use_time_for_policy**

There is no need to restart, just close the configuration editor.

---

### Post by bcbc on 2010-05-02
A lot of users are overwriting their windows boot sector due to a confusing message with the grub2 install. It says something like 'Choose where to install grub. If you are not sure select all partitions'. And this leads some to select their windows partition.

NOTE: if you are reading this before you upgrade, the only place you should install grub is to the drive you are booting from. For most people it's /dev/sda . If you installed from within windows (a WUBI install), do not install the grub2 bootloader - leave all boxes unchecked.

The fix and diagnosis is at: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector) courtesy of meierfra. 

This is not the same as the bug that caused the re-release of certain iso's. That had to do with the windows not being listed in the grub menu. In this case, the windows option is listed but fails to boot.

Links to launchpad bug(s);
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/571893)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by bcbc on 2010-05-02
Another issue - when upgrading to 10.04 from a wubi install (not sure if it affects normal upgrades) it gets into a tight loop. What it says is 'Preparing memtest86+' and if you click on the terminal windows it just shows the line 'found linux image linux-2.6.xxxx' repeating. 

Anyway, if you hit CTRL+C it continues successfully. Some people have tried rebooting or canceling the install which leaves their ubuntu broken.

Here's a link with a picture: [http://ubuntuforums.org/showthread.php?t=1467754](http://ubuntuforums.org/showthread.php?t=1467754)


Looks like this is the launchpad bug for it: [https://bugs.launchpad.net/ubuntu/karmic/+source/lupin/+bug/540579](https://bugs.launchpad.net/ubuntu/karmic/+source/lupin/+bug/540579)

Edit: I can confirm I didn't get this with a normal (non-wubi) upgrade.

---

### Post by swizman on 2010-05-02
mount.cifs won't mount shares; set uid bit not set   

[https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/563805)

the fix

 sudo chmod +s `which mount.cifs`
 sudo chmod +s `which umount.cifs`

---

### Post by luigi_mb on 2010-05-02
In the initial post

```
gksu /etc/default/grub
```

should be

```
gksu gedit /etc/default/grub
```

/luigi

---

### Post by talent03 on 2010-05-02
We also have a common bug if you have not encountered it. FSCK hangs or crashes on bootup.

Related bug reports:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707)
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/572786](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/572786)

Essentially if it hangs, it may finish in about 5 minutes or more. Sometimes hitting an arrow key around the 85% mark I believe helps it continue for some reason. This bug needs more investigation, but it will definitly bother many people. Just to test it, you can sudo touch /forcefsck and see if you have the problem on bootup. Thanks for making this post a sticky, keeping common bugs together for everyone to see.

---

### Post by friv_livs on 2010-05-02
If Pitivi gives errors, and the gstreamer packages have been installed, reinstall pitivi from synaptic.

Also, thanks for the gconf min-max-close syntax.

---

### Post by ibuclaw on 2010-05-03
This is a final warning.

The purpose of this thread is to list known Lucid Lynx issues and bugs, and **[COLOR="Red"]give the corresponding workarounds and launchpad entries[/COLOR]**.

Do not post offtopic replies in this thread. If you have a support question, [start a new topic]("http://ubuntuforums.org/newthread.php?do=newthread&f=331").

All offtopic posts beyond this will be removed and repeated offenders will receive a warning.

Regards

---

### Post by sideburns on 2010-05-03
Another, minor issue: the upgrade removed xscreensaver from my sister's computer.  The fix, of course, is simple: use the package manager to reinstall it.

---

### Post by fbkarsdorp on 2010-05-03
Hi, there is a rather permanent problem with the propietary ati drivers. Maximizing and unminimizing is terribly slow with compiz enabled. There are several workarounds, however. You could either try the no-backfill xserver, the back-clear patch or enable Direct2D.

Direct2D can be enabled with the following steps:

1. backup your current xorg.conf
[FONT="Courier New"]
~$ cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak[/FONT]

2. delete the contents of xorg.conf

3. let aticonfig make an initial configuration: 

[FONT="Courier New"]~$ sudo aticonfig --initial[/FONT]

4. then enable Direct2D: 

[FONT="Courier New"]~$ sudo aticonfig --set-pcs-str=DDX,Direct2DAccel,TRUE
[/FONT]
I personally prefer the backclear patch as I noticed that although the maximizing issue is reolved with Direct2D, scrolling in for example emacs becomes totally sluggish. You can find more information on the backclear patch here:

[http://www.phoronix.com/forums/showthread.php?p=125046](http://www.phoronix.com/forums/showthread.php?p=125046)

log out and in and enjoy your fancy desktop. hope it helps.

---

### Post by michwe on 2010-05-03
After having installed the new Ubuntu Version 10.04, the language support dialog box popped up and asked for packet installation. But the error "Could not apply changes. Fix broken packages first!" appears. Every new attempt fails again.

One first post is 
 [http://ubuntuforums.org/showthread.php?t=1445123&highlight=language+support](http://ubuntuforums.org/showthread.php?t=1445123&highlight=language+support)


One bad workaround is a new installation with an active internet connection. The Ubuntu Setup fetches the correct packets in advance and the problem does not occur at all.

---

### Post by jschille on 2010-05-04
In Response to Bootup/Plymoth Instructions:

The commands will only work for Grub2, not legacy.
To install Grub2 before following the instructions on how to fix Plymoth screen.

 	Code:
 	sudo apt-get remove grub
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo update-grub2 
Then follow the instructions stated in the OP post.

Another issue with the resolution.  I was not able to enter the resolution given in the instructions.  To find my correct resolution I restarted the computer, got into the Grub screen and pressed 'C'.

You will then be able to enter into a command:  	 	 		 			 				vbeinfo 			 		
	
Note your resolution and then use that resolution for the instructions instead of the given resolution.

Hope this helps.

---

### Post by dcstar on 2010-05-04
After an upgrade of an existing system (probably using VMs), this message may appear at boot:

[SIZE="4"]An error occurred while mounting /proc/bus/usb[/SIZE]

This is due to an /etc/fstab entry that is no longer supported in 10.04, commenting out or removing the line in fstab will resolve the problem:
```
gksudo /etc/fstab
```
Launchpad ID: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/575597](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/575597)

---

### Post by barthel on 2010-05-04
Regarding the minimize, maximize, and close buttons:

The position of these buttons is actually determined by a new key field in index.theme, so all that's required is to create a new index.theme.

The method in the first post requires each user to create their own theme via the customization GUI. Another method is to use the dreaded keyboard. :twisted:

For example:
```
cd /usr/share/themes
sudo mkdir Radiance-Alt
sudo cp Radiance/index.theme Radiance-Alt/
sudo gvim Radiance-Alt/index.theme

```

NOTE: Susbstitute your preferred text editor (mine is gvim) 

Here's a suitably modified index.theme:
```
[Desktop Entry]
Type=X-GNOME-Metatheme
Name=Radiance[COLOR="Red"]-Alt[/COLOR]
Comment=Ubuntu Radiance theme [COLOR="Red"]with old button placement[/COLOR]
Encoding=UTF-8

[X-GNOME-Metatheme]
GtkTheme=Radiance
MetacityTheme=Radiance
IconTheme=ubuntu-mono-light
CursorTheme=DMZ-White
[COLOR="Red"]#[/COLOR]ButtonLayout=close,minimize,maximize:
[COLOR="Red"]ButtonLayout=menu:minimize,maximize,close[/COLOR]

```

This is the easiest way to make variants which are available to all users. The nice thing about doing it this way is that any updates to the base theme will be applied to your modified theme automagically.

---

### Post by Lawand on 2010-05-04
Problem: Can't adjust screen brightness on Xubuntu 10.4 Lucid Lynx using keyboard function keys.

Solution: [not necessarily the best solution] Remove Xfce power manager (package name: xfce4-power-manager) and install Gnome power manager (package name: gnome-power-manager), then reboot the system.

Notes:
[LIST]
[*]I faced the problem on an HP Compaq 610 laptop
[*]I didn't upgrade into 10.04 from an older version, rather did a fresh install
[/LIST]

---

### Post by sylwester on 2010-05-04
After upgrade firefox never started up when chosen from menu. This was due to me having home directories in an other location than /home/ (Actually, /home on my system is soft linked to somewhere else). 

Firefox printed out this error when running from terminal:
```
(firefox-bin:14089): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

```

Googling this made lots of hits, but non relevant..dmesg shows clearly that the problem is apparmor:
```
[23481.043374] type=1503 audit(1272926900.593:260):  operation="open" pid=23126 parent=23122 profile="/usr/lib/firefox-3.6.3/firefox-*bin" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/lemur/home/westerp/.ICEauthority"
[23481.070918] type=1503 audit(1272926900.621:261):  operation="open" pid=23126 parent=23122 profile="/usr/lib/firefox-3.6.3/firefox-*bin" requested_mask="r::" denied_mask="r::" fsuid=1000 ouid=1000 name="/lemur/home/westerp/.mozilla/firefox/profiles.ini"
```

I had this fixed previously by changing /etc/apparmor.d/tunables/home, but in the heat of the upgrade I choose the packet maintainers version. For users upgrading from Hardy will hit this one for the first time around I guess. the fix is running:

```
sudo dpkg-reconfigure apparmor

```

this will make sure the change goes in effect since it reloads apparmor after updating config files.

---

### Post by edvar on 2010-05-04
X Forwarding on SSH stops working after the upgrade. Lanuchpad #434799:

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/434799](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/434799)

Setting "AddressFamily inet" in /etc/ssh/sshd_config and restarting sshd does work around this problem.

---

### Post by bpowell2005 on 2010-05-04
Haven't seen this on launchpad yet but:

Laptops with Intel graphics chips, post upgrade may not be able to enable desktop effects (compiz). May also get a warning during boot of "low res mode".

The problem is during the upgrade, all sorts of Nvidia drivers were installed, and they're clashing with the Intel drivers. The workaround (I know of two times this worked perfectly)

```
sudo apt-get --purge remove nvidia*
```

You may want to apt-get -s first (simulate) and make sure nothing unwanted is being removed. Then reboot and Bob's your uncle.

---

### Post by Rubi1200 on 2010-05-05
Regarding this known bug affecting Intel graphics chipsets:
 
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
 
This is a workaround that allows the LiveCD to be booted after people reported the process stalling at a black screen.
 
> Just to be clear, this is only for the LiveCD and getting to the desktop in 10.04
 
Once there I am not sure what you would have to do if you install and want to make this a permanent install.
 
So, here we go:
 
Put the LiveCD in and boot up;
 
when you see the Ubuntu logo hit Enter;
 
Choose language and leave the default Try as a live cd or whatever it says again;
 
Important: hit F6 and then Esc to see the boot line
 
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**
 
Now, again this is important, move the cursor backwards and remove quiet splash;
 
Add the following parameter:
 
i915.modeset=1
 
In other words, the boot should look like this:
 
**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz i915.modeset=1 --**
 
Now hit Enter and hopefully you will be at the desktop admiring Lucid Lynx 10.04.
 
This is taken from my reply to another post on the forum where someone, like me, was having issues with even booting the LiveCD.
 
I hope this helps people with Intel graphics chipsets.
 
Good luck!
:)

---

### Post by bumblestiltskin on 2010-05-05
> **Rubi1200 said:**
> Regarding this known bug affecting Intel graphics chipsets:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I have found/stumbled upon by accident a workaround that allows the LiveCD to be booted after people reported the process stalling at a black screen.

This is taken from my reply to another post on the forum where someone, like me, was having issues with even booting the LiveCD.

I hope this helps people with Intel graphics chipsets.

Good luck!
:)

I started the thread for this issue and Rubi1200 was kind enough to post his findings and get me going. Once I got the Live CD to boot, it installed just fine and on reboot came up to a fully functioning desktop. I didn't need to use the workaround he linked to, the drivers were already installed correctly. So it appears -- and this is just from my experience I'm basing it on -- that the drivers get installed correctly, but are not active/included on the Live CD.

If interested, all the gory details are here:

[http://ubuntuforums.org/showthread.php?t=1472054]("http://ubuntuforums.org/showthread.php?t=1472054")

---

### Post by MrPok on 2010-05-05
> **jschille said:**
> In Response to Bootup/Plymoth Instructions:

The commands will only work for Grub2, not legacy.
To install Grub2 before following the instructions on how to fix Plymoth screen.

 	Code:
 	sudo apt-get remove grub
sudo apt-get install grub-pc
sudo grub-install /dev/sda
sudo update-grub2 
Then follow the instructions stated in the OP post.

..

Hope this helps.

Note that your instructions do not comply with those in the official [Ubuntu Documentation > Community Documentation > Grub2]("https://help.ubuntu.com/community/Grub2") stating:
> ..allows the user to test GRUB 2 by adding an entry to their normal GRUB menu. Select "Yes" to place a _**Chainload**_ option on the GRUB menu. When GRUB boots the next time, the user can select a normal GRUB entry or transfer control to GRUB 2 via the Chainload entry.

Starting out with a removal of GRUB might not be an ideal way to go.

---

### Post by qorron on 2010-05-12
this solution should be added to the bug regarding some UMTS modems  stop working in 10.04:
[http://ubuntuforums.org/showthread.php?p=9244786#post9244786](http://ubuntuforums.org/showthread.php?p=9244786#post9244786)

adding the line:
```
apt-get install usb-modeswitch
```
would be sufficient.
this way, affected users do not have to read through the bug reports and have an easy and working solution at hand.

---

### Post by philinux on 2010-05-12
@qorron, done.

---

### Post by Zimmer on 2010-05-13
Re Printing.
Anyone else NOT seeing CUPS loaded at boot time?

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/554172)

Work around..
Start cups service from terminal

> sudo service cups restart

UPDATE: Was using NOUVEAU video driver for my NVIDIA card. Have installed NVIDIA proprietary driver and spent 2 hours booting and restarting. CUPS is now starting at boot time....  (will monitor situation... just in case..)

EDIT 25 May 2010
Not solved, still intermittent...

---

### Post by hawthornso23 on 2010-05-15
If you have both xubuntu-desktop and ubuntu desktop installed then  the upgrade from Karmic may fail with the message

> 
Could not calculate the upgrade
 An unresolvable problem occurred while calculating the upgrade:
The package 'ubuntu-desktop' is marked for removal but it is in the removal blacklist.
  This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu
 If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
This is a bug in upgrade manager caused by a conflict in audio library requirements.
[https://bugs.launchpad.net/ubuntu/lucid/+source/update-manager/+bug/571743](https://bugs.launchpad.net/ubuntu/lucid/+source/update-manager/+bug/571743)
The bug may also be triggered if other additional desktop combinations are present.

The [COLOR=Red]Workaround[/COLOR] is to uninstall extra desktops - then upgrade - then reinstall extra  desktops.

UPDATE: This bug now seems to be fixed.

---

### Post by rdkflucks on 2010-05-17
I noticed that a lot of people are having problems with sound after upgrading. I was totally upset and not thinking clearly when it first happened to me, took an hour or so to realize the obvious fix. 

> Go to Terminal. 
> Type "alsamixer" (without quotes).
> Make sure that Master, Headphones, Speaker, etc. are turned all the way up (or at least to the point that you want them to be.

This seems to work for people who say they can see that their system is playing something, but they can't hear anything.

---

### Post by KlavKalashj on 2010-05-19
There seems to be a lot of trouble with changing screen brightness on some Asus laptops. I think this applies to some Eee-models, and also UL-models. Here is the launchpad bugreport:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543294](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/543294)

And here two threads about it: 

[http://ubuntuforums.org/showthread.php?t=1468734](http://ubuntuforums.org/showthread.php?t=1468734)
[http://ubuntuforums.org/showthread.php?t=1481849](http://ubuntuforums.org/showthread.php?t=1481849)

And here is the solution (from the first thread):

1. Open a terminal (Program - Accessories - Terminal)
2. Type in "sudo gedit /etc/default/grub" (without the "")
3. Find the line that says: GRUB_CMDLINE_LINUX="quiet splash"
4. Edit it so it says: GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"
5. Save and exit
6. Run the command "sudo update-grub" (again without quotes of course)
7. Reboot and enjoy!

---

### Post by nigels on 2010-05-24
Regarding VNC (Desktop Sharing)

It appears that it's necessary to turn off desktop effects for VNC to work from other machines.

See also:
[http://ubuntuforums.org/showthread.php?t=1417146](http://ubuntuforums.org/showthread.php?t=1417146)
[http://ubuntuforums.org/showthread.php?t=1383356](http://ubuntuforums.org/showthread.php?t=1383356)

---

### Post by Eddie Wilson on 2010-05-25
This has to do with the problem Brasero is having not being able to burn an audio CD using an mp3 play-list from Rhythmbox or using nautilus.

The problem with Brasero has been fixed upstream. Below is a link to the bug report and at the end of the report is a link to a Brasero build with the fix applied. Thanks to all who helped.

[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/543892](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/543892)

---

### Post by stefan_g on 2010-05-26
**Sound: Weird/broken surround-sound volume control**

Since Karmic (9.10), a lot of people had and still have problems with correctly changing the volume of their speakers within a surround sound setup. An according launchpad link is [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948"). 

The background is PulseAudio trying to make everyone's life easier and providing simpler volume controls, which hide the actual hardware controls, as these are often not to easy to understand for the average user, and different settings may lead to the same output volume but with different quality (see here: [http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes]("http://pulseaudio.org/wiki/PulseAudioStoleMyVolumes")). Unfortunately, this good approach seems to have trouble with certain sound cards, e.g., with my SoundBlaster Live. I do not know who is to blame for that (PulseAudio, Alsa, Hardware), and this question is clearly beyond the scope of this guide.

The problem is known (e.g., see launchpad link above, or [http://ubuntuforums.org/showthread.php?t=1234894&page=3](http://ubuntuforums.org/showthread.php?t=1234894&page=3)), and several workarounds can be found, e.g., [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats#Volume%20range%20anomalies"), but none did suffice for me, as they all left me with some channel controls disabled.

I think I found another workaround which has not been posted here yet. The post is rather long. I'm sorry for that, but I wanted to provide at least a little background information, as well as a (hopefully) foolproof step-by-step guide to this workaround (ment to be usable by the average or even beginning user).

**_My (sound) system setup_**
[LIST]
[*] Ubuntu 10.04 (Lucid)
[*] Sound Blaster Live Value, a PCI card with two 2channel analog output jacks
[*] a traditional surround-4.0 speaker setup, i.e., two front and two rear speakers
[/LIST]

**_What I want_**
The traditional 4.0 surround sound and the ability, to control the individual speakers properly.

**_What I get_**
The sound preferences gui lets me choose "Analog 4.0 output and Mono input", which matches my physical setup so far. All speakers are indeed working, but changing the volume results in very strange changes of the individual channel volumes: The rear speakers reach a high volume very quickly, and only after that, the front speakers catch up and finally even drown out the rear ones. 

Running "alsamixer" from a terminal reveals: Among others, my sound card has controls named Master, PCM, and, Surround. The first strange thing is: Master only controls the front speakers, Surround only the back speakers, and PCM both, but not in the same way. When increasing only the PCM control, the front speaker volume is actually increasing (much!) more than the rear speaker volume!

Anyway, this first strangeness is totally up to ALSA, and not PulseAudio. In fact, PulseAudio correctly identifies the responsible channels. However, when increasing the volume via PulseAudio (now using the volume applet at the panel), at first, PCM is JUMPING to a high level, shortly afterwards followed by Surround, and finally, followed by Master. Furthermore, all unused channels (for me: Center and LFE) are set to 100% by PulseAudio.

Apparently, this strange behavior has been observed many times before (see links provided above). Starting with Ubuntu 9.10 (Karmic), it happens each time, anything else than classical stereo sound is used.


**_Which workarounds did NOT work_**
If you don't understand everything/anything in here, don't mind, and skip to the next section.

[LIST=1]
[*]Passing "ignore_dB=yes" to module "module-udev-detect" or to module "module-alsa-card". This resulted in PulseAudio only controlling the master channel, i.e., my front speakers.
[*] Restrict controls to PCM-only, as has been proposed by others before. First of all, I want to control ALL of my four channels. Second of all, my PCM control itself is weird (as mentioned above).
[*] Using "module-detect" instead of "module-udev-detect". I didn't manage to get surround sound then, even if the number of channels has been set to 4 in daemon.conf. 
[/LIST]

**_What finally DID work_**
The solution for me was to deactivate any auto-detection and to use "module-alsa-sink" instead of "module-alsa-card" (which is used as the result of auto-detection via "module-udev-detect").

**Step-by-Step guide:**

[LIST=1]
[*] Please start with a clean system, i.e., you have not tampered with any files in "/etc/pulse/", "~/.pulse/", "/usr/share/pulseaudio", or "/usr/share/alsa" (if you don't know what that is, you haven't).
[*] Open a terminal (Applications->Accessories->Terminal). From this point, any commands have to be typed in there, if not stated otherwise.
[*] Find the ALSA number of your sound card. If you only have one sound card, it is "0". Otherwise, run "aplay -l | grep card" (within the terminal, without the qoutes). See the word "card" followed by a digit followed by a string with the name of the sound card? Pick the digit. And don't worry that the same card is there multiple times.
[*] Run "cp /etc/pulse/default.pa ~/.pulse/". Now run "gedit ~/pulse/default.pa". A text editor with that file opened should pop up.
[*] Within the text editor, find line ".ifexists module-udev-detect.so". Outcomment this line by prepending a "#" to it. From this line, outcomment all following lines until the first ".endif", inclusively (you should now have typed in five "#" letters). 
[*] Still within the text editor, and after the ".endif" line you just outcommented, add a line "load-module module-alsa-sink device=surround40:0" (without the qoutes, of course). Change the digit after the colon to the one of your card (see step 3). Change the "surround40" to your speaker setup accordingly. For example, for two front, one center, and two rear speakers, as well as a subwoofer (that has a separate jack at the sound card), change it to "surround51". Don't forget to save. ;-)
[*]  Restart pulseaudio by running within the terminal "killall pulseaudio". PulseAudio will restart immediately with the new configuration. Please note, that any previous volume adjustments within the panel volume applet need to be done again (from PulseAudio's view, we now have a new device, for which no user settings exist yet).
[*] Make the terminal window wider and run "alsamixer". Now move the panel applet's volume slider around. If everything is ok, the sliders within alsamixer do NOT move, i.e., the hardware sliders do not move, but the volume is nevertheless actually changing. This means, PulseAudio now does the volume control in software, but this volume cannot exceed the maximum hardware settings. Therefore, within alsamixer, adjust the sliders to the balance and maximum volume you desire. For example, I have chosen Master and Surround to be 87%, and PCM to be 65%.
[/LIST]

Congratulations, you made it. :-)

**_Shortcomings of the approach_**
Is this a solution? No, it is merely a workaround with several issues:
[LIST=1]
[*] Probably most severe, we now have a static setup. So forget your usb headset plugged in during runtime. Actually, currently  we don't even have setup any static input (microphone).
[*] Volume control is done in software instead of hardware, which may result in suboptimal noise-loudness ratios.
[*] A verbose log showed that this method neither allowed for memory-mapped IO, nor for PulseAudio's timer-based scheduling method, although my card actually provides the required capabilities (shown in a log with the original flawed method). This means, both CPU load and latency may be suboptimal.
[*] From a user's point of view, setting up such a workaround is inacceptable.
[/LIST]

So lets hope that this issue is actually resolved eventually (it's known for over half a year now, *sigh*). Unless this isn't done, I will have to stick to the workaround.

I hope this will help at least some of you.
May the force be with you ;-)

Best wishes,
-- Stefan

---

### Post by kleeman on 2010-05-31
Many laptops are running hot with reduced battery life under Lucid. This bug seems to be the core problem:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281)

A fix that worked for me on two laptops and also for one other user (so far) is to revert to the Karmic kernel:

[http://ubuntuforums.org/showpost.php?p=9388329&postcount=48](http://ubuntuforums.org/showpost.php?p=9388329&postcount=48)

My laptops are running 5C cooler and powertop reveals a more than 50% drop in wakeups.

---

### Post by KermEd on 2010-05-31
Users who use the package command and Manage 3rd Party Software may become disabled during the upgrade.  This is from MailAgent replacing Package with its own Package command.  Happened to me upgrading from 9.10 to 10.04.

The error message they will see is:  [FONT=Courier New]Reply:   package: can't open config file  /home/test/.mailagent[/FONT]

More information: [ http://ubuntuforums.org/showthread.php?t=1497640]("http://ubuntuforums.org/showthread.php?t=1497640")
Autopackage Group: [http://watteimdocht.de/autopackage/forum/viewtopic.php?f=4&t=239](http://watteimdocht.de/autopackage/forum/viewtopic.php?f=4&t=239)
Launch Pad: [https://answers.launchpad.net/ubuntu/+question/112892](https://answers.launchpad.net/ubuntu/+question/112892)


The simple work-around is to use Autopackage (as a command) in place of Package.  However to recover the ability to use Manage 3rd Party Software users will need to use the following:

**Step 1-** Launch *Terminal*
    Enter: [FONT=Courier New]sudo apt-get remove MailAgent[/FONT]

*MailAgent* uninstalls and removes the faulty package command with  it.

**Step 2-** Download the following package to your*  ~/Downloads/autopackage* folder
    [http://autopackage.googlecode.com/files/autopackage-1.4.2-x86.tar.bz2](http://autopackage.googlecode.com/files/autopackage-1.4.2-x86.tar.bz2)
    *Note: This will install the PACKAGE command again for terminal

**Step 3-** Extract it to *~/Downloads/autopackage*
    *Note: You can place this somewhere else if needed

**Step 4-** Switch to Terminal
    Enter:  [FONT=Courier New]cd ~/Downloads/autopackage[/FONT]
    *Note: You should be in the same folder as the Install script

**Step 5-** Enter:  [FONT=Courier New]sudo ./install[/FONT]
    Enter Password

It will attempt to install the GUI which will likely fail on the URL's  for the GUI.  We will install the GUI separately.

**Step 6-** Enter:  [FONT=Courier New]man package[/FONT]

You should see and verify the regular package command succeeded before  moving on.

**Step 7-** Download the following package to your *~/Downloads/autopackage  *folder
    [http://autopackage.googlecode.com/files/autopackage-gtk-1.4.2.package](http://autopackage.googlecode.com/files/autopackage-gtk-1.4.2.package)
    *Note: This installs your *Autopackage* GUI

**Step 8-** Switch to Terminal
    Enter:  [FONT=Courier New]sudo package install  autopackage-gtk-1.4.2.package[/FONT]

You should now have your full auto-package re-installed.  Including  support for 3rd Party Applications and Removal of programs again.

:guitar:

---

### Post by bhadotia on 2010-06-11
People using pppoe connections lose their nrtwork manager applet after configuring the connection and rebooting. The bug report just explains the rest along with the workaround.:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/577678](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/577678)

---

### Post by Spr0k3t on 2010-06-17
After troubleshooting an issue with low resolution on the nvidia graphics with 3D hardware.  I've come across a temporary solution.

The problem: On boot, the error message "Could not apply the stored configuration for monitors X server does not support size requested" would show up and the resolution would be 640x480.

I found the problem is related to the nvidia-current 195.36.24-0ubuntu1~10.04 version.  So, I rolled back the version to 192.36.15-0ubuntu2 version and locked the version.  The same had to be done with nvidia-current-modaliases.

I'm checking to see if there's a bug posted regarding this.

---

### Post by recluce on 2010-06-18
In Lucid, Simple Backup or sbackup does absolutely nothing when hitting the "Backup Now" button, the backup process just goes Zombie. 

I found the solution on Source Forge and posted it here:

[http://ubuntuforums.org/showthread.php?t=1480520](http://ubuntuforums.org/showthread.php?t=1480520)

The solution is in post #8 of this thread

---

### Post by psullie on 2010-06-18
[B]SVG & PDF with linked remote assets crashing the window manager
[/B]
I've found that when viewing directories with SVG and/or PDF files that contain remote linked or missing assets will cause the window to stop responding. 

Removing the SVG & PDF files (with terminal) is necessary to sucessfully navigate the directory.

SVG files with local assets seem to be okay

My guess is that the viewer is trying to render a thumbnail (the clock icon is displayed) but fails and hangs.

Sullie

---

### Post by ToshibaLaptoplinux on 2010-06-23
There has been a problem with Appearance Preferences setting NOT being preserved upon reboot/logoff.

The pertinent Launchpad bugs can be found at:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/593252](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/593252)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/390001](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/390001)
[https://bugs.launchpad.net/bugs/482538](https://bugs.launchpad.net/bugs/482538)
[https://bugs.launchpad.net/bugs/482539](https://bugs.launchpad.net/bugs/482539)

The solution that worked for me was to re-save my Gnome Session in the Start-Up Applications dialogue ([http://ubuntuforums.org/showthread.php?t=1264495](http://ubuntuforums.org/showthread.php?t=1264495))

---

### Post by corruptor1972 on 2010-07-03
A fantastic tool for speeding-up DNS lookups (Talk:Talk users take note!) by using a local cache is pdnsd.

However when used with NetworkManager it stops working on making a new connection.  The solution is to restart pdnsd after the network connection is made, but this is inconvenient so a script can be written for NetworkManager to do this restart for you.

[Click here for details in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/pdnsd/+bug/452351").

---

### Post by Meneer Jansen on 2010-07-17
Every computer is unique, just like every human that uses it. ;) I opened a [topic]("http://ubuntuforums.org/showthread.php?t=1531810") about the specific problems that I ran into after installing Ubuntu 10.04 *The Lucid Lynx* on my computer.

A lot of solutions to my probs are already in this topic, or on these Ubuntu forums. But a few of my  solutions/workarounds may be of interest to others:

[LIST]
[*]Old Nvidia cards, xorg.conf and Copmiz.
[*]The Alsa bit of saa7134 based TV cards has problems (bug report filed; no hope of sloution).
[*]Calendar: Sunbird/Lightning.
[*]Make antique GTK1 apps (like Turbprint 1.96 and XDialog) look appealing.
[*]XBox Media center (XBMC) and bloody *libcdio*.
[/LIST]

Thank y'all for prroviding me w/ a lot of solutions to the many caveats in 'Lucid'. :)

---

### Post by JedMeister on 2010-07-17
> **kleeman said:**
> Many laptops are running hot with reduced battery life under Lucid. This bug seems to be the core problem:

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/524281)

A fix that worked for me on two laptops and also for one other user (so far) is to revert to the Karmic kernel:

[http://ubuntuforums.org/showpost.php?p=9388329&postcount=48](http://ubuntuforums.org/showpost.php?p=9388329&postcount=48)

My laptops are running 5C cooler and powertop reveals a more than 50% drop in wakeups.
Like kleeman says there is a kernel bug that effects Lucid. Whilst it is more obvious with Laptops and other portable systems (as they rely on battery use and users notice the heat increase) it actually effects power consumption on all Karmic systems (well I've only tested on Intel CPUs). As suggested in the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281"), it is actually an upstream kernel bug and affects all Linux OSs using this kernel version. There are reports that the bug still exists in the kernel used by Maverick.

As suggested in kleeman's post, one workaround is to use the Karmic kernel. Users now have another option! [Brian Rogers]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/524281/comments/80") has kindly provided a [PPA]("https://launchpad.net/~brian-rogers/+archive/power") which includes a Maverick kernel with a couple of patches applied. I haven't personally tested it in Lucid but others have reported in the bug post that it is a huge improvement.

---

### Post by Tak11 on 2010-08-06
Touchpad users have noticed their mouse has a 3-4 second lagg if their holding down any key, this is obviously a big problem as it makes games unplayable. 

This is because of a default setting "Disable mouse while typing" disable this setting from
system->preferences->mouse->touchpad

If you turn it off in the gconf editor it will now work.

[https://lists.launchpad.net/ubuntu-x-swat/msg82093.html]("https://lists.launchpad.net/ubuntu-x-swat/msg82093.html")

*the problem is also fixed using an external mouse.*

---

### Post by xiboce on 2010-09-07
CPU overload due to conflict between metacity and compiz.
Bug still not issued according to launchpad, however:

[http://ubuntuforums.org/showthread.php?p=9815898#post9815898](http://ubuntuforums.org/showthread.php?p=9815898#post9815898)

---

### Post by jeebustrain on 2010-09-24
regarding the shutdown issue - I required the gconf-editor modification "use_time_for_policy" change when I installed Ubuntu Lucid. 

I just recently gave Kubuntu Lucid a shot on the same laptop and am experiencing the same issue. Does anyone know the equivilent setting for KDE? I can't seem to find an appropriate option in the power config.

---

### Post by dugjones on 2010-11-24
[SOLVED] After screwing around with modifying the xorg.conf, installing pre-released updates and the whole nine yards for HOURS we finally fixed this issue with some voodoo. We had even tried installing Ubuntu 10.10 to see if something was fixed in there versus 10.04. Here is what we did that worked instantly:

We turned off the computer and unplugged it. We turned off both monitors and unplugged them and unplugged the vga and dvi cables from the computer. We waited for about 20 seconds and then plugged everything back in and turned it back on.

Once it came back up it correctly identified the monitors as Planar PL1910M's and offered the correct resolutions. We were able to go into the nvidia software and enable TwinView with no problem. I will not claim to understand it which is why I claim voodoo but I really hope this helps someone out.

---

### Post by MountainX on 2010-12-09
> **philinux said:**
> 

Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```

FYI, this didn't fix it for me. I'm using dual monitors and an nvidia card with Maverick. Furthermore, it should be pointed out that this fix "introduces a significant delay into boot just to get the splash screen up." So I am going to try to undo the change.

---

### Post by jaikamal on 2011-08-18
Recently i upgraded from Ubuntu 9.10 to 10.4. After that i am not able get into the graphics mode. when i try to use graphics mode, my machine getting hanged with a black screen but mouse is working. Kindly help me to recover from this problem.

Thank you

---

