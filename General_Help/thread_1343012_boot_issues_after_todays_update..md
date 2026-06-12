---
title: "boot issues after todays update."
date: 2009-12-01
forum: General Help
---

### Post by john newbuntu on 2009-12-01
Just about 4 hours ago, I updated ubuntu software using the update manager in Gnome.  I primarily use Gnome but I also have the kde-desktop installed.  But after todays update, I am unable to log back into Linux.  First of, I am missing windows OS in the GRUB, which means the grub has been updated somehow and removed windows OS.  Also, when I boot into Linux, I get a wierd looking screen in which nothing is decipherable - absolute garbage.  None of the keys respond after that. The update today included the following:
x11-common, sreadahead, gdm 2.28.1-0ubuntu1, liblancelot0 4:4.3.2-0ubuntu5 , plasma-widget-addons, plasma-dataengines-addons, xserver-xorg-video-all, xerver-xorg-input-all 

Is anyone else experiencing this problem?

e2fsck looks good. memory is also good and I do not have Nvidia or any other
graphics card- just the internal Intel card. I have had karmic for over 2 weeks with several shutdowns and have had no problem so far.  Nothing extraordinary in the logs.

---

### Post by 5BallJuggler on 2009-12-01
> **john newbuntu said:**
> Just about 4 hours ago, I updated ubuntu software using the update manager in Gnome.  I primarily use Gnome but I also have the kde-desktop installed.  But after todays update, I am unable to log back into Linux.  First of, I am missing windows OS in the GRUB, which means the grub has been updated somehow and removed windows OS.  Also, when I boot into Linux, I get a wierd looking screen in which nothing is decipherable - absolute garbage.  None of the keys respond after that. The update today included the following:
x11-common, sreadahead, gdm 2.28.1-0ubuntu1, liblancelot0 4:4.3.2-0ubuntu5 , plasma-widget-addons, plasma-dataengines-addons, xserver-xorg-video-all, xerver-xorg-input-all 

Is anyone else experiencing this problem?

e2fsck looks good. memory is also good and I do not have Nvidia or any other
graphics card- just the internal Intel card. I have had karmic for over 2 weeks with several shutdowns and have had no problem so far.  Nothing extraordinary in the logs.

I had the problem a couple of days ago, I was convinced that it was something to with kdm, 
the day before I installed a load of kubuntu programs from the repository, when I rebooted i was asked if i wanted to change to kdm permamently, and of course I selected "yes".

when I next rebooted I had the same thing as you are descibing, it took me a while to sort it out.

