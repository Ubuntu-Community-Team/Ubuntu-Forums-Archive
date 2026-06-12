---
title: "cannot login after upgrading to kde 4.3.3... low graphics mode..."
date: 2009-12-01
forum: General Help
---

### Post by ichundu on 2009-12-01
hi,
i'm using kubuntu 9.10 and i just upgraded to kde 4.3.3 (i have both kde and gnome installed). after rebooting i cannot enter the login screen where i enter my username and password. i get a message after usplash saying "ubuntu is running on low graphics mode. your screen, graphics card, and input device settings could not be detected correctly. you will need to configure these yourself." what can i do now? perhaps booting in the recovery mode (where i still get the 'low graphics mode' message) and trying the repair options that are available?
i have nvidia graphics card with driver version 185.18.36. i have installed it through 'Hardware Drivers' from the menu. kernel version is 2.6.31-15-generic.
Thanks!

---

### Post by ichundu on 2009-12-01
bump?

---

### Post by Spectre5 on 2009-12-01
What is in your xorg.conf file?  Run the nvidia settings with sudo (sudo nvidia-settings) and go to the X Server Display Configuration...make sure it looks right and press "Save to X Configuration File."  Restart the computer and see if it is any better.

---

### Post by ichundu on 2009-12-01
> **Spectre5 said:**
> What is in your xorg.conf file?  Run the nvidia settings with sudo (sudo nvidia-settings) and go to the X Server Display Configuration...make sure it looks right and press "Save to X Configuration File."  Restart the computer and see if it is any better.

here are xorg.conf and Xorg.0.log
as for nvidia-settings i cannot access it because i'm not able to graphically login into my desktop, only in command line mode.

Thanks

---

### Post by nerdy_kid on 2009-12-01
i just enabled backports on my pc and am getting the same issue.  However, i just hit 'cancel' and after a sec everything goes normal....no idea why.

NVIDIA 192.42 (8600M GT)

[edit] **looks though x log** yup: same error.  Hit cancel and then everything should go nicely :D  maybe a smart ubuntu person can tell us why...

---

### Post by ichundu on 2009-12-01
> **nerdy_kid said:**
> i just enabled backports on my pc and am getting the same issue.  However, i just hit 'cancel' and after a sec everything goes normal....no idea why.

NVIDIA 192.42 (8600M GT)

[edit] **looks though x log** yup: same error.  Hit cancel and then everything should go nicely :D  maybe a smart ubuntu person can tell us why...
i hit cancel the first time i got the message and then everything got back normal, but now i don't get the message anymore when i boot in normal mode, it only shows up in recovery mode now. there is just a black screen with a pulsing cursor after usplash :confused:

---

### Post by nerdy_kid on 2009-12-01
ok.

id rm the xorg config as to attemp to regain the GUI, then try to downgrade the xserver.  i dont know which packages were upgraded in the backports as i used kpackagekit.  if anyone can help out here, it be cool ;)

im gonna go fish though my syslogs and see if i can find something...


[edit] if you used synaptic -- check the history

---

### Post by nerdy_kid on 2009-12-01
oh yeah -- GOT IT!

ok, first make sure you let the blinking cursor sit for a while -- it took mine a bit to start up but i think it should work.

heres the log;
```

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 305776 files and directories currently installed.)
Preparing to replace x11-common 1:7.4+3ubuntu7 (using .../x11-common_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement x11-common ...
Preparing to replace sreadahead 1.0-5 (using .../sreadahead_1%3a0.90.3-2_i386.deb) ...
Unpacking replacement sreadahead ...
Selecting previously deselected package ureadahead.
Unpacking ureadahead (from .../ureadahead_0.90.3-2_i386.deb) ...
Preparing to replace libglu1-xorg-dev 1:7.4+3ubuntu7 (using .../libglu1-xorg-dev_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement libglu1-xorg-dev ...
Preparing to replace xlibmesa-gl-dev 1:7.4+3ubuntu7 (using .../xlibmesa-gl-dev_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement xlibmesa-gl-dev ...
Preparing to replace xserver-xorg-video-all 1:7.4+3ubuntu7 (using .../xserver-xorg-video-all_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Preparing to replace xserver-xorg-input-all 1:7.4+3ubuntu7 (using .../xserver-xorg-input-all_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg-input-all ...
Preparing to replace xserver-xorg 1:7.4+3ubuntu7 (using .../xserver-xorg_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg ...
Preparing to replace xorg 1:7.4+3ubuntu7 (using .../xorg_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xorg ...
Processing triggers for man-db ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 18310
Setting up x11-common (1:7.4+3ubuntu10) ...
Installing new version of config file /etc/gdm/failsafeXinit ...
Installing new version of config file /etc/gdm/failsafeXServer ...

Setting up ureadahead (0.90.3-2) ...

Setting up sreadahead (1:0.90.3-2) ...
Removing obsolete conffile /etc/init/sreadahead.conf
Removing obsolete conffile /etc/cron.monthly/sreadahead

Setting up libglu1-xorg-dev (1:7.4+3ubuntu10) ...
Setting up xlibmesa-gl-dev (1:7.4+3ubuntu10) ...
Setting up xserver-xorg-video-all (1:7.4+3ubuntu10) ...
Setting up xserver-xorg-input-all (1:7.4+3ubuntu10) ...
Setting up xserver-xorg (1:7.4+3ubuntu10) ...

Setting up xorg (1:7.4+3ubuntu10) ...

```sooo downgrade:

