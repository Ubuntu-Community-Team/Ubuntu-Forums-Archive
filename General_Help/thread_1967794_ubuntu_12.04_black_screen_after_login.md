---
title: "ubuntu 12.04 black screen after login"
date: 2012-04-28
forum: General Help
---

### Post by HolyRoses on 2012-04-28
Hi,

I installed ubuntu 12.04 lts on a lenovo desktop.  We are presented with the login screen and everything looks fine.  We login and the desktop goes black.  All we have is a cursor.

When the monitor when into suspend mode we were presented with a lockout screen/login.  Entered password and then saw a message "System program problem detected screen showed after." afterwards.  Cannot click cancel or send report button.

here is the lspci information

elizabeth@elizabeth-pc:~$ lspci
00:00.0 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: NVIDIA Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: NVIDIA Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: NVIDIA Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: NVIDIA Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: NVIDIA Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: NVIDIA Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: NVIDIA Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: NVIDIA Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: NVIDIA Corporation C51G [GeForce 6100] (rev a2)
00:09.0 RAM memory: NVIDIA Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: NVIDIA Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: NVIDIA Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: NVIDIA Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB controller: NVIDIA Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: NVIDIA Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: NVIDIA Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: NVIDIA Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: NVIDIA Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
03:08.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)

I also tried to update nvidia and that didn't help either.

sudo apt-get install nvidia-current-updates
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings-updates
The following NEW packages will be installed:
  nvidia-current-updates nvidia-settings-updates
