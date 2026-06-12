---
title: "Login to shell/commsnd prompt Xserver wont start nvidia kernel module prob"
date: 2012-08-21
forum: General Help
---

### Post by typos1 on 2012-08-21
[INDENT]Installed some updates went out for few hours and pc boots to command line. So I logged in and entered "startx" then got something saying there was a mismatch between nvidia modules ( see photo). I ve tried plugging the dvi lead into the pcs own dvi port rather than the one on the graphics card but I get no output at all then. I noticed one of the updates was for nvidia do I m assuming that thats   whats caused it. Any ideas as cant use pc at all, posted this from my galaxy S2.
[/INDENT]

---

### Post by typos1 on 2012-08-21
Anyone ? PC totally unusable and really need stuff on it

---

### Post by Yellow Orange on 2012-08-21
Try to boot with some previous kernel or recompile proprietary nvidia driver or reconfigure X-server for using open source nvidia driver or vesa.

---

### Post by typos1 on 2012-08-21
I gathered I d need to reconfigure xserver and or reconfigure nvidia drivers or something but I dont know how to do it hence this post.

---

### Post by typos1 on 2012-08-22
Right, logged in with a different kernel, anyone know how I can sort the problem though ?

---

### Post by efflandt on 2012-08-22
Where did you get 295.49 nvidia driver from?

The nvidia-current version is 295.40 and if you added x-swat repository, that is 304.37.  So it looks like you added x-swat, but also added 295.49 manually that the Ubuntu package manager is unaware of.

So after any kernel update, you either need to redo whatever you did to manually add 295.49, or reinstall Ubuntu and stick with Ubuntu or Debian packages, so updates would be automatic.

---

### Post by bogan on 2012-08-22
Hi!, **typos1**,

Please Post, from the 12.04 tty log-in: ```
lspci -nnk | grep  -iA3 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
sudo nvidia-installer --latest
```If you have a version of the nvidia.com driver installed, the third command will return its version number. If not then both the third and  fourth will show' no such...' or 'not found...'.

If you have one installed, then the fourth command will show the installed and latest available version numbers but will not alter anything - but it will confirm if your Internet connection is working, and open the path to correct things without a re-install of ubuntu, if that** is **what you want.

*Edit2: Numeric references to commands updated after adding lspci cmd.*

Chao!,** bogan**.

---

### Post by typos1 on 2012-08-22
Efflant, I didnt "get" any driver from anywhere, all I did was install approx 62 updates on Tuesday (21st). I always go through updates and see what they are when I install them and I m pretty certain there was an nVidia one in there somewhere. 

I dont know what x-swat is, all I ve ever done is install the post release updates from the additional drivers section and theyve been running fine for nearly 2 years, including each kernel update - I ve not had this problem before.

Bogan, I shall post that output a bit later . . .

Thanks

---

### Post by wheezewiz on 2012-08-29
This happened to me after I ran Update Manager and restarted my computer. After playing with for a while, it told me that updates were available. I did an apt-get update and install from the command prompt and now all is good (the Nvidia driver was one of those that updated). Apparently, Update Manager got confused and didn't get all the updates.

---

### Post by typos1 on 2012-09-03
There were more nVidia updates to install yesterday, hoped would fix the problem. 

Not at all, now its worse. I had been using the previous kernel version before, now that boots to the tty and I have to use the one before that. Also, despite the DVI lead being plugged into my graphics card, NOT the onboard DVI port, "system" now says I m using the onboard graphics and I ve been downgraded to Unity 2D, plus video is slow and jerky. And now the latest kernel doesnt work at all, it just boots to a blank screen

I ve tried Bogan's suggestions and I cant do the first command because I cant figure how to get the line between nnk and grep. So I tried the 4th command and it says "unknown command-nvidia installer" I tried taking out the "-" but still got the same.

All very strange,  anybody got any ideas ?

---

### Post by Crossbow on 2012-09-03
Hey, I'm having the same problem, I think. I installed updates to NVIDIA, restarted, and now the GUI is basically gone. I'm on my friend's computer right now. I did get-apt update and got a message that I should run get-apt update to correct the errors. The errors seem to be "duplicate source."

> lspci -nnk | grep  -iA3 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
sudo nvidia-installer --latest

First, third and fourth said "no such command."

Second said 

Installed: 304.43...
candidate 304.43...