x11-common
sreadahead
ureadahead --remove this
libglu1-xorg-dev
xlibmesa-gl-dev
xserver-xorg-video-all
xserver-xorg-input-all
xserver-xorg
xorg


this seems to work for me -- x server flopped then started fine with no dialog.


restart

if you get a command line -- give it a chance

login, and do a sudo apt-get update

hope this helps (for me too :D)



-------------------------------------

---

### Post by ybytyruzu on 2009-12-01
Hi, with me the same, but your tips working here. Now I can login without problem. But there still are the upgrades waiting...
Thank you!

---

### Post by PocketHercules on 2009-12-01
I am having the same issue (kubuntu 9.10), but I am not having any luck getting past the low graphics mode.

Here is the sequence:
(1) boot up takes me to "Ubuntu is running in low-graphics mode..blah..blah..blah"  OK is the only option, so I select it.

(2) Next screen says 
    "What would you like to do:
     o unreadable choice 1
     o reconfigure graphics
     o troubleshoot the error
     o exit to console login"
I can select either OK or cancel.  If I select "exit to console login" and then "OK" or just select "cancel" I am taken to a blank black screen...

Any ideas how I can get to at least a prompt so that I can try some of the tips above in this thread?

Thanks for any help!

---

### Post by ichundu on 2009-12-02
> **nerdy_kid said:**
> oh yeah -- GOT IT!

ok, first make sure you let the blinking cursor sit for a while -- it took mine a bit to start up but i think it should work.

heres the log;
```

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 305776 files and directories currently installed.)
Preparing to replace x11-common 1:7.4+3ubuntu7 (using .../x11-common_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement x11-common ...
Preparing to replace sreadahead 1.0-5 (using .../sreadahead_1%3a0.90.3-2_i386.deb) ...
Unpacking replacement sreadahead ...
Selecting previously deselected package ureadahead.
Unpacking ureadahead (from .../ureadahead_0.90.3-2_i386.deb) ...
Preparing to replace libglu1-xorg-dev 1:7.4+3ubuntu7 (using .../libglu1-xorg-dev_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement libglu1-xorg-dev ...
Preparing to replace xlibmesa-gl-dev 1:7.4+3ubuntu7 (using .../xlibmesa-gl-dev_1%3a7.4+3ubuntu10_all.deb) ...
Unpacking replacement xlibmesa-gl-dev ...
Preparing to replace xserver-xorg-video-all 1:7.4+3ubuntu7 (using .../xserver-xorg-video-all_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg-video-all ...
Preparing to replace xserver-xorg-input-all 1:7.4+3ubuntu7 (using .../xserver-xorg-input-all_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg-input-all ...
Preparing to replace xserver-xorg 1:7.4+3ubuntu7 (using .../xserver-xorg_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xserver-xorg ...
Preparing to replace xorg 1:7.4+3ubuntu7 (using .../xorg_1%3a7.4+3ubuntu10_i386.deb) ...
Unpacking replacement xorg ...
Processing triggers for man-db ...
Processing triggers for hal ...
Regenerating hal fdi cache ...
hal start/running, process 18310
Setting up x11-common (1:7.4+3ubuntu10) ...
Installing new version of config file /etc/gdm/failsafeXinit ...
Installing new version of config file /etc/gdm/failsafeXServer ...

Setting up ureadahead (0.90.3-2) ...

Setting up sreadahead (1:0.90.3-2) ...
Removing obsolete conffile /etc/init/sreadahead.conf
Removing obsolete conffile /etc/cron.monthly/sreadahead

Setting up libglu1-xorg-dev (1:7.4+3ubuntu10) ...
Setting up xlibmesa-gl-dev (1:7.4+3ubuntu10) ...
Setting up xserver-xorg-video-all (1:7.4+3ubuntu10) ...
Setting up xserver-xorg-input-all (1:7.4+3ubuntu10) ...
Setting up xserver-xorg (1:7.4+3ubuntu10) ...

Setting up xorg (1:7.4+3ubuntu10) ...

```sooo downgrade:

x11-common
sreadahead
ureadahead --remove this
libglu1-xorg-dev
xlibmesa-gl-dev
xserver-xorg-video-all
xserver-xorg-input-all
xserver-xorg
xorg


this seems to work for me -- x server flopped then started fine with no dialog.


restart

if you get a command line -- give it a chance

login, and do a sudo apt-get update

hope this helps (for me too :D)



-------------------------------------
hey, i'm on another kubuntu/ubuntu installation (with kde 4.3.2) that i have on another drive on the same computer and the update manager popped out with updates available: the same packages you mentioned here. so it seems the problem has nothing to do with kde 4.3.3 or the kubuntu backports because i haven't added that repo here. now i'm gonna try what you said and see if i can downgrade those packages...

---

### Post by ichundu on 2009-12-02
> **PocketHercules said:**
> I am having the same issue (kubuntu 9.10), but I am not having any luck getting past the low graphics mode.

Here is the sequence:
(1) boot up takes me to "Ubuntu is running in low-graphics mode..blah..blah..blah"  OK is the only option, so I select it.

(2) Next screen says 
    "What would you like to do:
     o unreadable choice 1
     o reconfigure graphics
     o troubleshoot the error
     o exit to console login"
I can select either OK or cancel.  If I select "exit to console login" and then "OK" or just select "cancel" I am taken to a blank black screen...

Any ideas how I can get to at least a prompt so that I can try some of the tips above in this thread?

Thanks for any help!

to login in command line mode boot from the 'recovery mode' entry in grub, then select the first option, the one you say 'unreadable choice'. it actually shoud read something like: 'run ubuntu in low graphics mode for this session only'. than select the first option again: 'Resume normal boot'. you should be able to login in command line mode now.

EDIT: i just booted in normal mode after a couple of tries and this last time there was no problem, graphics is ok... so strange :rolleyes:

---

### Post by nerdy_kid on 2009-12-02
> **ichundu said:**
> hey, i'm on another kubuntu/ubuntu installation (with kde 4.3.2) that i have on another drive on the same computer and the update manager popped out with updates available: the same packages you mentioned here. so it seems the problem has nothing to do with kde 4.3.3 or the kubuntu backports because i haven't added that repo here. now i'm gonna try what you said and see if i can downgrade those packages...


yeah i just discovered that they moved these 'updates' to the update section...
ill post how to do this via command line in a bit...dont have time just yet to research it.  

I personaly am sticking with the upgrade -- i can login consistantly and am hoping that a stupid x crash i kept having has been fixed...

---

### Post by ybytyruzu on 2009-12-02
Hi, I disable kubuntu backports and the updates are still there so are "regular" updates. Maybe the new package ureadahead is the problem.

---

### Post by geoff123 on 2009-12-02
Same problem here.  Has anyone definitively figured out what package causes this. I did a number of updates last night on two computers (both nvidia and intel graphics) and this affects them both.  

I think there were was ureadahead, xorg... kde 4.3.4 and maybe a few others.  

I'd like to not make too many changes or fumble around removing and installing more things than necessary.

Thanks, Geoff

---

### Post by ichundu on 2009-12-02
> **nerdy_kid said:**
> yeah i just discovered that they moved these 'updates' to the update section...
ill post how to do this via command line in a bit...dont have time just yet to research it.  

I personaly am sticking with the upgrade -- i can login consistantly and am hoping that a stupid x crash i kept having has been fixed...