0 upgraded, 2 newly installed, 0 to remove and 12 not upgraded.
Need to get 34.4 MB of archives.
After this operation, 100 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted nvidia-current-updates i386 295.40-0ubuntu1 [33.4 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/restricted nvidia-settings-updates i386 295.33-0ubuntu1 [925 kB]
Fetched 34.4 MB in 1min 35s (360 kB/s)
Selecting previously unselected package nvidia-current-updates.
(Reading database ... 142421 files and directories currently installed.)
Unpacking nvidia-current-updates (from .../nvidia-current-updates_295.40-0ubuntu1_i386.deb) ...
Selecting previously unselected package nvidia-settings-updates.
Unpacking nvidia-settings-updates (from .../nvidia-settings-updates_295.33-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current-updates (295.40-0ubuntu1) ...
INFO:Enable nvidia-current-updates
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match LENOVO with Dell Inc.
DEBUG:Quirk doesn't match
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match ThinkCentre XXXX with ThinkPad T420s
DEBUG:Quirk doesn't match
Loading new nvidia-current-updates-295.40 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-23-generic-pae
Building for architecture i686
Building initial module for 3.2.0-23-generic-pae
Done.

nvidia_current_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-23-generic-pae/updates/dkms/

depmod.......

DKMS: install completed.
Setting up nvidia-settings-updates (295.33-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-settings-updates/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...



Looking for help how to get the desktop :)  Installation of course worked fine and just running via CD is fine.

also via dmesg I see this error:

[   96.826209] compiz[1681]: segfault at a79bf800 ip b562f4c0 sp bfe47960 error 4 in libnvidia-glcore.so.295.40[b43de000+1bc0000]

---

### Post by HolyRoses on 2012-04-28
was able to login via selecting 2D at the login screen.  There was still a compiz crash.

anyone know how to disable this compiz or make the default login 2d? at least until a fix can be found?

---

### Post by ventrical on 2012-04-28
> **HolyRoses said:**
> was able to login via selecting 2D at the login screen.  There was still a compiz crash.

anyone know how to disable this compiz or make the default login 2d? at least until a fix can be found?


Do you have Precise Stable or are you running from an earlier release?

Edit: btw .. did you install 64bit or 32 bit version?

---

### Post by HolyRoses on 2012-04-28
32 bit. I downloaded the ubuntu yesterday.  So I assume its the latest revision.

---

### Post by ventrical on 2012-04-28
I am just curious as to whether 'Additional Drivers' reports anything to you? Could you try to run that please?

---

### Post by HolyRoses on 2012-04-28
just the nvidia update I am the (post-release updates) (version current-updates).

---

### Post by ventrical on 2012-04-28
> **HolyRoses said:**
> Hi,

also via dmesg I see this error:

[   96.826209] compiz[1681]: segfault at a79bf800 ip b562f4c0 sp bfe47960 error 4 in libnvidia-glcore.so.295.40[b43de000+1bc0000]

  It may be more simpler than this but at one time I had to un-install and re-install compiz. I'm not sure it will help. 

 My assumption is that there may be  a BIOS setting that needs to be adjusted, but I am also assuming that you perhaps have had Ubutnu running really well with a earlier version ?

---

### Post by HolyRoses on 2012-04-28
never installed ubuntu on this desktop.  its an older machine.  came with vista.  also had issues with graphics trying to install windows 7.

on a good note it seems to default to 2d on your login if you previously selected that.

---

### Post by ventrical on 2012-04-28
> **HolyRoses said:**
> never installed ubuntu on this desktop.  its an older machine.  came with vista.  also had issues with graphics trying to install windows 7.


Try from the terminal:

sudo apt-get purge nvidia*  

 then reboot

after reboot get into GRUB by holding down your <Shift> key and choose <recovery-mode>. Let it go through it's cycle and then select <resume> . This may give you a standard generic driver that will give you a desktop at least.

Edit:

If this does not work then try to re-install the nvidia drivers.

---

### Post by ventrical on 2012-04-28
Also here is somthing I found about your Nvidia card.

From Cariboo907

"March 30th, 2011, 10:57 PM
The  6100-6150 chipsets have always been strange as far as I'm concerned,  I've had 3 motherboards with them, and all of them needed either  safe-mode or nomodeset enabled before I could boot to a desktop with the  Live CD this is going back to 7.04. I haven't tried since Lucid,  because I bought add-in cards specifically a 8400GS, a 9400GT and a  GT210 so that I didn't have to deal with the weirdness any more.

You shouldn't have to, but if you are having problems, install nvidia-current, then run nvidia-xconfig to see if that helps.

I did a test install this afternoon on a system with a GT6600,  Additional drivers gave me the choice of either nvidia-current or the  experimental 3D open source driver, I chose the experimental drivers,  and Unity started right up with having to do a reboot after the driver  were installed."

---

### Post by bhoopal on 2012-04-28
sudo sed -i 's/user-session=ubuntu/user-session=ubuntu-2d/g' /etc/lightdm/lightdm.conf

---

### Post by HolyRoses on 2012-04-28
nvidia current is what is installed by default.

i can get a desktop but i have to select 2D at the login screen by pressing the gear like icon and selecting 2d.

by purging nivida* I can login via 3d mode I guess (just selecting ubuntu and not ubuntu 2d). graphics are only 640x480 though.

---

### Post by HolyRoses on 2012-04-28
> **bhoopal said:**
> sudo sed -i 's/user-session=ubuntu/user-session=ubuntu-2d/g' /etc/lightdm/lightdm.conf

this will remove the 3d option I assume?

---

### Post by ventrical on 2012-04-28
> **HolyRoses said:**
> nvidia current is what is installed by default.

i can get a desktop but i have to select 2D at the login screen by pressing the gear like icon and selecting 2d.

by purging nivida* I can login via 3d mode I guess (just selecting ubuntu and not ubuntu 2d). graphics are only 640x480 though.

Does >settings>display  give you any other alternatives?  (click the wheel on top right  screen, choose displays, then check the resolution options.

---

### Post by HolyRoses on 2012-04-28
no, only 640x480.  if i click the proprietary drivers presents a list of nvidia drivers again.  though now I can't see the versions because the screen is so small.  I selected the bottom one.

nvidia current is reinstalled.  still same problems as before, can only login with 2d.

---

### Post by ventrical on 2012-04-28
Unfortunately a lot of nvidia cards were obsoleted with the most recent upgrade to Precise with Unity 3D. I have an older nVidia card also and it will only render Unity 2D. I'll take a look around .. and of course, stay tuned to this forum as I am sure others will drop in :)

---

### Post by lukibeni on 2012-04-29
This is a bug, and it's already reported on Launchpad. The only thing we can do is subscribing to the bug ([https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/982485)) and wait for the fix.
Although there is a workaround, just pick up this ppa ([https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)) and downgrade the nvidia-current package to 295.33 It works for me :-)
Good luck!

---

### Post by HolyRoses on 2012-04-29
@lukibeni  wish you would provided me the commands... I am a redhat person...  these darn apt commands drove me nuts.  anyhow I thank you.

I did the following:

apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'

apt-get update

apt-get purge nvidia*
removed: nvidia-common* nvidia-current* nvidia-settings* ubuntu-desktop*

apt-cache showpkg nvidia-current
apt-cache showpkg nvidia-settings
apt-get install nvidia-current='295.33-0ubuntu1~precise~xup1' nvidia-settings='295.33-0ubuntu1~precise~xup1'

echo "nvidia-current hold" | sudo dpkg --set-selections
echo "nvidia-settings hold" | sudo dpkg --set-selections

It still prompts that there is an update available but it is blocked.

-HR

---

### Post by lukibeni on 2012-04-29
@HolyRoses

Firstly remove all the installed propietary driver from the Additional Drivers. Then type these commands into the terminal:
[LIST=1]
[*]sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
[*]sudo apt-get update
[*]sudo apt-get install nvidia-current=295.33-0ubuntu1~precise~xup1
[/LIST]
Finally just reboot, and the unity3D will work (or at least I'm hoping it :-))
Of course you mustn't upgrade the nvidia-current to the 295.40 version, because it brokes everything.

P.S.: I hope you didn't purge the whole ubuntu-desktop, because I see this in your comment...

---

### Post by HolyRoses on 2012-04-29
that's basically what I did, the exact commands I typed though are in post.

It said it removed desktop, but it didn't or maybe it reinstalled it I dunno.  Everything is working fine now.

---

### Post by bogan on 2012-04-29
Hi!,** HolyRoses**, as you found, you do not need to alter compiz to set the default display, it is set to what ever you last selected at login.

Also, if you are running 12.04 LTS release the icon in the top left of the log-in window should not be a gear, but either an Ubuntu logo, or a Gnome logo { the footie thingme} depending on what you last logged into.

The segfaults are a symptom of the April14th bug in the 295.40 nvidia driver, and also in the ubuntu nvidia-current, also 295.40: this gives troubles especially with 7xxx &8xxx series nvidia video cards; varying from failure to boot, freezes and hang-ups to very slow running, but only in 2D or low res.

For some 295.33 will run OK, though it may need the 'nomodset' option, otherwise 290.20 may work, or failing that 290.10.

Try```
 sudo nvidia-installer --latest
``` from an ordinary terminal, This will just tell you the version installed and the latest recommended version, which at the moment is 295.33. [ This despite 295.40 being available from the nvidia/downloads site]

The simple way to get the right version is as follows:
The GUI & Xserver must not be running:```
 sudo nvidia-installer -f 
```from a text terminal [ Ctrl+Alt+F1 or F2] tty.

This will uninstall the existing driver and install 295.33. Then reboot.

**First** however you **MUST **check [COLOR=Red]the Linux kernal & headers are correct[/COLOR], as your previous Posts show nvidia being installed for the 3.2.0-23 version, which is  Beta, and the LTS release is 3.2.0-24 dated April 25.[ Which, if you are running 3.2.0-24, will cause horrendous problems.]```
uname -a
``` will tell you what is installed.

Post back how it goes and we can take it from there.

Chao!, **bogan**.

---

### Post by K4NEB on 2012-04-29
log in in 2D disable NVIDIA restart computer log back in to normal unity, and it will work

---

### Post by bogan on 2012-04-29
Hi!,** HolyRoses**, as you found, you do not need to alter compiz to set the default display, it is set to what ever you last selected at login.

Also, if you are running 12.04 LTS release the icon in the top left of the log-in window should not be a gear, but either an Ubuntu logo, or a Gnome logo { the footie thingme} depending on what you last logged into.

The segfaults are a symptom of the April14th bug in the 295.40 nvidia driver, and also in the ubuntu nvidia-current, also 295.40: this gives troubles especially with 7xxx &8xxx series nvidia video cards; varying from failure to boot, freezes and hang-ups to very slow running, but only in 2D or low res.

For some 295.33 will run OK, though it may need the 'nomodset' option, otherwise 290.20 may work, or failing that 290.10.

Try```
 sudo nvidia-installer --latest
``` from an ordinary terminal, This will just tell you the version installed and the latest recommended version, which at the moment is 295.33. [ This despite 295.40 being available from the nvidia/downloads site]

The simple way to get the right version is as follows:
The GUI & Xserver must not be running:```
 sudo nvidia-installer -f 
```from a text terminal [ Ctrl+Alt+F1 or F2] tty.

This will uninstall the existing driver and install 295.33. Then reboot.

**First** however you **MUST **check [COLOR=Red]the Linux kernal & headers are correct[/COLOR], as your previous Posts show nvidia being installed for the 3.2.0-23 version, which is  Beta, and the LTS release is 3.2.0-24 dated April 25.[ Whichif you are running 3.2.0-24 will cause horrendous problems.]```
uname -a
``` will tell you what is installed.

Post back how it goes and we can take it from there.

Chao!, **bogan**.

---

### Post by HolyRoses on 2012-04-29
Hi bogan,

Your nvidia commands would of been handy.  The desktop has since left my house and I don't have immediate access to it anymore.  I was trying to help a friend get off "windows platform" as it was constantly virused.  I consider the problem resolved now.  Seems everything is in order.

My original post was me trying different things.  I since re-installed from that post and ran the following (which is mentioned in subsequent posts):

apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'
apt-get update

apt-get purge nvidia*

apt-cache showpkg nvidia-current
apt-cache showpkg nvidia-settings
apt-get install nvidia-current='295.33-0ubuntu1~precise~xup1' nvidia-settings='295.33-0ubuntu1~precise~xup1'

echo "nvidia-current hold" | sudo dpkg --set-selections
echo "nvidia-settings hold" | sudo dpkg --set-selections


If I had to do it again I would likely use your method.  It was 12.04 LTS and the gear or button I was referring to was the logo that is to the right of your login name that you can click.  It presents you with a menu of "ubuntu and ubuntu 2d".  I was going from memory when I wrote that.

@K4NEB that is not a good solution.  Leaves one without a proper video driver.

---

### Post by bogan on 2012-04-29
Hi!, **HolyRoses**,

Glad you got it fixed.

You Posted:>  It was 12.04 LTS and the gear or button I was referring to was the  logo that is to the right of your login name that you can click.  It  presents you with a menu of "ubuntu and ubuntu 2d"Yeah! that is the one I meant too. 12.04 Beta still had the gear icon.

The LTS release 3.2.0-24 has a Ubuntu logo instead, which changes to a Gnome logo if logged in to Gnome or Gnome-Classic .

Chao!,** bogan**.

---

### Post by brx75 on 2012-05-02
I've a similar problem (black screen after lightDM login) with Ubuntu 12.04 on a Dell Latitude E6410 with Intel Graphics (i915 drivers).
Anyone heard of this and could point me to a relevant thread/forum?

Thanks.

---

### Post by bogan on 2012-05-02
Hi!, **brx75**,

You Posted:>  Anyone heard of this and could point me to a relevant thread/forum?There are any number of threads dealing with variations on this problem in Desktop Environments or Installations & Upgrades: have a look at this one:
 [http://ubuntuforums.org/showthread.php?t=1967945](http://ubuntuforums.org/showthread.php?t=1967945)

A lot depends on just when the black screen occurs, whether 'Crtl+Alt+F1', F2 or F4 give a tty log-in prompt, and on what you had done before it first occurred; for instance, had you just upgraded or installed?, or had you altered the background image?

The video driver you are using for the Intel graphics, may also be significant.

You would do best to open your own thread with such details, if you cannot find one that exactly matches your problem.

Chao!,** bogan**.

---

### Post by brx75 on 2012-05-02
Thanks Bogan. I'm reading on the thread you suggested.

---

### Post by bogan on 2012-05-04
Hi!,** All,**  There is a new driver, 295.49 available from nvidia downloads
 [http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-295.49-driver-uk.html)

 Noon Friday May 4th; ```
nvidia-installer --latest 
``` now  returns: v295.49 and     ```
nvidia-installer -f 
``` will install  295.49 after un-installing the previous version.

 NVNews says of version295.49:> **Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**
Chao!, **bogan**

---

### Post by wribeiro on 2012-05-04
What we can expect of Pangolin? That is fast, safe and simple, but most important of all, that work!
So, how can such a huge bug, that affects a enormous amount of users, can occur in a LTS version?
I'm very disappointed.

---

### Post by norton.miller on 2012-05-05
> **HolyRoses said:**
> Hi bogan,

Your nvidia commands would of been handy.  The desktop has since left my house and I don't have immediate access to it anymore.  I was trying to help a friend get off "windows platform" as it was constantly virused.  I consider the problem resolved now.  Seems everything is in order.

My original post was me trying different things.  I since re-installed from that post and ran the following (which is mentioned in subsequent posts):

apt-add-repository 'deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) precise main'
apt-get update

apt-get purge nvidia*

apt-cache showpkg nvidia-current
apt-cache showpkg nvidia-settings
apt-get install nvidia-current='295.33-0ubuntu1~precise~xup1' nvidia-settings='295.33-0ubuntu1~precise~xup1'

echo "nvidia-current hold" | sudo dpkg --set-selections
echo "nvidia-settings hold" | sudo dpkg --set-selections


If I had to do it again I would likely use your method.  It was 12.04 LTS and the gear or button I was referring to was the logo that is to the right of your login name that you can click.  It presents you with a menu of "ubuntu and ubuntu 2d".  I was going from memory when I wrote that.

@K4NEB that is not a good solution.  Leaves one without a proper video driver.


I had installed 295.49 (or so I thought) using nvidia-installer -f but my machine would only boot to console (tty1 - tty6). I had no x-server/gui running on tty7. I followed your instructions and I now have Unity 2D running. While carrying out the installation of 295.33 I noticed that my machine reported that I still had 295.40 nvidia-settings installed even though I had installed 295.49.

Maybe this was the cause of my initial problem (no gui on tty7).

So, thanks for your machine-saving 295.33 installation instructions. :)

Edit: As soon as I had Unity 2D up & running, Update Manager reported that there were updates - the latest nvidia drivers (295.49). So I accepted the updates & installed these drivers. After a reboot I tried to use Unity 3D with no success. The new 295.49 drivers have not worked for me.

---

### Post by bogan on 2012-05-17
Hi!,** All**.

[COLOR=Blue]There is a new nvidia driver version 295.53 available [/COLOR]from nvidia downloads.  This Link is for the 32 bit version, check you get the correct one.
[http://www.nvidia.co.uk/object/linux...driver-uk.html]("http://www.nvidia.co.uk/object/linux-display-ia32-295.53-driver-uk.html")

[COLOR=RoyalBlue]**Edit: Updated Thursday May 17th; **[/COLOR]     

      	Code:
 	nvidia-installer --latest 
 now returns: v295.53 and the currently installed version, without altering anything.
     

      	Code:
 	nvidia-installer -f 
 will install 295.53 after un-installing the previous version.

NVNews says of version 295.53:
QUOTE:
**Please note:** This [NVIDIA]("http://www.nvidia.com/") Linux graphics driver release supports **GeForce 6xxx and newer [NVIDIA]("http://www.nvidia.com/") GPUs**,
 [GeForce4]("http://viglink.pgpartner.com/rd.php?r=10313&m=878281881&q=o&priceret=87.73&pg=%7E%7E3&k=2b6229593608c3c1fb499d0ca9880634&source=feed&url=http%3A%2F%2Fmicropartsusa%2Ecom%2F31p6953%2Dibm%2Dnvidia%2Dgeforce4%2Dmx440%2D64mb%2Dagp8x%2Datx%2Dgraphics%2Dcard%2Dw%2Do%2Dcable%2Dnew%2Dbulk%2Din%2Dstock%2Ehtml&st=feed&mt=%7E%7E%7E%7E%7E%7E%7E%7En%7E%7E%7E") and older GPUs are supported through the **96.43.xx** and **71.86.xx** [NVIDIA]("http://www.nvidia.com/") legacy graphics drivers.
 GeForce FX GPUs are supported through the **173.14.xx** NVIDIA legacy graphics drivers.

[B]
bogan.[/B]

---

### Post by muckblit on 2013-01-02
"nvidia-installer not found" with ubuntu raring, or after adding that ppa.

Microsoft must have taken the nvidia-installer out so that we can no longer achieve our revolutionary goals on a worldwide base of computers that will no longer run Microsoft...now not Ubuntu either. Ubuntu raring iso won't load either, thanks to the same concerted effort not to run on anything Windows doesn't want.

Different package name: [nvidia-graphics-drivers-updates]("https://launchpad.net/ubuntu/raring/+package/nvidia-current-updates")

Why would the latest iso not have this? Why are we not hungry anymore?

---