295 [http://us.archive](http://us.archive). (blah blah)... restricted i386 package

---

### Post by bogan on 2012-09-03
Hi!, **typos1**,

The 'bar', '|', in the lspci command is the 'pipe'symbol directing the output to a given destination.

On an UK keyboard it is the shifted symbol immediately to the right of the left 'shift' key.

On an USA keyboard, I believe it is the shifted key above the right shift key.

The fact that nvidia-installer shows as 'unknown command' means you do not have an nvidia.com downloaded driver installed. So you can not use that method.

You should be able to run the first two commands, & Post the output. 

Chao!,** bogan**.

---

### Post by Crossbow on 2012-09-03
Actually I know what the problem is, I just don't know the technical terms or how to fix it. 

I was having trouble running WoW in wine, and the information on the sticky post said it was not a wine problem but a driver problem and that upgrading to the latest Ubuntu should fix it - but I had just upgraded to 12.04. So I went to "additional drivers" and saw a post-release Nvidia update, so I installed that, was prompted to reboot, and found myself where I am now: No GUI.

I am getting an error about an API mismatch: Nvidia module is 304.43 but driver is 295.49. It doesn't say how to fix that, though.

---

### Post by Crossbow on 2012-09-03
FIXED!!!!!

From: [http://ubuntuforums.org/showpost.php?p=12203435&postcount=16](http://ubuntuforums.org/showpost.php?p=12203435&postcount=16)

> sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current

Then just ctrl-alt-delete to reboot.

---

### Post by Crossbow on 2012-09-03
@#$@$%#@#$%

Not fixed. I have GUI but it still keeps throwing me back to the login screen. EXCEPT, I can log in as guest user just fine. I know someone else around here was having the same problem...

---

### Post by typos1 on 2012-09-03
Hello bogan.  Yes, I am getting the same mis match error as you crossbow.

I also DO very deffinately have nVidia drivers installed, I installed them myself ! Plus I just tried the commands that Crossbow suggested and "purge nVidia-*" purged nVidia (freed 300 odd mb of disc space) and surely it couldnt purge nVidia if there were no nVidia drivers installed ?

Unless of course the update un-installed them. 

Either way, a few updates have caused some humungus errors lately for nVidia users and no one seems to be doing anything about it.

I know WHERE the line or "pipe" symbol is bogan, its how to access it that is the problem, neither, shift, caps lock, super key or control allows me to access it. I can only access " ` " or " ¬ " on that key, the line/pipe  never appears. The " ` " , " ¬ " and the pipe/bar are to the left of the number one, above the letters on my keyboard.


Here is what I did in the terminal, thought it might be useful, if not I ll edit it out.

{typos1@typos1-HP-dx5150-SFF:~$ sudo apt-get purge nvidia-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-vdpau-driver' for regex 'nvidia-*'
Note, selecting 'nvidia-185-kernel-source' for regex 'nvidia-*'
Note, selecting 'nvidia-96-kernel-source' for regex 'nvidia-*'
Note, selecting 'nvidia-173-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-kernel-common' for regex 'nvidia-*'
Note, selecting 'nvidia-common' for regex 'nvidia-*'
Note, selecting 'nvidia-173' for regex 'nvidia-*'
Note, selecting 'nvidia-cg-toolkit' for regex 'nvidia-*'
Note, selecting 'nvidia-180-libvdpau' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-96-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-current' for regex 'nvidia-*'
Note, selecting 'nvidia-185-libvdpau-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-96' for regex 'nvidia-*'
Note, selecting 'nvidia-96-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-current-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-vdpau-driver-ia32' for regex 'nvidia-*'
Note, selecting 'nvidia-173-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-va-driver' for regex 'nvidia-*'
Note, selecting 'nvidia-185-libvdpau' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau' for regex 'nvidia-*'
Note, selecting 'nvidia-current-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-173-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-tegra' for regex 'nvidia-*'
Note, selecting 'boinc-nvidia-cuda' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-185-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-opencl-icd' for regex 'nvidia-*'
Note, selecting 'nvidia-173-kernel-source' for regex 'nvidia-*'
Note, selecting 'libgl1-nvidia-alternatives' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-173' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-180' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-185' for regex 'nvidia-*'
Note, selecting 'nvidia-settings-updates' for regex 'nvidia-*'
Note, selecting 'nvidia-96-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-180-libvdpau-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-96-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-180-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-173-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-current-updates-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-96-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-cuda-toolkit' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau-ia32' for regex 'nvidia-*'
Note, selecting 'nvidia-libopencl1-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-180-kernel-source' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau1' for regex 'nvidia-*'
Note, selecting 'nvidia-libvdpau1-ia32' for regex 'nvidia-*'
Note, selecting 'nvidia-current-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-96' for regex 'nvidia-*'
Note, selecting 'nvidia-173-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-185-modaliases' for regex 'nvidia-*'
Note, selecting 'nvidia-glx' for regex 'nvidia-*'
Note, selecting 'libkwinactivenvidiahack4' for regex 'nvidia-*'
Note, selecting 'nvidia-glx-180-dev' for regex 'nvidia-*'
Note, selecting 'nvidia-settings' for regex 'nvidia-*'
Note, selecting 'nvidia-texture-tools' for regex 'nvidia-*'
Note, selecting 'libkwinnvidiahack4' for regex 'nvidia-*'
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Note, selecting 'vdpau-va-driver' instead of 'nvidia-va-driver'
Package nvidia-96 is not installed, so not removed
Package nvidia-96-dev is not installed, so not removed
Package nvidia-96-updates is not installed, so not removed
Package nvidia-96-updates-dev is not installed, so not removed
Package nvidia-cg-toolkit is not installed, so not removed
Package libkwinactivenvidiahack4 is not installed, so not removed
Package libkwinnvidiahack4 is not installed, so not removed
Package nvidia-173 is not installed, so not removed
Package nvidia-173-dev is not installed, so not removed
Package nvidia-173-updates is not installed, so not removed
Package nvidia-173-updates-dev is not installed, so not removed
Package nvidia-current-updates-dev is not installed, so not removed
Package boinc-nvidia-cuda is not installed, so not removed
Package nvidia-current-dev is not installed, so not removed
The following package was automatically installed and is no longer required:
  ladspa-sdk
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  nvidia-common* nvidia-current* nvidia-current-updates* nvidia-settings*
  nvidia-settings-updates* ubuntu-desktop*
0 upgraded, 0 newly installed, 6 to remove and 7 not upgraded.
After this operation, 392 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 270671 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing nvidia-common ...
Purging configuration files for nvidia-common ...
Removing nvidia-current ...
Removing all DKMS Modules
Done.
Purging configuration files for nvidia-current ...
Removing nvidia-current-updates ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Purging configuration files for nvidia-current-updates ...
update-initramfs: deferring update (trigger activated)
Removing nvidia-settings ...
Purging configuration files for nvidia-settings ...
Removing nvidia-settings-updates ...
Purging configuration files for nvidia-settings-updates ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
typos1@typos1-HP-dx5150-SFF:~$ sudo apt-get install nvidia-current 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  ladspa-sdk
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-settings
The following NEW packages will be installed
  nvidia-current nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/69.1 MB of archives.
After this operation, 206 MB of additional disk space will be used.
Do you want to continue [Y/n]? yy
Selecting previously unselected package nvidia-current.
(Reading database ... 270132 files and directories currently installed.)
Unpacking nvidia-current (from .../nvidia-current_304.43-0ubuntu1~precise~xup1_amd64.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_304.43-0ubuntu1~precise~xup1_amd64.deb) ...
Processing triggers for man-db ...
Setting up nvidia-current (304.43-0ubuntu1~precise~xup1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
Loading new nvidia-current-304.43 DKMS files...
First Installation: checking all kernels...
Building for 3.2.0-26-generic and 3.2.0-29-generic
Building for architecture x86_64
Building initial module for 3.2.0-26-generic
Done.

nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod.........

DKMS: install completed.
Building initial module for 3.2.0-29-generic
Done.

nvidia:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-29-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up nvidia-settings (304.43-0ubuntu1~precise~xup1) ...
update-alternatives: warning: alternative /usr/lib/nvidia-settings-updates/ld.so.conf (part of link group nvidia_settings_conf) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/nvidia_settings_conf is dangling, it will be updated with best choice.
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
typos1@typos1-HP-dx5150-SFF:~$ }

---

### Post by Crossbow on 2012-09-03
So can you log in now?

---

### Post by typos1 on 2012-09-03
Just about to restart ! . . . .

---

### Post by typos1 on 2012-09-03
Yes ! Thats sorted it !

How long did you wait on the login screen ? Mine took a few minutes to get past it, thought I was gonna have the same problem as you ? Any chance you didnt leave it long enough ?

---

### Post by Crossbow on 2012-09-03
I don't know. I can log in as a guest user with no problem, it's only when I try to log in as myself. No error message, it seems to accept my password, then goes black then back to the log in.

---

### Post by typos1 on 2012-09-03
Oh, sorry to get your hopes up.

:(

---

### Post by Crossbow on 2012-09-03
Unbelievable - I actually made it WORSE. I tried this:

[http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04](http://askubuntu.com/questions/139528/cant-log-in-to-ubuntu-12-04)

and now I can't even get to any log in screen, graphic OR textual. The only thing I can change now is the setup! 

Can anyone please help me???

ETA: Excuse my panic. I got a login screen back by recovery mode, which I didn't know I could do before the setup. However, I still can only log in as guest.

---

### Post by typos1 on 2012-09-04
Sorry, I cant help - its beyond my capabilities. 

But it does seem like it might be unrelated to nVidia drivers because you can login as a guest with them all working.

---

### Post by bogan on 2012-09-04
Hi!, **typos1** & **Crossbo**w,

I do not know if there is any point in trying further  explaining, but without the needed data it is not possible to make sensible suggestions, It is just grouping in the dark.

First: the command "lspci" is : 'ell-ess-pee-see-eye', a small 'L', not a big  'i' or a '1'. Please try that command again.

On my UK keyboard the Pipe/Bar is to the right of the left 'Shift' key, and the 'bar' on the '`'key, to the left of the '1', is shown as a divided bar:  Though when pressed as "Alt GR+' " it produces the same pipe/bar symbol: '|', and it works in the lspci command in the same way as "Shift+\ ".

I do not have an US keyboard so I can only say what I have read in the forums. 

Second: There is a distinction between the nvidia drivers installed with the Additional Drivers or Jockey/Synaptic, or from the Xswat or other PPA, and those installed by running the nvidia .run file downloaded from the nvidia.com/Download site. Though they may have the same version numbers.

It is important to note that they do not go well together, and neither do nvidia-current and nvidia-current-updates.

**typos1** Posted:>  I also DO very deffinately have nVidia drivers installed, I installed  them myself ! Plus I just tried the commands that Crossbow suggested and  "purge nVidia-*" purged nVidia (freed 300 odd mb of disc space) and  surely it couldnt purge nVidia if there were no nVidia drivers installed  ? It did not find any nvidia .com drivers, it deleted the nvidia-current* drivers which were conflicting. > The following packages will be REMOVED
  nvidia-common* nvidia-current* nvidia-current-updates* nvidia-settings*
  nvidia-settings-updates* ubuntu-desktop* Note the last bit!! You will need to reinstall ubuntu-desktop. This may well exp-lain both your [**typos1'**s] & **Crossbow**'s loss of graphics.```
 sudo apt-get install --reinstall ubuntu-desktop # Then re-boot
```NOTE: APT-GET, NOT: "GET-APT".

Chao!**, bogan.**

---

### Post by typos1 on 2012-09-04
Thanks bogan, its Alt Gr plus the key, that lets me access the pipe/line thing.

Not sure what the thing about apt-get and get-apt is about, never used "get-apt" or heard of it before.

I had installed the latest nVidia drivers on my machine, I DID NOT uninstall them. Maybe the 2 recent updates uninstalled them. I installed them using "additional drivers" in system settings and I have not touched them since, I just installed 2 lots of updates, including nVidia ones. It seems the ones in the updates did not work for some reason, or conflicted with the additional drivers I had installed. Although I have purged and  updated and now everything works fine. I have had these drivers for my graphics card with no problems for the last 2 years. Although I cant remember seeing any nVidia updates in Update Manager before and I always look at what the updates are for before I install them.

As for

"sudo apt-get install --reinstall ubuntu-desktop # Then re-boot"

I simply followed what Crossbow suggested and it worked fine - everything is back to normal now, so how would coding this help now ?

This is what Crossbow suggested:

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current

---

### Post by bogan on 2012-09-04
Hi!, **Crossbow**,

From the log-in screen, press 'Crtl+Alt+F1' [ or F2-F6] to get a TTY login prompt ['Crtl+Alt+F7' will take you back to the GUI ] Log-in and enter password [ it will not show] and 'Enter'. Run:```
 ls -l .*authority # It should give something like:
-rw------- 1 user user 77308 Sep  4 09:56 .ICEauthority
-rw------- 1 user user    57 Sep  4 09:56 .Xauthority
```If any of the 'user's show as 'root', or the permissions are not '-rw-------- 1', that is the cause of your log-in problems.

If so rename the offending file and reboot, Use```
 gksu nautilus / home/username 
```Set 'View' menu to 'Show hidden files' and right-click on the file.

Chao!, **bogan**.

---

### Post by bogan on 2012-09-04
Hi!, **typos1**

If you do not want to Post the lspci output, there is nothing further I can usefully contribute.

You Posted: 
> As far as: "sudo apt-get install --reinstall ubuntu-desktop # Then re-boot"

I simply followed what Crossbow suggested and it worked fine -  everything is back to normal now, so how would coding this help now ?If "everything" includes Ubuntu Unity3d, all the Desktop Icons correct and working, and Videos & games play correctly; then the old saying applies: " If it aint broke, dont fix it."

The command:```
 sudo apt-get install nvidia-current 	
```Will produce totally different results, depending on what PPAs are active. For this reason, it is advised that any additional PPAs should be de-activated [ or purged ] before running an update, if you do not want unannounced  and unexpected updates. 

In **Crossbow**'s case it installed 304.43, in your's I do not know what it installed, and doubt you do.

Chao!,** bogan.**

---

### Post by typos1 on 2012-09-04
No, no bogan, you misunderstand (read previous posts fully to see what has happened), thank you very much for your help, but in the end, the only thing that you suggested that helped any of my problems was to use Alt GR for the pipe/line thing.

Nothing else you suggested worked, but I tried what Crossbow suggested and that sorted everything and my pc is back to normal. So I have no need to do anything more 

Simply coding:

sudo apt-get update
sudo apt-get purge nvidia-*
sudo apt-get install nvidia-current     

and then restarting sorted it. 

Thanks for trying, I do not wish to seem ungrateful, its just that on this occasion your suggestions didnt work. So I have no need to post any outputs because I am back to normal.    :)

Unless you want the lspci output to see what had actually happened ?

---

### Post by bogan on 2012-09-04
Dont bother, Glad it is fixed.

---

### Post by mikeyxote on 2012-09-08
I've been having this same problem for a couple of weeks now.  I was able to get it working by selecting the "Experimental 3D support for NVIDIA cards" drivers.  Not everything is working like it was however:
-Some of the Gnome functions are gone like sticky windows.
-the NVIDIA settings manager is still not available under Administration
-Minecraft fails with a java error when I try to start(might be unrelated, but started at the same time)

A couple differences that I noticed when I was trying to figure out the problem is that the API mismatch error tells me that the Kernel version is 302.17 and the NVIDIA driver version is 304.37.  When I try 'modinfo nvidia' it tells me that the kernel version is 304.37.  What could be causing this discrepancy?

I'm going to roll on with typo1's solution(purge and re-install).  Thanks for hashing out this problem and posting solutions!

p.s. this is my first post on Ubuntuforums!

---

### Post by bogan on 2012-09-08
Hi!, **Mickyxote**,

If your "Experimental 3D support for NVIDIA cards" driver is from nvidia.com, & not an ubuntu nvidia-current or 'updates' version,  you will need to use "sudo apt-get purge nvidia*", instead of "sudo apt-get purge nvidia-*".

Watch the messages as it operates, & if it removes 'ubuntu-desktop', you may need to re-install it.

Chao!, **bogan**.

---

### Post by mikeyxote on 2012-09-08
Bogan,

    Greetings!  Is there a way to figure out where the experimental driver came from?  I've never installed any drivers manually, but when I installed the graphics card I added the Ubuntu-x-swat repositories for natty.  That's likely where they are from as I recall.

The purge/re-install did work and now it shows that both the nvidia-current driver and the experimental are working.  I tried disabling the experimental driver and my second screen went away.  The odd side issues that I mentioned before are still there as well.  I also tried re-installing the nvidia-settings package in synaptic...still nothing.

Thanks.

MXote

---

### Post by bogan on 2012-09-08
Hi!, **mickeyxote,**

Try:```
 lspci -nnk | grep  -iA3 VGA
sudo apt-cache policy nvidia-current
cat /sys/module/nvidia/version
```The first will tell what divers and modules are installed.

The second will show what versions of nvidia-current are installed, or available to you and where they come from. If you know the package name of the 'experimental' driver, insert it in the second command, and run that as well.

The third will only work, if you had an nvidia.com downloaded driver installed, otherwise itwill show 'no such...'

If you Google:"Experimental 3D support for NVIDIA cards" you will get several references to it, but they date to 2011, and it is apparently the original nouveau updated driver, which is now the default nvidia driver in 12.04.

It used to be that nvidia drivers were not compatible with nouveau, and it had to be blacklisted , but it appears that the latest versions of both can live side by side.

If the driver you downloaded is an old version of nouveau it could be causing trouble.

The question is: What happens if you remove --purge the experimental & the nvidia driver and run on the default nouveau driver.??

Running:```
 /usr/lib/nux/unity_support -p
```before and after, might throw some light on the problems you have.

Chao!, **bogan**.

---