i know a way to downgrade via command line but haven't tested it myself. let's say you want to downgrade the xorg package. you can run 'sudo apt-cache xorg' and check the versions available. the output in the end has something like:
```
Provides:                                                                    
1:7.4+3ubuntu10 - x-window-system-core x-window-system                       
1:7.4+3ubuntu7 - x-window-system-core x-window-system                        
Reverse Provides: 
```
remove the existing xorg package and then install the lower version with:
```
sudo aptitude install xorg=1:7.4+3ubuntu7
```

i'm not downgrading for the moment either. want to see if the problem gets fixed in a different way. as i said i had no problem on the last boot. will try other boots to see what happens.

EDIT: i did 5-6 reboots and i get the 'low graphics mode' message now again, but at least i'm able to login graphically after i hit cancel

---

### Post by nerdy_kid on 2009-12-02
> **geoff123 said:**
> Same problem here.  Has anyone definitively figured out what package causes this. I did a number of updates last night on two computers (both nvidia and intel graphics) and this affects them both.  

I think there were was ureadahead, xorg... kde 4.3.4 and maybe a few others.  

I'd like to not make too many changes or fumble around removing and installing more things than necessary.

Thanks, Geoff


the packages to downgrade are:

xserver-xorg
xserver-xorg-video-all
xserver-xorg-input-all
x11-common
xorg
sreadahead


follow ichundu's instructions to downgrade via commandline.

---

### Post by PocketHercules on 2009-12-02
> **ichundu said:**
> to login in command line mode boot from the 'recovery mode' entry in grub, then select the first option, the one you say 'unreadable choice'. it actually shoud read something like: 'run ubuntu in low graphics mode for this session only'. than select the first option again: 'Resume normal boot'. you should be able to login in command line mode now.

EDIT: i just booted in normal mode after a couple of tries and this last time there was no problem, graphics is ok... so strange :rolleyes:

Ichundu,

Thanks for your feedback.  Unfortunately, all this yields me is a blank black screen with no prompt.  I have tried all kernel versions available in my grub menu as well as there corresponding 'recovery mode' entries.  Any ideas why I don't get a prompt or a console login?

---

### Post by ichundu on 2009-12-02
> **PocketHercules said:**
> Ichundu,

Thanks for your feedback.  Unfortunately, all this yields me is a blank black screen with no prompt.  I have tried all kernel versions available in my grub menu as well as there corresponding 'recovery mode' entries.  Any ideas why I don't get a prompt or a console login?

i don't know why you don't get the prompt, sorry. i didn't get it either for some times, just the black screen, that's why i was trying 'recovery mode' where i did get the prompt and was able to login to command line. it looks like a buggy and unstable behavior of x server. maybe you have to wait for some minutes at the black screen and see what happens, like nerdy_kid suggested.

---

### Post by nerdy_kid on 2009-12-02
PocketHercules:

or login via recovery console and downgrade through the root shell.  I'd also dispose of your current X config -- maybe:

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_OLD

