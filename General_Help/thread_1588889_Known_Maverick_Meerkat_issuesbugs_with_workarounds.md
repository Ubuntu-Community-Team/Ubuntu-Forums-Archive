---
title: "Known Maverick Meerkat issues/bugs with workarounds"
date: 2010-10-05
forum: General Help
---

### Post by CharlesA on 2010-10-05
***Disclaimer :***

**The purpose of this thread is to list solutions for common problems with Maverick Meerkat.**

Feel free to propose other known Maverick Meerkat bugs to be listed here but please provide a link to the workaround and a link to the corresponding launchpad entry.

Please do not use this thread for support questions, either start a thread or use Launchpad.

-------------------------------------------------

[B][COLOR=DarkRed]Warning: Before upgrading or attempting a reinstall make sure you backup essential files.[/COLOR]

Please read the Release Notes:[/B]
[http://www.ubuntu.com/getubuntu/releasenotes/1010](http://www.ubuntu.com/getubuntu/releasenotes/1010)

Check out this [thread]("http://ubuntuforums.org/showthread.php?t=1588658") as well for commonly asked questions regarding **Downloading the Ubuntu 10.10 Final Release.**

-------------------------------------------------

**_GPG Errors_**: If you get the following error message:

> W: An error occurred during the signature verification. The repository  is not updated and the previous index files will be used.
GPG error: [http://extras.ubuntu.com]("http://extras.ubuntu.com/")  maverick Release: The following signatures couldn't be verified because  the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)Run:

```
gpg &#8211;keyserver keyserver.ubuntu.com &#8211;recv 3E5C1192
gpg &#8211;export &#8211;armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```-------------------------------------------------

**_Virtualbox_**: Oracle released a new version of Virtualbox, Virtualbox 3.2.10 , shortly after the release of Ubuntu 10.10.

If you upgrade to Virtualbox 3.2.10 the guest additions are working in both Ubuntu 10.10 and Fedora 14.

[See this link for details](http://www.sysprobs.com/oracle-virtualbox-3210-supports-ubuntu-1010-fedora-14-guest-additions-iso)

If you wish to continue to use Virtualbox 3.2.8 , first install the guest additions from the iso , then install the opensource X11 guest additions from the Ubuntu repositories.

```
sudo apt-get install virtualbox-ose-guest-x11
```
 When asked, accept (type "y") to install the maintainers version.

---

### Post by NightwishFan on 2010-10-10
Bug Report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
```
load-module module-udev-detect
```

It should look like this:
```
load-module module-udev-detect tsched=0
```

Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

---

### Post by alexfish on 2010-10-11
**3g broadband dongles**: 

original post removed
The how to in tuts an tips now updated for udev rules and driver problems + port detection

POST #[**2**]("http://ubuntuforums.org/showpost.php?p=9201405&postcount=2")
[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

alexfish

---

### Post by lotharmat on 2010-10-12
@rps63ifid, gdonwallace

> Please do not use this thread for support questions, either start a thread or use Launchpad.

You may get a better response to support questions if you post a new thread.

---

### Post by CharlesA on 2010-10-12
Moved support requests to seperate threads.

---

### Post by Ingdawg on 2010-10-12
I have the exact above GPG error. I am trying the above fix but not getting it to work. I could also be doing it wrong. I'm an Ubuntu newbie.

---

### Post by The Cog on 2010-10-12
**Epson scanners**
simple-scan and xsane both fail to scan from an Epson Perfection 640. I haven't tried xsane, but the following fix made simple-scan work for me.

Bug report link: [https://bugs.launchpad.net/bugs/632026](https://bugs.launchpad.net/bugs/632026)

Fix: Edit file **/etc/sane.d/dll.conf** and find the lines for epson and epson2. Uncomment epson and comment out epson2 instead, to they look like this:
> epson
#epson2
The original fix proposal ([http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9943325](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9943325)) also suggested adding a line to /etc/sane.d/epson.conf. I found this not necessary to get simple-scan working, but maybe it is needed for xsane.

---

### Post by jkxx on 2010-10-12
The preferred applications applet in Gnome does not work. Different applications can be selected but the new selection has no effect and the default is launched anyway.

Bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/657454]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/657454")

Fix:

For multimedia, one can right-click on the file, select "Open With..." and then "Other application" and pick a different app while checking the "Remember this application..." check box. This will cause the new application to open that particular type of file.

E-mail: currently no fix, evolution is launched no matter. In my case I installed thunderbird and made a shortcut on my desktop, which is easy enough to launch.

---

### Post by yeats on 2010-10-13
> Virtualbox: When running Ubuntu 10.10 as a guest there is a small problem with the virtualBox additions. The graphical enhancements fail with the following message:

Quote:
Warning: unknown version of the X Window System installed. Not installing
X Window System drivers.
To resolve this, install or upgrade to the latest version of VirtualBox.
__________________

An alternative solution to the VirtualBox guest X11 issue is to first install the Guest Additions as usual, then to install the package 'virtualbox-ose-guest-x11' within the Ubuntu 10.10 guest machine, then reboot the guest machine.

---

### Post by andrewthomas on 2010-10-13
> **philinux said:**
> Other graphics card users including nVidia may  get a black screen with flashing cursor and then a very short duration  plymouth. 
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801)
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` and add this option FRAMEBUFFER=y, save the file.
Then
```
sudo update-initramfs -u

```
This issue seems to still be a problem with Maverick

---

### Post by Refalm on 2010-10-13
The Ubuntu supplied non-free nvidia driver (version 195.x) doesn't work on many modified internal cards for laptops.
Installing it results in X not starting in combination with said hardware.

If this has happened, or if you know **for sure** this is going to happen, you need the beta driver (version 260.x).
You can do that by adding the *ubuntu-x-swat/x-updates* repository and performing an update:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```If X is still not starting, add this to */etc/X11/xorg.conf*
```
Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
```[B]Only do this if you have issues with the nvidia driver,
or if you really want that 2 fps extra in CoD:MW2 while playing on your 1080p 30" LCD monitor.[/B]

---

### Post by Mr_VeRiTy on 2010-10-13
> **CharlesA said:**
> 

**_GPG Errors_**: If you get the following error message:

Run:

```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```-------------------------------------------------

This doesn't seem to work for me, terminal output below;

Output for "gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192"
```
gpg: directory `/home/luke/.gnupg' created
gpg: new configuration file `/home/luke/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/luke/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/luke/.gnupg/secring.gpg' created
gpg: keyring `/home/luke/.gnupg/pubring.gpg' created
usage: gpg [options] [filename]

```

Output for "gpg –export –armor 3E5C1192 | sudo apt-key add -"
```
usage: gpg [options] [filename]
[sudo] password for luke: 
gpg: no valid OpenPGP data found.

```

Error message at end of terminal output for "sudo apt-get update"
```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

```

---

### Post by fjctp on 2010-10-14
> **Mr_VeRiTy said:**
> This doesn't seem to work for me, terminal output below;

Output for "gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192"
```
gpg: directory `/home/luke/.gnupg' created
gpg: new configuration file `/home/luke/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/luke/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/luke/.gnupg/secring.gpg' created
gpg: keyring `/home/luke/.gnupg/pubring.gpg' created
usage: gpg [options] [filename]

```Output for "gpg –export –armor 3E5C1192 | sudo apt-key add -"
```
usage: gpg [options] [filename]
[sudo] password for luke: 
gpg: no valid OpenPGP data found.

```Error message at end of terminal output for "sudo apt-get update"
```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9BF3BB4E5E17B5

```

Hi,
I got the same thing too.
what's wrong?

---

### Post by Akaedintov on 2010-10-14
> **Refalm said:**
> The Ubuntu supplied non-free nvidia driver (version 195.x) doesn't work on many modified internal cards for laptops.
Installing it results in X not starting in combination with said hardware.

If this has happened, or if you know **for sure** this is going to happen, you need the beta driver (version 260.x).
You can do that by adding the *ubuntu-x-swat/x-updates* repository and performing an update:
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```If X is still not starting, add this to */etc/xorg.cfg*:
```
Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
```[B]Only do this if you have issues with the nvidia driver,
or if you really want that 2 fps extra in CoD:MW2 while playing on your 1080p 30" LCD monitor.[/B]


/etc/xorg.cfg

No such file or directory...

---

### Post by Refalm on 2010-10-14
> **Akaedintov said:**
> /etc/xorg.cfg

No such file or directory...
:oops:

It should be: /etc/X11/xorg.conf

---

### Post by bodhi.zazen on 2010-10-14
> **chrissharp123 said:**
> An alternative solution to the VirtualBox guest X11 issue is to first install the Guest Additions as usual, then to install the package 'virtualbox-ose-guest-x11' within the Ubuntu 10.10 guest machine, then reboot the guest machine.

That is the solution posted origionally.

With the release of Virtualbox 3.2.10 the issue is now fixed (and I am updating the post).

---

### Post by jkxx on 2010-10-15
This is a similar problem to the one andrewthomas mentions.

Attempting to boot off the live CD to install Ubuntu can result in the screen blinking a few times and then going black. This happened on a PC with a geforce 6600GT video card so it was a case of nouveau not handling that card correctly.

Here's one way to get around that and get Ubuntu to boot so it can be installed:

Right after the "ISOLINUX" linux appears, tap the Esc key several times. The options menu included in earlier versions of Ubuntu should appear.

Press F6 to activate the 'other options' menu, then use the arrow keys to get to the "nomodeset" line. Press Enter to activate the option - you should see a checkmark next to it once you've enabled it.

Now you can go back to the first menu and choose either "Try ubuntu without installing" or "Install". Both should load a desktop that works enough to install from.

NOTE: This tip only helps with the live cd. After ubuntu is installed it will not respond to pressing the Esc key. In this case you can try pressing Ctrl+Alt+F1 to get to a console and log in as yourself, then execute a

sudo apt-get install nvidia-current (for Nvidia geforce 6+ users) and let it install the binary driver for you.

Another alternative that should give you a working desktop is the vesa driver, although I'm not sure how to get that set up without manually editing the xorg.conf file.

---

### Post by cg0191 on 2010-10-15
> **NightwishFan said:**
> Bug Report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
```
load-module module-udev-detect
```It should look like this:
```
load-module module-udev-detect tsched=0
```Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

I have stuttering sound in embedded videos on web pages in firefox.
This simple change fixed it.
How in gods name does such simple things get missed by QA before release???

---

### Post by kio_http on 2010-10-15
Kubuntu 10.10 ubiquity installer manual partitioning mode fails to delete partition (Installer crashes with error concerning parted)

Workaround:
Do the partitioning in another tool. You can use gparted live cd.

Or install a partitioner from the repositories while trying the live cd.

---

### Post by timgood on 2010-10-16
If you have problems adding your Facebook account to Gwibber following upgrade to 10.10, go to your home folder in Nautilus. Press CTRL+H to view hidden files and navigate to the .config/gwibber folder. Delete the gwibber.sqlite file and restart Gwibber. You should now be able to add your Facebook account.

Hope this helps.

---

### Post by NightwishFan on 2010-10-16
If you are experiencing poor video quality using Totem when it was fine before this may be because deinterlacing is enabled. Go to Edit -> Preferences -> Display, and check "Disable Deinterlacing".

> **timgood said:**
> If you have problems adding your Facebook account to Gwibber following upgrade to 10.10, go to your home folder in Nautilus. Press CTRL+H to view hidden files and navigate to the .config/gwibber folder. Delete the gwibber.sqlite file and restart Gwibber. You should now be able to add your Facebook account.

Hope this helps.

This works fine! :)

---

### Post by sendblink23 on 2010-10-16
No clue if I should post this here.. but it could help new people using Ubuntu 10.10 or users who are having this issue using this driver ATI/Nvidia... System > Administration> Additional Drivers

If you have V-Sync issues(screen tearing) on **ATI** cards - using the driver from - System > Administration > Additional Drivers

Activate/Install the driver & reboot

***Single cards users:**
**1.** 
First make sure you have, CCSM (System > Preferences > CompizConfig Settings Manager): go here if you don't have it to enable it - [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695) 

**2.**
Go to System > Preferences > CompizConfig Settings Manager > General Options > Display Settings >
Texture Filter - Best
Detect Refresh Rate - Un-Checked
Refresh Rate - set it according to your monitor, for my monitor its 60
Detect Outputs - Checked
Sync To VBlank - Checked

Click Back & close CCSM

**3.**
Go to System > Preferences > ATI Catalyst Control Center
3D > More Settings >
Wait for vertical refresh - set it to Quality (Always On)
Click OK

Now restart the computer and enjoy no more vsync issue/screen tearing

***CrossfireX users:**
Activate/Install the driver & reboot

Go to System > Preferences > ATI Catalyst Control Center(Administrative)
CrossfireX > Enabled > Apply > OK > Restart Computer

Follow Steps: **1**, **2** & **3** Enjoy

-----------------------------

If you have V-Sync issues(screen tearing) on **Nvidia** cards - using the driver from - System > Administration > Additional Drivers

Activate/Install the driver & reboot

The rest its pretty much the same as ATI's process on CCSM (Step **1** & **2**)... then go to
System > Administration > Nvidia X Server Settings
X Server XVideo Settings > Sync To VBlank *Checked
OpenGL Settings > Sync to VBlank *Checked

Close the Window, restart the computer and enjoy no more vsync/tearing issue.

*SLI no clue don't own one :P I'd imagine you'd enable it through the Nvidia Settings

-------------

This worked for me testing on my own on Ubuntu 10.10 x64 & x86 -  for my ATI CrossfireX 5770's & for my Nvidia 9800GTX+... pretty certain it should work for most others as well.. If I mentioned something wrong please correct me ;)

---

### Post by James78 on 2010-10-16
I have screen tearing and I'm using onboard Intel. :(

Anyways, just like in 10.04, Plymouth still isn't showing on system startup (due to graphics not being initialized quickly enough). The 10.04 fix for this works just the same, which was...
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u
```

Additionally, when I upgraded my Ubuntu Server from 10.04 to 10.10, the message of the day would show the regular 10.10 message, but also had the old 10.04 message.. Like so:
```
Linux server 2.6.35.6-server #1 SMP PREEMPT Wed Sep 29 10:05:02 EST 2010 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to the Ubuntu Server!
* Documentation: http://www.ubuntu.com/server/doc

System information as of Fri Oct 15 10:47:55 EST 2010

System load: 0.0 Processes: 112
Usage of /: 11.1% of 269.51GB Users logged in: 1
Memory usage: 20% IP address for eth0: 172.16.0.245
Swap usage: 0%

Graph this data and manage this system at https://landscape.canonical.com/

Ubuntu 10.04.1 LTS

Welcome to the Ubuntu Server!
* Documentation: http://www.ubuntu.com/server/doc

System information as of Thu Oct 14 17:57:00 EST 2010

System load: 0.08 Processes: 123
Usage of /: 11.0% of 269.51GB Users logged in: 2
Memory usage: 25% IP address for eth0: 172.16.0.245
Swap usage: 0%

Graph this data and manage this system at https://landscape.canonical.com/

5 packages can be updated.
0 updates are security updates.

*** System restart required ***
```
Fix is to open the file /etc/motd.tail, and empty everything out of it.

---

### Post by sendblink23 on 2010-10-16
> **James78 said:**
> I have screen tearing and I'm using onboard Intel. :(

I've only tested on a 950gma just using the compiz settings and it works as well after rebooting... it was on an Acer 3680 laptop
But I don't have any others to test... just realized that laptop is still using 10.04.. not 10.10.. so I will upgrade it & report back

*UPDATE* forget about it... while downloading the files to make the upgrade system froze... and somehow it killed grub or my ubuntu install on the laptop :(
If you want to help me.. go here: [http://ubuntuforums.org/showpost.php?p=9984275&postcount=21](http://ubuntuforums.org/showpost.php?p=9984275&postcount=21)

*UPDATE 2* well it seems that freeze somehow killed my root.disk from windows since its not there anymore checking the ubuntu folder within windows :( - I will now install fresh 10.10 on the laptop to try to make the *Intel testing to see if I experience any vsync/tearing issues.

---

### Post by NightwishFan on 2010-10-17
> **timgood said:**
> If you have problems adding your Facebook account to Gwibber following upgrade to 10.10, go to your home folder in Nautilus. Press CTRL+H to view hidden files and navigate to the .config/gwibber folder. Delete the gwibber.sqlite file and restart Gwibber. You should now be able to add your Facebook account.

Hope this helps.

I quoted you for askubuntu:
[http://askubuntu.com/questions/6994/gwibber-will-not-allow-me-to-log-into-facebook/7705](http://askubuntu.com/questions/6994/gwibber-will-not-allow-me-to-log-into-facebook/7705)

---

### Post by soldier1st on 2010-10-17
The ubuntu 10.10 CD refuses to mount but the fix is to use the DVD version instead.
also another issue: when a screensaver is set to launch automaticaly it will log you out.the fix is to disable to automatic loading of the screensavers and load them manualy or use 10.04.

---

### Post by James78 on 2010-10-17
> **sendblink23 said:**
> I've only tested on a 950gma just using the compiz settings and it works as well after rebooting... it was on an Acer 3680 laptop
Well, my computer uses the Intel Corporation 82915G/GV/910GL Integrated Graphics Controller. It was perfect in 10.04, like normal, but 10.10 seems to hate my graphics, and tears a lot. I haven't found anything useful in the logs yet. :(

---

### Post by PorkLip on 2010-10-17
**Issue:** All the fluffy Ambiance stuff from the Appearance Preference is missing after login and the panels, icons and GUI-componets in windows is rendered using some old "grey" default settings.

**Workaround:** [http://ubuntuforums.org/showthread.php?p=9969103#6](http://ubuntuforums.org/showthread.php?p=9969103#6)

**Side-effect:** Login screen is unthemed.

---

### Post by androidcupcake on 2010-10-18
> **timgood said:**
> If you have problems adding your Facebook account to Gwibber following upgrade to 10.10, go to your home folder in Nautilus. Press CTRL+H to view hidden files and navigate to the .config/gwibber folder. Delete the gwibber.sqlite file and restart Gwibber. You should now be able to add your Facebook account.

Hope this helps.

No luck! Never been able to configure Facebook on Gwibber!!

---

### Post by mbeierl on 2010-10-18
Applications using bitmap fonts have garbled output on display (emacs, xterm, etc):  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/635258)

After upgrade to maverick, I noticed vertical bars appearing in all my xterms during typing.  Moving the xterm window (or attempting to get a screenshot!) caused the garbage to clear up.

---

### Post by Wobblybob on 2010-10-18
> **NightwishFan said:**
> Bug Report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
```
load-module module-udev-detect
```

It should look like this:
```
load-module module-udev-detect tsched=0
```

Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

Great tip mate, works a treat, Thanks

---

### Post by pradap on 2010-10-20
> 
some of these devices are been reported : "[COLOR=Blue]not recognized on the system[/COLOR]" or "[COLOR=Blue]will not configure[/COLOR]"

this is due to the option driver module not loading

as a workaround the option driver can be  loaded from the terminal


    [**How to check for the option drive****r and modprobe option driver module**]("http://ubuntuforums.org/showpost.php?p=9953330&postcount=36")
  
 
 it may be necessary to use this on each new boot
 
 this problem usually disappears by  keep the system updated:guitar:
_____________________________________
[Cheap Hotels Kanyakumari ]("http://www.*****************.com") | [Kanyakumari Tourist Home]("http://www.*****************.com/tour-package") | [Kanyakumari Sunrise and Sunset]("http://www.*****************.com/budget-hotel-offers")

---

### Post by SiegHard on 2010-10-20
Any fixes with touchpad horizontal scroll problem(it doesn't activate in mouse options)?

---

### Post by BLAD3_ on 2010-10-20
any other help please

---

### Post by snowguy on 2010-10-20
I had the following problems
-----------------------------
Flash player not working in full screen mode
brasero burning to disk not working
CD/DVDs ejected don't unmount properly
Alt-F2 not working

I posted already fixes I found or workarounds. see [http://ubuntuforums.org/showthread.php?t=1601356](http://ubuntuforums.org/showthread.php?t=1601356)

---

### Post by jbaranski on 2010-10-21
> **jkxx said:**
> This is a similar problem to the one andrewthomas mentions.

Attempting to boot off the live CD to install Ubuntu can result in the screen blinking a few times and then going black. This happened on a PC with a geforce 6600GT video card so it was a case of nouveau not handling that card correctly.

Here's one way to get around that and get Ubuntu to boot so it can be installed:

Right after the "ISOLINUX" linux appears, tap the Esc key several times. The options menu included in earlier versions of Ubuntu should appear.

Press F6 to activate the 'other options' menu, then use the arrow keys to get to the "nomodeset" line. Press Enter to activate the option - you should see a checkmark next to it once you've enabled it.

Now you can go back to the first menu and choose either "Try ubuntu without installing" or "Install". Both should load a desktop that works enough to install from.

NOTE: This tip only helps with the live cd. After ubuntu is installed it will not respond to pressing the Esc key. In this case you can try pressing Ctrl+Alt+F1 to get to a console and log in as yourself, then execute a

sudo apt-get install nvidia-current (for Nvidia geforce 6+ users) and let it install the binary driver for you.

Another alternative that should give you a working desktop is the vesa driver, although I'm not sure how to get that set up without manually editing the xorg.conf file.

edit: I ignored the rule about not asking questions, then I noticed it, so i hope you can delete this post, because i dont know if I can.

---

### Post by Bazon on 2010-10-22
**Issue:**
On a Samsung N150, the suspend/stanby mode often doesn't work.

**Solution:**
Use a Lucid kernel instead as proposed in the bug's comments: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640100/comments/72](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/640100/comments/72)

---

### Post by Bazon on 2010-10-22
**Issue:**
A USB-Bootstick containing Lucid Install CD created in Maverick won't boot.

**Solution:**
Type "help" after the boot prompt and hit return. Just wait and boot of the Lucid installer continues normaly.

see:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)  
[http://linuxundich.de/de/ubuntu/mit-dem-startmedienersteller-aus-maverick-erstellte-usb-sticks-mit-ubuntu-10-04-starten-nicht/](http://linuxundich.de/de/ubuntu/mit-dem-startmedienersteller-aus-maverick-erstellte-usb-sticks-mit-ubuntu-10-04-starten-nicht/)  (german)

---

### Post by andrew.46 on 2010-10-23
**Issue:** When installing the libavcodec-extra-52 package from Medibuntu in the expectation of enabling aac encoding with libfaac using the Repository FFmpeg such encoding is *not* enabled. Problem is a lower version named package by Medibuntu leaves the Ubuntu Repository libavcodec-extra-52 package as the default selected.

**Solution:** The Medibuntu package must be 'Forced' either from within Synaptic or from the commandline, not sure of the exact commandline syntax for this...

**Bug-Report:** mc4man has been good enough to file a Launchpad Bug Report here:

Maverick: the ffmpeg extra packages are versioned below maverick repo ones 
[https://bugs.launchpad.net/medibuntu/+bug/665366](https://bugs.launchpad.net/medibuntu/+bug/665366)

Andrew

---

### Post by beercz on 2010-10-23
I have temporarily gone back to lucid as the following items no longer worked in meerkat but worked fine in lucid:

My laptop would not hibernate
My USB mobile dongle wasn't recognised
My screen had several "ghost" images
My laptop occasionally froze

I've no doubt that all these issues are resolvable, or will be, but I simply don't have the time at the moment, as I use my laptop for work.

I will have another go later, when I have more time.

All good fun!

---

### Post by thebarisaxkid on 2010-10-23
> **Bazon said:**
> Issue:
A USB-Bootstick containing Lucid Install CD created in Maverick won't boot.

Solution:
Type "help" after the boot prompt and hit return. Just wait and boot of the Lucid installer continues normaly.

Thanks so much, I had that problem!

---

### Post by Bazon on 2010-10-24
Not really an ubuntu issue, but an issue with programs which define the menu-font-colour but leave the background colour to the OS:

**black font on dark grey menu background**
(e.g. skype, jdownloader)

**solution**:
In the program options, select as style "desktop-style" or "system-style" and restart the program.

---

### Post by simön on 2010-10-24
> **timgood said:**
> If you have problems adding your Facebook account to Gwibber following upgrade to 10.10, go to your home folder in Nautilus. Press CTRL+H to view hidden files and navigate to the .config/gwibber folder. Delete the gwibber.sqlite file and restart Gwibber. You should now be able to add your Facebook account.

Hope this helps.

That does not work for me. Even ```
apt-get purge gwibber gwibber-service
``` leaves the .config/gwibber folder in place. I deleted it manually, re-installed gwibber and still found my twitter & facebook account listed as added. Where is this information stored? Why does purge not remove it?
My main problem is, that I can not see or post any messages from/to facebook. So I thought a complete reinstall/reconfirm of the account might help.

Any ideas?

Thank you very much!

Simon

EDIT:
Sorry folks, in the moment of hitting 'save' hereon the forum, I found the answer: I quit gwibber, deleted the db as mentioned and then deleted every gwibber-related keyring-entry. Starting gwibber again still (!!?!) showed me my accounts, but after re-authorization of fb and twitter, I saw my messages! I do not know why it was a problem of the keys because I did not change my fb-account password.
Hope this helps someone else...

---

### Post by Sef on 2010-10-24
A [sticky]("http://ubuntuforums.org/showthread.php?t=1604868") is posted on fixing Broadcom's 43xx wireless problems. 

Note: It may not work for every Broadcom 43xx card. Some of these cards may work just fine out-of-the-box.

---

### Post by atworkwithjf on 2010-10-25
**LDAP Bug causing AD Join Failure**

This bug effects Likewise Open as shipped in the Maverick Meercat main repository.

A fix has been submitted, but for the time being the Likewise Open folks have provided a patched version which resolves the issue.

Details here:

    [http://ubuntuforums.org/showthread.php?t=1603486](http://ubuntuforums.org/showthread.php?t=1603486)

---

### Post by donato roque on 2010-10-25
Update-Manager(GUI) Does Not Update After Prompting User

After clicking "Install Updates", error message saying installing from unsafe source.  I checked my software sources and nothing is wrong with them. 

I ran Gnome-Terminal and started update.

Code:
user@user-desktop:~$sudo apt-get update && sudo apt-get upgrade

The update proceeded without a glitch.  Note: It might be my Dropbox update.  Or the update affects Dropbox, a third-party application.

---

### Post by coldraven on 2010-10-26
With the64bit version the Ubuntu Software centre has a bug.
After entering your password and pressing "Authenticate" the text entry box vanishes and leaves a window with just "Authenticate". 
Clicking on this does nothing, install only starts if you close the box.
See the screenshots.

Update: As of 28th. October 2010 this seems to be fixed.
Update: January 2011, this bug is back in both the software centre and the update manager

---

### Post by orrie on 2010-10-26
This is not really a issue, but the hotkey for "Show Desktop" is changed from <Control><Alt>d to <Super>d.
If you want the old hotkey, you can fix it this way.

**Solution:** Press <Alt><f2> and run *gconf-editor*.
Navigate here: apps -> metacity -> global_keybindings
Edit the *show_desktop*-key, and change from <Super>d to <Control><Alt>d.

---

### Post by Sunflower1970 on 2010-10-26
Hoping I'm not the only one having this problem:
**Issue** Using a Microsoft wireless natural keyboard and mouse. Clicking Ctrl+t in any program that allows one to open more tabs, such as Firefox, a terminal, nautilus causes the mouse and the keyboard to become inactive. 
**Solution** Drop in to a console: ctrl+alt+F1, log in, then go back to X ctrl+alt+F7, and all should be fine. 

I've tried other solutions I've found on launchpad, and here and this is the only workaround I've found to be successful for me. Hope others may find it useful.

---

### Post by Lancro on 2010-10-27
> **coldraven said:**
> With the64bit version the Ubuntu Software centre has a bug.
After entering your password and pressing "Authenticate" the text entry box vanishes and leaves a window with just "Authenticate". 
Clicking on this does nothing, install only starts if you close the box.
See the screenshots.

Have you found a solution?, having same bug here!!

Thanks.

---

### Post by coldraven on 2010-10-28
Epson Scanner and Xsane

I got my Epson Perfection 1670 scanner working with Xsane by following this:
[http://ubuntuforums.org/archive/index.php/t-26911.html](http://ubuntuforums.org/archive/index.php/t-26911.html)

For other scanners the BIN file should be found in C:\WINDOWS\system32\ if you installed the vendors drivers to your VM or friends computer.

---

### Post by shahan on 2010-10-29
[http://www.somewhereinblog.com](http://www.somewhereinblog.com) doesn't load the web version in Maverick Meerkat
In Maverick this site loads it Mobile version. But other version works good.

---

### Post by gushy on 2010-10-29
> **coldraven said:**
> With the64bit version the Ubuntu Software centre has a bug.
After entering your password and pressing "Authenticate" the text entry box vanishes and leaves a window with just "Authenticate". 
Clicking on this does nothing, install only starts if you close the box.
See the screenshots.

Update: As of 28th. October 2010 this seems to be fixed.
I'm seeing this issue, it seems to affect anything using that authenticate window - network manager, update manager, etc.

---

### Post by craigsn on 2010-10-31
I'm still having the problem. And I'm current on the updates. 64bit system.

---

### Post by kktm on 2010-10-31
**Ubuntu Thinkpad - Microphone**

at least on T400s you have to load the snd-hda-intel module with the option "thinkpad" to get the microphone working

Fix:

```
echo  options snd-hda-intel model=\"thinkpad\" | sudo tee -a /etc/modprobe.d/alsa-intel.conf
```

Taken from [Thinkwiki - Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400s]("http://www.thinkwiki.org/wiki/Install_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T400s#What_doesn.27t_work_out_of_the_box.3F")
(Don't get confused about the Karmic Koala, this info there is about Maverick.

---

### Post by ardunarda on 2010-11-01
compiz 0.9 does not work for amd64 version

---

### Post by fleamour on 2010-11-04
> **NightwishFan said:**
> Bug Report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
```
load-module module-udev-detect
```

It should look like this:
```
load-module module-udev-detect tsched=0
```

Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

I can only find following:

```
### Automatically load driver modules depending on the hardware available
.ifexists module-udev-detect.so
load-module module-udev-detect
.else
```

---

### Post by FBKK on 2010-11-17
> **coldraven said:**
> With the64bit version the Ubuntu Software centre has a bug.
After entering your password and pressing "Authenticate" the text entry box vanishes and leaves a window with just "Authenticate". 
Clicking on this does nothing, install only starts if you close the box.
See the screenshots.

Update: As of 28th. October 2010 this seems to be fixed.

How was this fixed any additional information would be useful, as I am experiencing this with a fully updated version of Meerkat.

Thank you!

---

### Post by daas88 on 2010-11-21
> **James78 said:**
> I have screen tearing and I'm using onboard Intel. :(

Anyways, just like in 10.04, Plymouth still isn't showing on system startup (due to graphics not being initialized quickly enough). The 10.04 fix for this works just the same, which was...
```
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash

update-initramfs -u
```

That doesn't work for me, all I get at startup is the text theme, but it does work fine when shutting down the system.
I have an nvidia card with its privative drivers.

---

### Post by sky pilot on 2010-11-22
> **NightwishFan said:**
> Bug Report: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/621430?comments=all)

Workaround for glitchy (crackling, skipping) audio is to open:
/etc/pulse/default.pa

Find the line that looks like this and add "tsched=0".
```
load-module module-udev-detect
```

It should look like this:
```
load-module module-udev-detect tsched=0
```

Save and reboot (or just log out).


Note this will not fix a problem with that specific chipset in the bug report with a muted speaker/headphone. I have no idea where to go with that one. Lidex and I have been trying to figure it out.

Thank You so much! This fixed the sound bug in my Linux Mint 10 Julia, 32 bit. Awesome!

---

### Post by pessimism on 2010-11-30
VirtualPC needs the following two boot options added when you boot off the CD (press F6) 
vga=791 noreplace-paravirt

The OS does not detect the VirtualPC environment.

After installation a number of fixes are needed to make X work properly.  I am making a howto for this.

---

### Post by SnoopNL on 2010-12-11
If installation fails with a distorted screen on systems with a Nvidia graphics card, please do the following:
Start installation with the safe driver from the F6 menu.

After the installation completes, start the system with the ubuntu recovery and start with the safe graphics drivers.

After this ubuntu will allow you to install the nvidia drivers.
After that everything is good to use.

---

### Post by AngelDE98 on 2010-12-22
**FN Keys Brightness not working properly ( Brightness is always same )**

Problem : The FN Brightness Keys are being found and Ubuntu shows its popup but nothing changes . 

Solution : There are many ways but just do : 
```
sudo gedit /etc/default/grub
``` 

Find GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" and change it to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=" 

At end just do ```
sudo update-grub
``` and reboot . I am looking for fixing the ± symbol bug and swap FN + LEFT and FN + RIGHT on some laptops .

---

### Post by xfearxnxloathing on 2011-01-12
selecting the proper nvidia driver and rebooting does not fix enable desktop effects setting. neither driver of the two listed when selected and rebooted work at all to change this setting.

---

### Post by makakut on 2011-01-12
> **sendblink23 said:**
> No clue if I should post this here.. but it could help new people using Ubuntu 10.10 or users who are having this issue using this driver ATI/Nvidia... System > Administration> Additional Drivers

If you have V-Sync issues(screen tearing) on **ATI** cards - using the driver from - System > Administration > Additional Drivers

Activate/Install the driver & reboot

***Single cards users:**
**1.** 
First make sure you have, CCSM (System > Preferences > CompizConfig Settings Manager): go here if you don't have it to enable it - [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695) 

**2.**
Go to System > Preferences > CompizConfig Settings Manager > General Options > Display Settings >
Texture Filter - Best
Detect Refresh Rate - Un-Checked
Refresh Rate - set it according to your monitor, for my monitor its 60
Detect Outputs - Checked
Sync To VBlank - Checked

Click Back & close CCSM

**3.**
Go to System > Preferences > ATI Catalyst Control Center
3D > More Settings >
Wait for vertical refresh - set it to Quality (Always On)
Click OK

Now restart the computer and enjoy no more vsync issue/screen tearing



Thanks. This works for me great but only till I reboot the computer. After reboot settings are saved but tearing comes back again. To resolve this issue i have to open ATI CCC every time and turn off "Wait for Vertical Refress" next turn on, click APPLY and i have no tearing.

Why settings aren't saved in hardware.

lisio@nv:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 4.0.10237 Compatibility Profile Context

Special options in xorg.conf file like this:

Option        "TexturedVideoSync" "on"
Option        "Capabilities" "0x00000800"

doesn't help. 

Is this a bug in ATI Drivers? or my hardware ASUS ATI HD5770 is not supported for linux

---

### Post by jaklec on 2011-01-13
I suddenly out of nowhere got problems with the Nvidia driver which caused X to freeze with hard reboot as the only option. Upgrading to the latest driver through the x-swat repositories didn't solve the problem. But I finally found a solution that works for me.

Solution:
In "System/Administraion/NVIDIA X Server Settings" go to "X Server Display Configuration" and click "Save to X Configuration File". You will be prompted with a password dialog - type your password. A new xorg.conf file will be created in /etc/X11. Now reboot!

I'm using the default Nvidia settings and this solved the freezing problems for me.

I made a rather massive post describing the problem and all my efforts to fix it in the Nvidia forums: [http://www.nvnews.net/vbulletin/showthread.php?t=158729](http://www.nvnews.net/vbulletin/showthread.php?t=158729)

---

### Post by Fluffgar on 2011-01-19
I'm not sure what to do with this (gwibber-service-bugreport.txt attached).

---

### Post by bilallucky on 2011-02-01
If you upgrade to Virtualbox 3.2.10 the guest additions are working in both Ubuntu 10.10 and Fedora 14.

---

### Post by jlknapp505 on 2011-02-23
I'm trying to get a driver for a Netgear N150 WNA dongle; downloading the software from Netgear won't work.  When trying to use the ndiswrapper command I was directed to load the program, and when I typed in the prompt, Terminal asked for my password, but won't allow me to type anything.  I've now experienced this problem twice, asking for password in Terminal but refusing to allow the password to be entered.  
No solution so far.

---

### Post by imblack on 2011-03-01
1. Samsung 21' Sync Master 2033 often fails in Screensaver mode and when you come back the display is distorted.

2. When I install updates and it asks for password I give it but the dialog wont close I manually need to press escape. :S

---

### Post by ClientAlive on 2011-03-21
Hi!
 
You know, I don't know what to do. I really wanted to run and even install linux on my machine but have had all kinds of problems even running the live usb. I posted last night about this (under absolute newbie > installation and  . . .)  and have gotten no replies - so here I sit. I've been dealing with this for over three days (today is day four). I look at the recent/ new posts and see people getting responsed sometimes within minutes of posting. Mines been up for hours and no help.
 
What do I do?? Just give up on having linux??
 
Please help!
 
Please help?
 
Pretty please?

---

### Post by nannirk on 2011-04-15
> **Refalm said:**
> If X is still not starting, add this to */etc/X11/xorg.conf*
```
Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
```[B]Only do this if you have issues with the nvidia driver,
or if you really want that 2 fps extra in CoD:MW2 while playing on your 1080p 30" LCD monitor.[/B]

Well, I am having trouble.
But I don't know how I'm supposed to edit xorg.conf  without a GUI..
Please tell me what I need to do. This is so annoying not being able to use my laptop.
I'll link to the thread explaining my problems **[here]("http://ubuntuforums.org/showthread.php?p=10680085").**

---

### Post by spirit.986 on 2011-04-15
Ok here's one bug found into my PC [ASUS M51Va]("http://www.drivers-xp.com/asus/asus-m51va-windows-xp-drivers-download/")

Sometimes after i close the Indicator Applet the Panels and the windows revert into some old grey colored skin (battleship gray)..
I can't fix it in the current session.. have to restart the PC.

---