1. shutdown the PC and reboot, when prompted to selected boot options press escape, you need to select the earliest kernal of linux that you can find.
2. select this kernel, in repair mode/safe mode/debug mode (I can't remember what it is called)
3. when you boot up, you will be told that your display drivers are no good, click OK,
4. you should then get the option to boot in low graphics mode. select this
5. at this point I then removed kde from my system in the synaptic package manager. when I rebooted, my system was OK.

I hope this helps
Phil.

---

### Post by 5BallJuggler on 2009-12-01
just a little more info.

today's update also include linux-firmware.

and after the updates, I rebooted with no problems.

---

### Post by philinux on 2009-12-01
> **john newbuntu said:**
> Just about 4 hours ago, I updated ubuntu software using the update manager in Gnome.  I primarily use Gnome but I also have the kde-desktop installed.  But after todays update, I am unable to log back into Linux.  First of, I am missing windows OS in the GRUB, which means the grub has been updated somehow and removed windows OS.  Also, when I boot into Linux, I get a wierd looking screen in which nothing is decipherable - absolute garbage.  None of the keys respond after that. The update today included the following:
x11-common, sreadahead, gdm 2.28.1-0ubuntu1, liblancelot0 4:4.3.2-0ubuntu5 , plasma-widget-addons, plasma-dataengines-addons, xserver-xorg-video-all, xerver-xorg-input-all 

Is anyone else experiencing this problem?

e2fsck looks good. memory is also good and I do not have Nvidia or any other
graphics card- just the internal Intel card. I have had karmic for over 2 weeks with several shutdowns and have had no problem so far.  Nothing extraordinary in the logs.

Try running 

sudo update-grub

from recovery mode

---

### Post by john newbuntu on 2009-12-01
Thanks Phil and Phil.
The only 2 kernels I have in the boot menu is 2.6.31-15-generic and recovery.  Choosing either modes takes me to that same garbled screen which is not humanly decipherable. After hitting enter (or tab and enter), it takes me to a blank screen.  No combination of key presses get me a prompt, which means that the kernel (or initramfs) never gets loaded.

However, I can, by using a live cd mount my partitions one by one and read the data.  On carefully observing the logs, I see these messages:

> kdm main process ended, respawning
kdm respawning too fast, stopped
init: gdm main process terminated with status 1
kdm: failed to start X server. Starting failsafe X server.
kdm: X server died during startup
kdm: X server for display :0 cannot be started, session disabled
kernel: mtrr: no MTRR for c0000000,7b0000 foundWithout getting to a shell, I would be unable to do any updates I assume, unless there is a way to do this using liveCD.


WAIT A SECOND!
Something serendipitous just happened.  As I was about to submit this, I decided to give it one last try.  So, after choosing the regular 2.6.31-15-generic option and booting, I hit the following keys in rapid succession(delay probably half a second between each): escape, Ctrl+F1, Ctrl+F2, Ctrl+F3.  Lo and behold the boot went like just any another normal boot and everything looks fine now.  All the files, hardware and networking devices worked normally.  A sudo update-grub2 identified the Windows partition and hopefully fixed it.  I also tried doing an update but there was nothing to update.

So, is there some key sequence that allows the kernel to be brought up and kdm to start the X server normally?

---

### Post by Altayr2 on 2009-12-02
Hello!

i have exactly the same problem after xorg yesterday's update.
1. X server was starting in low graphics mode
2. After regenerating configuration still starting in low graphics mode
3. Randomly about every second system restart X was starting correctly
4. In daemon.log I see:
Dec  2 11:53:10 localhost init: gdm main process (1459) terminated with status 1
Dec  2 11:53:11 localhost kdm[1460]: X server died during startup
Dec  2 11:53:11 localhost kdm[1460]: Failed to start X server. Starting failsafe X server.
Dec  2 11:53:32 localhost kdm_greet[1773]: Cannot load /usr/share/kde4/apps/kdm/faces/.default.face: No such file or directory

From [here]("https://wiki.ubuntu.com/X/Bugs/NvidiaDriverMissingKernelDriver") I tried:
dpkg-reconfigure nvidia-185-kernel-source
and this (re?)created /lib/modules/2.6.31-15-generic/updates/dkms/nvidia.ko

I can confirm that I have working xorg.conf, the problem somewhere else.

Still after every reboot I get:
 **Ubuntu is starting in low graphics mode**

but if I pres Esc, failsafe mode configurator disapears, I see tty1 login prompt.
Just wait 5 seconds and eventually normal KDM login screen appears!!! 
I am writting from normal accelerated graphical session now, but if I restart computer this story start over again.

One more interesting thing, that Ctrl+Alt+F1 till F6 shows normal console login tty's,
and F7 shows blinking cursor! F8 shows garbage on screen, and F9 is this normal working X session which I am working now!

If somebody could help with fix please write here!

Also this is kdm.log from start (I rotated logs before reboot):
 ddxSigGiveUp: Closing log

Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.

 ddxSigGiveUp: Closing log
Warning:  Failsafe mode was already attempted within 30 seconds.
Warning:  Falling back to gdm to report the issue.

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu


... normal load continues..

---

### Post by tarator on 2009-12-02
Hello I have the same problemns after the last upgrade.
But i now can't get to a login-shell (as mentioned by john above) (Strg+Alt+F2 etc. doesn't work)
I just get a blank screen. Can anybody tell me how to solve this problem?
If i could login to the console it would be great!

I tried any of the options (Run in low praphics mode, reconfigere, troubleshoot, go to login console) but with no effect. The screen stays black....
So I can't type any command....

Can anybody help me?

---

### Post by john newbuntu on 2009-12-02
One thing you could try is to bring up the window manager from a single user mode.  So when you boot the computer, at the grub menu, hit escape.  Choose your normal linux kernel option and hit "e" for edit.  Go to the end of the line.  Remove the quiet and splash keywords and replace them with "S" without quotes. Hit enter and b.
Now it should take you to a console (cross fingers).  Login as root and type kdm or /etc/init.d/kdm.

---

### Post by tarator on 2009-12-02
Thanks for your reply, but it didn't work.

Replacing quiet and single has no effect. (Normal and recovery)
The kdm still starts on boot.

Do i use the "S" flag right!?

I could start a Live system and edit files, but I'm not sure which files to manipulate.
Any suggestions!?

[IMG]http://i581.photobucket.com/albums/ss258/tarator/Kubuntu/PC023010.jpg[/IMG]

[IMG]http://i581.photobucket.com/albums/ss258/tarator/Kubuntu/PC023011.jpg[/IMG]

[IMG]http://i581.photobucket.com/albums/ss258/tarator/Kubuntu/PC023012.jpg[/IMG]

---

### Post by Altayr2 on 2009-12-02
Yes, exactly same screen!

After you get message about low graphics mode, pres Esc, then on another message
What you want to do imideatelly press Esc again and wait 15 seconds, for me normal login prompt from kdm appears!

Ps. I am experiencing this on two computers, both kubuntu, but have gnome installed, one has Radeon video card another has Nvidia, so this is not driver related.

---

### Post by tarator on 2009-12-02
Pressing ESC also didn't work for me... Screen stays still....

I logged in via SSH now. That works...

Then I removed package "kdm" with aptitude and restarted. (As mentioned above.) Everything works fine (xfce as wondow manager).

---

### Post by Altayr2 on 2009-12-02
somehow Esc work only when default login manager set to kdm. I have tried xdm, just plain tty2 login prompt. Now will try gdm.

---