```or something like that.  dont create a new one until you get basic graphics back...

---

### Post by lacihobo on 2009-12-02
I downgraded these packages and now everything is ok. 
But I don't understand why these packages were updated when they are not working? ](*,)

---

### Post by geoff123 on 2009-12-02
I fixed mine by setting it to use gdm instead of kdm.

From the terminal:
"sudo dpkg-reconfigure gdm"
then select gdm
reboot.

So looks like something is messed with the new KDM 4.3.4

Computer 1 (nvidia): was able to login using recovery mode and do this easily
Computer 2 (intel): recovery mode didn't even work and kept giving me a black screen after it tried to start in low graphics mode.  The xorg error was about not finding the "i810" driver.  easily logged in via ssh to fix.

I feel really sorry for non-command line people when this sort of thing happens.

---

### Post by nerdy_kid on 2009-12-02
> **geoff123 said:**
> I fixed mine by setting it to use gdm instead of kdm.

From the terminal:
"sudo dpkg-reconfigure gdm"
then select gdm
reboot.

So looks like something is messed with the new KDM 4.3.4

Computer 1 (nvidia): was able to login using recovery mode and do this easily
Computer 2 (intel): recovery mode didn't even work and kept giving me a black screen after it tried to start in low graphics mode.  The xorg error was about not finding the "i810" driver.  easily logged in via ssh to fix.

I feel really sorry for non-command line people when this sort of thing happens.

interesting. what about the people here who are having the same issue with KDE 4.3.3?
i dont think it is KDM, but i could be wrong :)  ill try gdm out and see if it helps my case...
and yeah it sucks for non terminal users ;)

---

### Post by PocketHercules on 2009-12-02
Thanks to all for digging in and reporting which packages needed to be downgraded.  I have successfully downgraded and I am back in the game.

---

### Post by penguin79 on 2009-12-03
To further compliment ichindus instructions on how to downgrade from command line, here's what was needed exactly on my Karmic to go back one step from the versions as of 3-Dec-2009 10:00 AM (GMT+2):
 
(disregard the sudos if you're on root shell)
 
sudo aptitude install x11-common=1:7.4+3ubuntu7
sudo aptitude remove ureadahead
sudo aptitude install libglu1-xorg-dev=1:7.4+3ubuntu7
sudo aptitude install xlibmesa-gl-dev=1:7.4+3ubuntu7
sudo aptitude install xserver-xorg-video-all=1:7.4+3ubuntu7
sudo aptitude install xserver-xorg-input-all=1:7.4+3ubuntu7
sudo aptitude install xserver-xorg=1:7.4+3ubuntu7
sudo aptitude install xorg=1:7.4+3ubuntu7
sudo reboot
 
Pls note that the removal of ureadahead also correctly downgraded the sreadahead pkg as suggested earlier in this thread. After this the almighty KDM login screen appeared on my screen as it should.
 
I was able to get to the command line via SSH, on 2nd PC I noticed that the shell was accessible also by clicking "Cancel" on all the "Ubuntu is running in low graphics ..."-warning dialogs. Running on ATI/Radeon here.
 
Anyone have a clue how this mess got started in the first place, i.e. how the broken pkgs got to the apt updates?
 
/Kimmo

---

### Post by nerdy_kid on 2009-12-03
dispite all my doubts, switching to gdm also solves the error!  of course the suckish part is that now i have to use the commandline from within KDE to shutdown the pc, as the shutdown/reboot commands in kicker depend on KDM.

---

### Post by nerdy_kid on 2009-12-03
as a side note, everyone with this issue use KDM?

---

### Post by Tautoa on 2009-12-03
> **nerdy_kid said:**
> as a side note, everyone with this issue use KDM?

Just installed KDE, and experienced the same issue as the OP after rebooting.
Running "sudo dpkg-reconfigure gdm" and selecting "gdm", as suggested above, fixed this for me.

---

### Post by ybytyruzu on 2009-12-03
Oh yes, enabling GDM login without problem, but not KDM...but after downgrade all these updates KDM is working fine again. Here I have AMD Semprom 3500 - ATI Radeon Xpress 1100, Ubuntu 9.10, but now using KDE 4.3.4.

---

### Post by pchev on 2009-12-03
I got the same problem after installing the ureadahead and x.org update today. 
I was using KDM with KDE 4.3.2, I not use any backport.

Switching to GDM also solve the problem for me. 
The brown/blue mix is not the nicest startup effect but I prefer that than reverting this packages.

---

### Post by Chame_Wizard on 2009-12-03
Low graphics(800x600)?

```
sudo xrandr -s 1024x768
```

If krandRtray is installed,you can choose the resolution/screen size higher than 1024x768. 
;)

---

### Post by kxmas on 2009-12-03
It has something to with a package included with ubuntu-desktop.  
I was fine with 4.3.3 until I ran 'apt-get install ubuntu-desktop'  My wife is used to the gnome desktop, so I installed it for her.

Now, my screen goes blank after showing the kubuntu logo.

---

### Post by pchev on 2009-12-03
No, we get this "low graphic" message because KDM crash. But if I accept to start in "low graphic" my session was 1680x1050 with full acceleration, Kwin effect working normally.

---

### Post by ichundu on 2009-12-03
> **nerdy_kid said:**
> dispite all my doubts, switching to gdm also solves the error!  of course the suckish part is that now i have to use the commandline from within KDE to shutdown the pc, as the shutdown/reboot commands in kicker depend on KDM.
that's the reason why i don't use gdm. it's sad we don't have shutdown/restart options in kde.

> It has something to with a package included with ubuntu-desktop. 
I was fine with 4.3.3 until I ran 'apt-get install ubuntu-desktop' My wife is used to the gnome desktop, so I installed it for her.

Now, my screen goes blank after showing the kubuntu logo.

if the screen goes blank and you don't get the 'low graphics mode' prompt then you should boot in recovery mode and from konsole run what penguin79 summarized at post #25 to downgrade those packages.

so is this only happening to those who have both kde and gnome and not to those who use only one desktop environment???

---

### Post by ybytyruzu on 2009-12-03
No, now I installed Ubuntu Karmic and then Kubuntu Desktop, but before this I installed a clean Kubuntu karmic and enable backports and there was ureadahead and the other packeges but on backports and experimented the same behavior. Now with the normal updates of the same packages the bug is still there. Maybe is time to report to launchpad.

---

### Post by kxmas on 2009-12-04
> **pchev said:**
> No, we get this "low graphic" message because KDM crash. But if I accept to start in "low graphic" my session was 1680x1050 with full acceleration, Kwin effect working normally.

Which video chip are you using?  I have an intel IGP and there was no way to recover.

---

### Post by pchev on 2009-12-04
> **kxmas said:**
> Which video chip are you using?  I have an intel IGP and there was no way to recover.

I have an ATI 5770 with fglrx from Catalyst 9.11

---

### Post by pchev on 2009-12-04
OK, I just try at work with an Intel IGP on a system without gdm and instead of showing the recovery menu it just show a black screen and cut the screen power :(

Rebooting in recovery mode I remark the following in kdm.log:
X: /tmp/.X11-unix has suspicious mode (not 1777) or is not a directory, aborting.

So I remove all files in /tmp and reboot. And now all is working fine :)
I rebooted 3 time straight to the kdm login screen without problem.

---

### Post by manishsk on 2009-12-04
> **ybytyruzu said:**
> No, now I installed Ubuntu Karmic and then Kubuntu Desktop, but before this I installed a clean Kubuntu karmic and enable backports and there was ureadahead and the other packeges but on backports and experimented the same behavior. Now with the normal updates of the same packages the bug is still there. Maybe is time to report to launchpad.

**Followup here, I have already raised a bug:**
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483")

Thanks,
Manish

---

### Post by kxmas on 2009-12-04
> **ichundu said:**
> that's the reason why i don't use gdm. it's sad we don't have shutdown/restart options in kde.



if the screen goes blank and you don't get the 'low graphics mode' prompt then you should boot in recovery mode and from konsole run what penguin79 summarized at post #25 to downgrade those packages.

so is this only happening to those who have both kde and gnome and not to those who use only one desktop environment???

Booting in recovery mode results in the exact same blank screen that booting normally does.  It's really horrific.  As far as a I can tell, it's the Intel IGP that's the factor with the blank screen in recovery mode.

I had to boot off a live cd, set up a chroot, and switch to GDM.

---

### Post by kxmas on 2009-12-04
> **pchev said:**
> OK, I just try at work with an Intel IGP on a system without gdm and instead of showing the recovery menu it just show a black screen and cut the screen power :(

Rebooting in recovery mode I remark the following in kdm.log:
X: /tmp/.X11-unix has suspicious mode (not 1777) or is not a directory, aborting.

So I remove all files in /tmp and reboot. And now all is working fine :)
I rebooted 3 time straight to the kdm login screen without problem.

Interesting.  I shall try this after work and report my results here.

---

### Post by PAC1 on 2009-12-04
There's an extra twist to this story as some of us can't even read the "low graphics mode" pop-up as the wrong resolution is selected and all you can see is mush!  

[http://ubuntuforums.org/showthread.php?p=8439202](http://ubuntuforums.org/showthread.php?p=8439202)

Rolling back the X updates (post #19 of bug report [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483?comments=all](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483?comments=all)) got my system working again using KDM.

---

### Post by nerdy_kid on 2009-12-04
i tryed purging /tmp/; no change over here

---

### Post by nakednous on 2009-12-04
I got the same issue after upgrading to kde 4.3.4. I upgraded to kde 4.3.3 before without any problem. Switching to gdm solved it to me. Do you know if there is a bug report about this?

---

### Post by kxmas on 2009-12-04
> **nakednous said:**
> I got the same issue after upgrading to kde 4.3.4. I upgraded to kde 4.3.3 before without any problem. Switching to gdm solved it to me. Do you know if there is a bug report about this?

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483")

---

### Post by reto.ineichen on 2009-12-05
Don't ask me why, but the following steps helped to solve the problem on my Kubuntu Karmic Koala with KDE 4.3.3:

1. copy /etc/init/gdm.conf to a place as you like (backup)
2. delete /etc/init/gdm.conf
3. Restart Kubuntu

Apperantly, gdm an kdm are conflicting in the boot process through upstart...

---

### Post by doctordruidphd on 2009-12-05
Hello,
This problem may be related to another bug, that is causing kdm to attempt to start twice. The first time it tries to start is in failsafe mode, before the video driver is loaded, hence the "Low Graphics" error.

Try the following as a workaround:


```
cd /etc/init
sudo mv failsafe-x.conf failsafe-x.conf-disable
cd /etc/init.d
sudo mv failsafe-x failsafe-x-disable 
```

See if this gets kdm going (works here).

---

### Post by ybytyruzu on 2009-12-05
Hello,

doctordruidphd, here is working that. 
Thank You

---

### Post by kxmas on 2009-12-05
> **doctordruidphd said:**
> Hello,
This problem may be related to another bug, that is causing kdm to attempt to start twice. The first time it tries to start is in failsafe mode, before the video driver is loaded, hence the "Low Graphics" error.

Try the following as a workaround:


```
cd /etc/init
sudo mv failsafe-x.conf failsafe-x.conf-disable
cd /etc/init.d
sudo mv failsafe-x failsafe-x-disable 
```

See if this gets kdm going (works here).

I got it working doing something similar.

1.  Change the driver from 'vesa' to your actual driver in [FONT="Fixedsys"]/etc/X11/xorg.conf.failsafe[/FONT].  Failsafe now works with intel.  Big improvement over the blank screen

2.  Create a new [FONT="Fixedsys"]/etc/X11/xorg.conf[/FONT] that contains the following, changing [FONT="Fixedsys"]intel[/FONT] to the driver that you use
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
EndSection

```

3. re-run [FONT="Fixedsys"]sudo dpkg-reconfigure kdm[/FONT] and select kdm as your default.

---

### Post by kxmas on 2009-12-05
I hope everyone with a launchpad account has clicked the *Does this bug affect you?* link at the top of bug report.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483")

---

### Post by nerdy_kid on 2009-12-05
[doctordruidphd]("http://ubuntuforums.org/member.php?u=740768")'s workaround works for me; thanks!  now you said that kdm is trying to start itself twice -- is this issue in a script? cause then we could kill the first time it tries to start before the video drivers are loaded.....

---

### Post by marshalldn on 2009-12-05
[doctordruidphd]("http://ubuntuforums.org/member.php?u=740768")'s workaround works for me too...thanks a lot!!!!

---

### Post by jojohippo on 2009-12-05
Thank you doctordruidphd, it worked!

---

### Post by kxmas on 2009-12-05
> **nerdy_kid said:**
> [doctordruidphd]("http://ubuntuforums.org/member.php?u=740768")'s workaround works for me; thanks!  now you said that kdm is trying to start itself twice -- is this issue in a script? cause then we could kill the first time it tries to start before the video drivers are loaded.....

I saw two messages in my log as well from KDM stating that X server died at startup.  One failure for normal startup, the second failure for the bulletproof X or whatever it is failing.