### Post by nuclearsaber on 2009-12-02
kdm doesn't work for me after the last update. Sometimes I only get a black screen, other times I come to the X11 failsafe mode. I have had to change the display manager to gdm instead using

sudo dpkg-reconfigure gdm

However I also had problems even getting a login shell where I could do this.

---

### Post by yo2boy on 2009-12-02
Just to be safe, I didn't update my system. But, should I? If so, when?

---

### Post by powerwave on 2009-12-02
Hello all,

I had also issues after updates installed today on Ubuntu 9.10. However I have an Nvidia graphic card and haven't seen a login screen at all, just a white ubuntu logo which will never disappear. After rebooting a few times, I was able to boot into Ubuntu like usual.

I remembered that xorg was listed to update ealier, so I went to synaptic manager, selected the xorg packet and forced to install the older version 1:7.4+3ubuntu7. After this ubuntu worked like before 

Edit: Hmm, one day later I got the same problem again: no login screen, just ubuntu white logo, rebooting then works.

Manuel

---

### Post by nilera on 2009-12-02
After update I have the same problem with low graphics mode. If I enter console login and start KDM manually from the command line, things work normally until I reboot.

---

### Post by ricerider1 on 2009-12-02
Add me to the list. My problem is that system doesn't see grub or OS on dual boot that was working. It had been taking a long time to load grub before update, now it can't find anything but cd. I booted off ubuntu 9.10 and booted to first hdd which is win hdd and it went to hdb where my koala lives and booted successfully. I am newb, so I am just reading and trying. Havan't found a working solution yet.

---

### Post by Thiago_M on 2009-12-04
Same here, after the update kdm won't work anymore (gdm still runs fine).

kdm log shows
```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.
```

which strikes me as a particularly odd error...

---

### Post by john newbuntu on 2009-12-05
Try first with the new kernel that was put in yesterday (2.6.31-16-generic) using sudo apt-get update and see if that solves the problem.  If not, read on..

In the file /etc/default/grub, replace the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```with
```
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT=""
```and run 
```
sudo update-grub
```Yeah, you may not have a fancy boot into *buntu but you get to know what is going on.  So far, 5 of my boots are clean with the .15-generic kernel.

Edit:
Alas, after about a dozen successful boots, I have the same problem.  So, I decided to use gdm as the default manager
dpkg-reconfigure gdm
and choose gdm.

---

### Post by Kokopelli on 2009-12-05
I have been having this problem as well.  I am beginning to suspect it is a event dependency problem with upstart and kdm.

1) gdm works fine
2) with kdm I get the "starting in low resolution" messages, however if I quickly exit to console (last option on the menu) KDM will start automatically and correctly a few seconds after the CLI login prompt shows up.

So this suggests to me that either 
-KDM is not starting early enough and so the default "starting in low resolution mode" message is coming up (preventing KDM from starting).
or
-KDM is starting too early and the underlying X11 is not ready for KDM.

I suspect the former.  Is there any way to disable the checks and failsafe for X?

---

### Post by tjmcwiz on 2009-12-06
I had the same problem with issues after these updates. I had the blank screen with the associated problem of KDM respawning. There is another thread (can't remember now where it's at) that does a good job of providing insight into the problem. 

It appears to be a problem between the latest KDM (4:4.3.2-ubuntu7.1) and Upstart. I disabled KDM from starting from upstart by changing kdm.conf to kdm.conf-disable within the /etc/init directory. Changing the name to be anything but config at the end will prevent the script from executing. 

```
sudo mv -f kdm.conf kdm.conf-disable
sudo mv -f failsafe-x.conf failsafe-x.conf-disable
```

This prevents KDM from starting (assuming it's the default display manager) and allows me to get to a login prompt (non-graphical). Upon logging in than I just type

```
sudo kdm
```

And the graphical session comes up normally. This is just a work around until somebody fixes something or gains additional insights to help solve the problem.

If someone has suggestions --- I can see if the suggestions will fix the problem.....

---

### Post by teddybairs1 on 2009-12-07
Near as I could tell, the problem was with the most recent KDM update, although I updated with the 4.3.4 release from Kubuntu.org's launchpad repos. I was finally able to get to the KDE login screen after pressing ctrl-f5 during the usplash. I then assumed that it was the KDM and so I went into /etc/X11/default-display-manager and changed it to /usr/sbin/gdm from /usr/bin/kdm.

I then booted back up and everything was normal under Gnome. It's not the first time I've had trouble with the KDM, but it's been a long time. My plan at the moment is to continue with the GDM until someone has a fix for KDM. Remember, you don't need to wipe KDE out completely, you can select the KDE session from the GDM login screen and it will start normally.

---

### Post by wapitismith on 2009-12-09
I was having the same problem but I don't use KDM.  I re-installed the ubuntu-desktop and everything is working again.

Just FYI

---

### Post by john newbuntu on 2009-12-13
This issue seems to have been resolved through some of the updates that were done on kde.  Now, I am able to log in just fine straight to either gnome or kde without any problems or changes.

---

### Post by Altayr2 on 2009-12-17
yes, last kernel update solved it.

---