So not really a script failure.  If X fails, then bullet proof X should kick in.  Something is wrong with how KDM detects failure or more likely, how long KDM waits before declaring failure.

---

### Post by manishsk on 2009-12-06
I don't have failsafe-x in my init-d dir. /etc/init dir has the mentioned file.

/etc/init.d$ cat failsafe-x
cat: failsafe-x: No such file or directory

---

### Post by Francesco Ricci on 2009-12-06
Someone has solved with the new kernel 2.6.31-16?

---

### Post by manishsk on 2009-12-06
> **Francesco Ricci said:**
> Someone has solved with the new kernel 2.6.31-16?

I have not updated yet and worried about should I go ahead or not. I also have the updates waiting for the 7 degraded packages to solve lo-graphics mode issue.

---

### Post by Thehound on 2009-12-06
I get the same thing with Karmic and KDM with both Intel and ATI graphics. I also can login fine if I hit cancel and wait a few seconds at the black screen it produces. KDM then pops up like nothing happened. Everything on my e16 desktop works fine. Logged into KDE and same. Even hardware acceleration is no issue. Now to add some fuel to this fire. If I boot into kernel 2.6.31-15, this issue does not occur at all. No low graphics mode warning and just a normal login. With 2.6.31-16, I get the warning but can login by hitting cancel. My xorg.conf has not been changed in months and I confirmed such by opening it up and looking at it.

Edit: Tried doctordruidphd's workaround and it does indeed work. Solves a big annoyance on a system I'm otherwise happy with, for now. I just got to remember I did that workaround when a fix is actually issued.

---

### Post by kxmas on 2009-12-07
A new gdm package has been uploaded to karmic-proposed and will be available in a few hours.  

From the bug report:
> Accepted gdm into karmic-proposed, the package will build now and be available in a few hours. Please test and give feedback here. See [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) for documentation how to enable and use -proposed. Thank you in advance!

---

### Post by manishsk on 2009-12-09
> **kxmas said:**
> A new gdm package has been uploaded to karmic-proposed and will be available in a few hours.  

From the bug report:

Please check out [here]("https://bugs.launchpad.net/ubuntu/karmic/+source/gdm/+bug/491483") for more details.

---

### Post by roaltug on 2009-12-09
> **geoff123 said:**
> I fixed mine by setting it to use gdm instead of kdm.

From the terminal:
"sudo dpkg-reconfigure gdm"
then select gdm
reboot.

So looks like something is messed with the new KDM 4.3.4

Computer 1 (nvidia): was able to login using recovery mode and do this easily
Computer 2 (intel): recovery mode didn't even work and kept giving me a black screen after it tried to start in low graphics mode.  The xorg error was about not finding the "i810" driver.  easily logged in via ssh to fix.

I feel really sorry for non-command line people when this sort of thing happens.

Thanks, this solved my problem.

---

### Post by Vecho on 2009-12-09
Gdm update solved my problem :)

---

### Post by zelhar on 2009-12-09
I have the same problem and my video card is ATI HD3650. 

I can load Ubuntu with the older kernel but with the latest kernel, 2.6.31-16-generic and also with the rt kernel I get the same problem. 

The weird thing is it did used to be able to work with the new kernel and other times it gave me this error. Now it would never work.

update: I switched to gdm and problem seems to be solved.

---

### Post by PocketHercules on 2009-12-12
> **doctordruidphd said:**
> Hello,
This problem may be related to another bug, that is causing kdm to attempt to start twice. The first time it tries to start is in failsafe mode, before the video driver is loaded, hence the "Low Graphics" error.

Try the following as a workaround:


```
cd /etc/init
sudo mv failsafe-x.conf failsafe-x.conf-disable
cd /etc/init.d
sudo mv failsafe-x failsafe-x-disable 
```See if this gets kdm going (works here).


doctordruidphd,

Just one question about the workaround you posted...did you also revert the packages that were proposed by other users?  or did you apply this workaround without reverting the packages?

---

### Post by ichundu on 2009-12-13
> **PocketHercules said:**
> doctordruidphd,

Just one question about the workaround you posted...did you also revert the packages that were proposed by other users?  or did you apply this workaround without reverting the packages?

i haven't tried doctordruidphd's workaround, but i guess you don't have to downgrade those packages. this is an alternative solution to downgrading the packages.

---

### Post by ichundu on 2009-12-13
seems like problem is solved for me. i upgraded xorg and other packages in my other kubuntu installation that i use for testing and there is no such problem, it's working fine. i've been busy and not up to date with the latest news about the issue, is the problem solved or what?

---

### Post by PocketHercules on 2009-12-13
ichundu,

I found another thread that seems to be talking about the same issue.  This thread, titled ureadahead update - can't login, is located at:
[http://ubuntuforums.org/showthread.php?t=1343648](http://ubuntuforums.org/showthread.php?t=1343648)

Post #15 by kolAflash indicates there is an update.  I pulled in this update using the update manager, but it did not fix the issue for me.

With regard to your other reply to my, I did try doctordruidphd's workaround with the latest version of the packages mentioned in other posts.  It worked fine.  So, as you suspected, no need to downgrade packages...just another workaround.

Just a note on the package downgrade workaround...this workaround quit working for me yesterday, which is why I started to investigate other options...

---

### Post by wall0645 on 2009-12-13
Has this been solved yet? I haven't updated for over a week, don't wanna go through the hassle of fixing it.
EDIT: Fixing it *again*.

---

### Post by ichundu on 2009-12-16
> **wall0645 said:**
> Has this been solved yet? I haven't updated for over a week, don't wanna go through the hassle of fixing it.
EDIT: Fixing it *again*.

it is solved for me, but i'm waiting for others to confirm as well

---

