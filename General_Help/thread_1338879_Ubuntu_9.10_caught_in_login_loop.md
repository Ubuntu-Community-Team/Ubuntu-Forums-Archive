---
title: "Ubuntu 9.10 caught in login loop"
date: 2009-11-26
forum: General Help
---

### Post by Chimmer on 2009-11-26
Ok...I have a dual boot PC, WinXP SP3 and Ubuntu 9.10. I usually run WinXP during the week and Ubuntu on weekends. Since I have a few days off, I booted into Ubuntu today and checked and installed the latest updates as I always do.

Now I'm having a strange problem. When I reboot, choose Ubuntu, I get the login screen, make sure my username and password is entered and it starts to finish loading and then stops, the screen goes black for a second and then takes me right back to the login/password screen.

I enter everything again and same issue, it won't finish loading and takes me back to the login screen. I booted up in recovery mode, tried repairing things, tried rebooting, same problem.

One time I was able to successfully get in. When it asked for my username, I click "other" instead of the pre-filled default and then entered my username and password and it worked. Used Ubuntu all day and then rebooted to see if I had any problem. Sure enough I'm stuck again at the username/password loop. No matter what I do, I can't get past this point. I enter user name and password, it looks like it's proceeding to load and then bounces me back to the login screen again.

Does anyone know how I can fix this issue?

Thanks for any help!

---

### Post by spider_0k on 2009-11-27
Have to say I have the same problem. Still searching for the answer myself. Trouble is I don't know where to begin. So even if you don't have the complete answer I would be grateful for s shove in the right direction.

Philip

---

### Post by Spiraea on 2009-11-27
I'm having the exact same problem. I had it set to automatically login so I shouldn't be seeing this screen in the first place but for whatever reason, I am. My password appears to be accepted but I just go right back to the login screen. Using Ctrl+Alt+F1 and entering my login information there works so proves that I have the information right. I tried using the "Other" at the screen but got the same results.

The last thing I did was remove pulseaudio and installed GNOME-ALSA MIXER to control my sound. I was having too many problems with pulseaudio (couldn't hear system sounds, VLC player audio was going in and out, in-fact only the Last.Fm application was the only thing that was working right with pulseaudio) but after removing it, everything was coming in crystal clear. I did a reboot shortly after and this is where I'm at. I don't believe that has anything to do with the current problem but I'm not sure what it could be..

---

### Post by Chimmer on 2009-11-27
I sort of got mine to work. During the boot, I chose the recovery mode, repair files option then chose to continue to boot. It asked for username and password. The GUI didn't load but at the command prompt I typed "GDM" and got it to load properly.

I then went into synaptic package manager and re-downloaded and installed the 2.6.31-14 image that I had previously deleted. 

After a reboot, I select the -14 image and I can usually launch it within 2 tries of entering username and password. I also deleted the -15 image which is what caused all the problems I was having.

I also noticed that the login screen resolution is too large for my monitor, if I move the cursor down, there are additional options at the bottom of the screen. I have my resolution set to 1024x768 and it looks fine once Ubuntu is loaded so I don't know why the boot screen resolution is different.

The -15 image update definitely caused the login problems for me so hopefully a future update will take care of things. One thing I've learned is when they do an image update, keep at least one previous copy instead of deleting it.

---

### Post by Spiraea on 2009-11-27
"gdm" brings about an error for me:
 
> ** (gdm-binary:1898 ) : WARNING **: Failed to acquire org.gnome.DisplayManager: Connection ":1.22" is not allowed to own the service "org.gnome.DisplayManger" due to security polices in the configuration file
 
** (gdm-binary:1898 ) : WARNING **: Could not acquire name; bailing out
 
"sudo gdm" causes the screen to flicker (and the number lock light on my keyboard to go on and off) with an error of:
 
> gdm-binary[1908]: WARNING: Unable to find users: no seat-id found
gdm-binary[1908]: WARNING: GdmDisplay: display lasted 2.654298 seconds
*A number of additional "gdmDisplay: displayed lasted ???? seconds, followed by:*
gdm-binary[1908]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
 
I'm pretty much a linux noob so I don't really know where to go from here.

---

### Post by Chimmer on 2009-11-27
> **Spiraea said:**
> 
I'm pretty much a linux noob so I don't really know where to go from here.

Did you reboot, choose recovery mode, then choose resume normal boot, enter your username and password, wait for it to do it's thing and then at the command line type GDM?  That's what did it for me. 

What image(s) show up in the boot screen and which do you select? 

Another thing you could try is to repair files from the recovery mode, I think I did that a few times too.

---

### Post by Spiraea on 2009-11-27
Yes, I did exactly that. I've also tried repairing numerous times with no results. I took a suggestion that I googled that Grub could be affecting it so I upgraded from Grub Legacy to Grub 2.. I now have Grub 2 but still getting the same results.
 
Images in Grub are:
 
> Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Ubuntu, Linux 2.6.28-15-generic
Ubuntu, Linux 2.6.28-15-generic (recovery mode)
Microsoft Windows XP Professional
 
The -14 image is even more wonky as I don't even get the login screen, just a command prompt that flashes and has a serious delay on typed letters.

---

### Post by Chimmer on 2009-11-27
> **Spiraea said:**
> 
The -14 image is even more wonky as I don't even get the login screen, just a command prompt that flashes and has a serious delay on typed letters.

Did you try the 28-15 image...the oldest one you have listed?

---

### Post by Spiraea on 2009-11-27
> **Chimmer said:**
> Did you try the 28-15 image...the oldest one you have listed?
 
Just did, got the same result as the 31-15.

---

### Post by Spiraea on 2009-11-27
Since it appears to be the Gnome display manager not working properly, I'm currently in the process of downloading KDE and seeing if I'm able to login using it. I used the command:
 
sudo aptitude install kubuntu-desktop
 
which I believe is downloading all the necessary files. If it's not, someone please let me know. I'll keep you updated.

---

### Post by Spiraea on 2009-11-27
And I'm in! So GDM is definitely the problem. I guess somehow it got corrupted so it looks like I'll have to reinstall it although I am going to give KDE a bit of a go.. see if I perfer it over GDM.
 
Perhaps this is you guys problem as well?

---

### Post by cybrsaylr on 2009-11-27
I was having the same problem.
Here's my thread:
[http://ubuntuforums.org/showthread.php?p=8399629#post8399629](http://ubuntuforums.org/showthread.php?p=8399629#post8399629)

I suspect it's the 32 bit version of KK....at least it was for me.
64 bit KK boots up normal with none of that 'looping' the OP posted on both my laptop and brand new PC.

FWIW, I only had that same looping while running 32 bit KK.

---

### Post by spider_0k on 2009-11-28
Further investigation:

I have a "visitor" login that reproduces the same problem (on hdd1. However I also have an older installation on another hdd that 'works'.

The home folders are on separate partitions on the two drives, so I edited the fstab on the 1st drive (problem installation) to the 'old' /home on my second hdd 2. that also works. This seems to point to something in the /home folder hdd1.

I the edited the fstab on drive 2 to point to the /home folder on hdd1. booted from hdd2 and .... it worked???

I'm now very confused!

to top it all now pulse audio has gone west, but that's another issue.

I have run out of ideas. Thinking about replacing /home hdd1 with /home hdd2.

I will wait and see what tomorrow brings here.

philip

---

### Post by Chimmer on 2009-11-28
Yeah, I'm losing patience. I can get past the login/password screen maybe 1 out of 8 tries. Once I'm in, I'm ok. 

I updated to Grub2 and now the GDM thing doesn't work, I get the same error messages that was posted in the earlier thread.

Maybe I'll just wait a few weeks and see if there are any type of updates. I'm not going to waste my weekend trying to figure this out.

---

### Post by Spiraea on 2009-11-28
> **Chimmer said:**
> Yeah, I'm losing patience. I can get past the login/password screen maybe 1 out of 8 tries. Once I'm in, I'm ok. 

I updated to Grub2 and now the GDM thing doesn't work, I get the same error messages that was posted in the earlier thread.

Maybe I'll just wait a few weeks and see if there are any type of updates. I'm not going to waste my weekend trying to figure this out.

Well after trying out KDE (didn't like it, too slow. Heck my Windows XP starts up faster and start-up speed is a big deal to me), I simply used these commands:

> sudo apt-get update

> sudo apt-get install ubuntu-desktop

to reinstall Ubuntu (I had removed it from the synapatic package manager). After that I logged out and into Gnome and followed up with removing KDE from the commands at this link):

> [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

And I'm now in GDM and life is good. Had a few cluttered apps from between the two but nothing major. Now there should be an easier, quicker fix to GDM.. perhaps a reinstall code such as

> sudo apt-get reinstall ubuntu-desktop
or
> sudo apt-get reinstall gdm
?

Take those with a grain of salt as it's a more or less a guess at what the commands are than actual knowledge but at the very least, it couldn't hurt.

---

### Post by efflandt on 2009-11-28
The normal way to start X with the default window manager (usually gnome in ubuntu) is with the command **startx**.  But if you pick a (recovery) kernel and resume booting, you have to log in as your user in the console and then run startx.

I had issues being unable to boot with normal grub2 menu entries (blinking cursor for a second, then nothing with no disk activity).  But if I manually enter grub commands it boots fine to gui login, and if I use (recover) menu selection and run startx, gnome works fine.  Apparently gfx or splash had trouble finding a mode after I switched my DVI 1280x1024 19" monitor to DVI 1280x720 27" HDTV (although, the TV accepts 1280x1024).  Gnome automatically recognized it as 1280x720 (its real resolution).

The HDTV boots fine when connected with VGA.  Then gnome does not see its actual resolution, but offers an alternate 1360x768 that works (close to most 720p HDTV's).

I need to test if setting a specific GRUB_GFXMODE or disabling splash in /etc/default/grub would help booting with DVI.

---

### Post by Chimmer on 2009-11-29
> **Spiraea said:**
> 
to reinstall Ubuntu (I had removed it from the synapatic package manager). After that I logged out and into Gnome and followed up with removing KDE from the commands at this link):
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)


I had installed Kubuntu Desktop to see if it would make a difference, it didn't, I was still caught in the endless login loop so I used the link above to get back to a "Pure Gnome" desktop.

I was still having problems logging in, but one of the times I was able to, I then installed "Start Up Manager" which seemed to update to GRUB2 beta 1.97. 

Ever since that, I've been able to login without any problems using the -14 image. I removed the -15 image and won't update again until I hear of a new -16 or better image. 

The boot screen resolution is still way off, everything doesn't fit on the screen even though it's set to 800x600 in the start up manager but I'm not going to complain too much, as long as I still can get past the login screen.

---

### Post by Chimmer on 2009-11-29
Well, looks like I spoke too soon. After several successful tries, I'm now stuck in the endless login loop again. This really sucks. 

I wonder if it has to do with the monitor resolution at the login screen? It's too large to fit the screen although once I get lucky and get Ubuntu to load properly, the resolution is fine. 

I wish someone could figure this out because I sure can't. :(

[COLOR="Blue"]**Edit:**[/COLOR] After some googling, I found I was able to change the login/password resolution screen by editing the xorg.conf file. Here is what I did:

sudo gedit /etc/X11/xorg.conf

I noticed the value for "virtual" was too high so I changed it to 1024 768 and now the login screen displays properly. Not sure if this will fix the loop that I was caught in, it will probably take me dozens of successful logins to confirm but I'm hoping it works. 

Below is the section of the xorg.conf file that I changed...changes are in blue.

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	[COLOR="Blue"]**1024	 768**[/COLOR]

---

### Post by asdeasde on 2009-11-29
I had the same problem
 

 it was that the resolution of the login screen (higher) was not the same that the  
 desktop screen that I set up (lower)
 

 the installation default was 1280x960 I changed to 1152x864 this was causing 

the login loop 



 now it is back to 1280x960  
 

 I think that the different resolutions login (higher) and 

desktop (lower) cause the loop
 

 when the login screen goes to the desktop it change resolution 

but it dos not go to the desktop it goes back to the login  
 

 this work for me I hope it works for you  
 

 try to set the same resolution on both screens, from the recovery mode   
 

 does anybody knows were the config files for the login and the desktop screens are? 



 	 	 pd English it is not my native language

---

### Post by asdeasde on 2009-11-29
several logins and working great

---

### Post by Chimmer on 2009-11-29
> **asdeasde said:**
> I had the same problem
 
 it was that the resolution of the login screen (higher) was not the same that the  
 desktop screen that I set up (lower)

I suspected that the higher resolution of the login screen may have been causing me problems. 

> **asdeasde said:**
>  does anybody knows were the config files for the login and the desktop screens are? 

See my post just above yours, where I edited the xorg.conf file, this changed the login screen resolution and so far I've logged in at least 5 times with no problems. For the desktop screen resolution, just go to system, preferences, display and you can set it there. 

I'm going to wait awhile before I declare the problem "fixed."

---

### Post by Chimmer on 2009-11-30
I'm going to mark this one as resolved. My [post #18]("http://ubuntuforums.org/showpost.php?p=8408929&postcount=18") in this thread contains the info that fixed the problem for me. Hopefully it will help someone else out.

---

### Post by missmoondog on 2009-11-30
> **Chimmer said:**
> I'm going to mark this one as resolved. My [post #18]("http://ubuntuforums.org/showpost.php?p=8408929&postcount=18") in this thread contains the info that fixed the problem for me. Hopefully it will help someone else out.


Same issue here and your trick in post #18 didn't work. This is all the info in my xorg.conf file.

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


I think I started a thread already on this subject when Karmic first came out. This one stupid machine, which technically is my BEST machine, has this reboot loop it goes into when I tried upgrading it to Windows Vista also. At that time, I simply downgraded back to 9,04, which works great. 

I have gone through all 4 other computers and done the distribution upgrade on them with no issues. On one computer, I had to revert all the way back to 8.04 and do the upgrades one version at a time, to get it up to 9.10.

edit:
I just ran the command sudo dpkg-reconfigure -phigh xserver-xorg and logged out then back in. Login worked faster than ever, that time. Should do a complete re-boot and try but don't want to screw with it at the moment.

edit2
OK, rebooted.:
Nope, no difference, although this time it ONLY took 2 tries to login!!

edit3:
was wondering what you people were talking about updating to gdm2, or something like that. just found it in a synaptic update. seems to have fixed the issue too!

have rebooted twice, doing other things also, logged in on first try.

---

### Post by missmoondog on 2009-12-01
on a different computer today and just got the updates. stuck in the worst loop of all time now!!

why is it every time they mess with any thing that has to do with the display in ubuntu, it ALWAYS screws stuff up?

it's been that way since the first time i tried ubuntu version 5.04!

no wonder i end up removing it every time!

absolutely ridiculous. 

going to try a simple log out and log back in. if this computer doesn't login on first try, ubuntu just became history, again!

sheesh!!

edit:
nope, still stuck. so long ubuntu, forever!
already removed the install and grub.

hello windows!!
at leaat it's something that works.
ALL the time!

---

### Post by Chimmer on 2009-12-01
> **missmoondog said:**
> on a different computer today and just got the updates. stuck in the worst loop of all time now!!

why is it every time they mess with any thing that has to do with the display in ubuntu, it ALWAYS screws stuff up?

it's been that way since the first time i tried ubuntu version 5.04!


Sorry to hear of your problems with Ubuntu. I've been using it since version 7.x, installed it as dual boot with WinXP. I was shocked how easy everything went. 

This login loop issue is really the first major problem I've had with Ubuntu and it happened when the recent -15 image update took place. Even after I went back to -14 and removed -15 I was still having problems, so some update that happened the same time as -15 hosed my install. I have a cheap old CRT monitor and I'm guessing that if I had a newer LCD one, I wouldn't have seen the problem with the mismatched resolution.

Hopefully you can get your problem resolved, just keep plugging away and googling, that's how I found my solution.

Good luck!

---

### Post by Reston Marcus on 2009-12-06
Good day all,
 

 Need assistance to become aware on how to repair login to the GUI.  Since 8.04 I have upgraded (traded -- v-e-r-y hard time consuming task) laptops and such, to be able to simply run Ubuntu so that I could be able to learn this OS.  I'd really like  this OS to permanently replace MS-Windows (I'm a linux noob w/little info and familiarity).
 

 Well, now I have an ultra loaded, touch-screen capable, Lenovo t400 laptop with fingerprint activation capability loaded initially with Win-XP.
 

 I upgraded and removed XP for Win-7 Ultimate. After modifying and tweaking it to the max, I decided to try Ubuntu 9.10 after much review and study (today I found this thread).
 

 After that successful install and then the inclusion of some fancy stuff like Compiz, Awn, etc. (which is PHAT) and maintaining automatic log-in for rebooting, suddenly I could not get to the GUI but only to a flickering command-line.
 

 After review and soliciting aid from the community, I did get a single suggestion to try:
 

 “ sudo /etc/init.d/gdm start”
 

 The response to this was:
 

 “since the script you are attempting to invoke has converted to an upstart job, you may also use the “start (8) utility,” e.g. “start gdm start/running, process 2181.”
 

 after trying “start gdm start/running,” I got the message, “no seat id found.”
 

 Then out of curiosity, I tried, “gdm gdm/start” and got this message:
 

 “Failed to acquire org.gnome.DisplayManager Connection “1:20” is not allowed to own the service due to security policies in configuration file.”
 

 Please aid me to repair this so that I can get on my personal mission to assist others too. Don't have a clue on how to adjust the configuration file and scared to blindly attempt all that I've found in Chimmer's thread (# 8393913) but I will, if prodded. 



Please remember I'm NEW to Linux

---

### Post by spider_0k on 2009-12-08
Solved (sort of).

I have one or two things in my home folder that are too complicated to move and I'm lazy anyway.

One of my conclusions was that it may be some kind of script that was running after login. So With my 'Visitor' login (sudo enabled) or login via terminal. I moved all the .(dot) files (not folders) in to a new clean folder.

Restarted logged in, running fine!

I should run down which one that's causing the problem. Sorry guys that's not going to happen.

I know it's marked as solved further up, but this one worked for me, so I felt I should share it in any case.

Philip

---

### Post by ASchweitzer on 2009-12-09
So what distros is everyone running? And are we running with encrypted home folders?

I'm on xubuntu with encrypted home folder, going to do a clean install without encryption to see if this is a problem.

---

### Post by Vitas1 on 2009-12-11
Well I have the similar problem. Here is my configuration and my solution.

Software - Ubuntu 9.10 clean install, encrypted home dir, resolution 1024x768.
Hardware - PIII PC, S3 (?) Video, HP 1702 LCD monitor, KVM switch.

Suddenly (not after install!) I get an infinite loop during logon. Switching KVM-switch during logon sometimes results in successful boot - but with stupid 800x600 non-changeable res.

Generally my monitor supports up to 1280x1024 res, but I want 1024x768. So I create the following /etc/X11/xorg.conf:

##################
Section "Device"
   Identifier   "Configured Video Device"
EndSection

Section "Monitor"
   Identifier   "Configured Monitor"
   ModeLine "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
   HorizSync       30.0-81.0
   VertRefresh     56.0-76.0
   Option "PreferredMode" "1024x768_60.00"
   Option "DPMS"   	
EndSection

Section "Screen"
   Identifier   "Default Screen"
   Monitor      "Configured Monitor"
   Device       "Configured Video Device"
   DefaultDepth 24
SubSection "Display"
   Depth 24
   Modes "1024x768_60.00"
   Virtual 1024 768
EndSubSection
EndSection
#################

NOTE! I get modeline from CVT command - not from GTF! They give me different settings!!!!! HorizSync and VertRefresh were taken from monitor spec.

And now it works! Just hope that these parameters will not blow up my monitor :-)))

---

### Post by ASchweitzer on 2009-12-11
From what I can tell, the issue is with encrypted home directories. When X goes to launch, it attempts to load some files in some subfolder of home, and can't because home is still encrypted. I've also noticed error messages that /home can't be decrypted, but I know it can be because CLI login still works.

So the issue is with encrypted home folders and X. I've done a clean install without encrypted /home and I've had no issues. 

I take it creating /etc/X11/xorg.conf circumvents this problem, since the loading of X is now no longer dependent on the decryption of /home.

Hope that helps someone along the way.

---

### Post by Chimmer on 2009-12-11
> **ASchweitzer said:**
> So what distros is everyone running? And are we running with encrypted home folders?


I'm running Ubuntu 9.10 with a non encrypted home folder I guess. I never ran any type of encryption so however it's installed is how I'm using it. I've just been using ubuntu since versio 7.x on a dual boot PC with WINXP SP3. 

My problem was solved by changing the boot screen resolution as mentioned in my previous post in this thread. Been working fine ever since.

---

### Post by jenelle on 2009-12-11
i get into it i use the Internet i am not sure if it happened after i down loaded a pic then closed it off yesterday but i down loaded  this pic again today after closing it the computer takes it's self out of there and goes into like it is booting up to signing in again so i have to sign in again totally weird !not sure if you understood all that sorry

---

### Post by pottzie on 2009-12-13
I'm stuck in log-in hell too. What gets me is that before the update earlier this week I never had to log in  at all; it just loaded and worked, simply and painlessly. After the  update a few days ago, suddenly I'm asked for my password. I thought then  "This isn't going to be good." It's like asking the owner of a bar to show his driver's license to himself before allowing him to be served. Now since the next update it's clobbered. I'm writing this now from a recovery disc.
 Wonder who's brainstorm this was? Microsoft employee, perhaps?

---

### Post by doctorV23 on 2009-12-13
Same situation here. This is how I fixed it:

I installed the new Xubuntu on an old machine as a low memory system using the 'alternate install'. It went fine, except that upon rebooting the system and entering the password on the login screen, it cycled back to the login screen instead of going to the desktop making the system unusable.
The fix:
1. Before the login screen displays, press Ctrl+Alt+F1 to bring up a text prompt.
2. Here you should be able to successfully enter your username and password.
3. Type and enter "startx" (without quotes) to bring up that annoyingly illusive desktop!
4. Go to System->Update manager->"Settings..." and add "Prereleased updates karmic proposed"
5. Install all missing updates.
6. Enjoy :-)

---

### Post by jeb800e on 2009-12-13
Similar problem here

---

### Post by Chimmer on 2009-12-13
> **doctorV23 said:**
> 
3. Type and enter "startx" (without quotes) to bring up that annoyingly illusive desktop!

That was one of the methods I had tried but after entering startx it started to load, I got the bottom and top tool bars but the screen was black with a spinning circle that just sat there and would not finish loading.

---

### Post by newfrog on 2009-12-18
I try   get manual for _video card_ and _Monitor_ , first _reset monitor_ . go to  _system_ then

_Preferences_ then _display_ .  In display hit detect monitor , this resets things .

next look at the settings , set it so _monitor_ , _video card_ and the _display settings_ 

all match that they are capable of . { I think there are settings that some hardware

is not cable of .} Why it worked before I don't know . Ubuntu 9.10

---

### Post by UranUtan on 2009-12-19
I have tried all the tricks in this thread and nothing works. Except the terminal method Ctrl-Alt-Fx and typing startx. This method is not convenient for the very novice user for whom I prepare the machine for.

Using Xubuntu 9.10 x32, no encrypted home folder. Everything standard + system updates + restricted codecs.

I got fed up, I reinstalled Ubuntu 9.10 on top of Xubuntu. Now no more login loop. It's not Xubuntu issue, on another machine Xubuntu works perfectly. Or may be this bug occurs if there are more than 1 user? B/c on the Xubuntu that works, there is only one user. The troubled Xubuntu has two users.

---

### Post by tojo6940 on 2009-12-22
I am also in the endless logon loop. I am running Ubuntu 9.10 with all updates. I run Gnome and could only log in through Gnome failsafe. I tried a variation of Vitas1's approach and went into start up manager and changed the start up resolution to match the resolution when running normally. Now boots normally in all modes. My problem is solved. I hope it helps you all. Thanks Vitas1.

tojo6940

---

### Post by ub-pir on 2009-12-28
I had a slightly weirder problem: I had three accounts set up, let's say A, B and C; A was super-user. I could login and out as many times as I liked as A but when I tried to login as B or C I couldn't. I could login as either B or C only once after a restart, but I could not log back in again to B or C. Having tried to login as B/C, I couldn't then login to A - had to restart!

My problem now solved with the help of this thread (thanks - :) ) just by adding:

SubSection "Display"
     Virtual 1024 768
EndSubSection

to the "Screen" section of the xorg.conf file, where 1024 x 768 is the user screen resolution I am using. Are all the other  changes   to /etc/X11/xorg.conf suggested in this thread really necessary? My experience suggests not...

Final thoughts: i) I guess this problem only affects people with CRT monitors - no reason to set the resolution of an LCD to anything other than max., and ii) should this really be filed as a bug? Surely a user should not be able to screw-up their system just by changing the screen resolution? This is a bad side-effect!  If it's so critical I would have thought that only the super-user should be allowed to change the screen resolution and that change should also modify the xorg.conf file (or something else in X)?

---

### Post by bbneo on 2009-12-29
How do you go to the startup manager?

---

### Post by bbneo on 2009-12-29
> **ub-pir said:**
> I had a slightly weirder problem: I had three accounts set up, let's say A, B and C; A was super-user. I could login and out as many times as I liked as A but when I tried to login as B or C I couldn't. I could login as either B or C only once after a restart, but I could not log back in again to B or C. Having tried to login as B/C, I couldn't then login to A - had to restart!

My problem now solved with the help of this thread (thanks - :) ) just by adding:

SubSection "Display"
     Virtual 1024 768
EndSubSection

to the "Screen" section of the xorg.conf file, where 1024 x 768 is the user screen resolution I am using. Are all the other  changes   to /etc/X11/xorg.conf suggested in this thread really necessary? My experience suggests not...

Final thoughts: i) I guess this problem only affects people with CRT monitors - no reason to set the resolution of an LCD to anything other than max., and ii) should this really be filed as a bug? Surely a user should not be able to screw-up their system just by changing the screen resolution? This is a bad side-effect!  If it's so critical I would have thought that only the super-user should be allowed to change the screen resolution and that change should also modify the xorg.conf file (or something else in X)?
I have had this issue, but it is somewhat sporadic and my setup is a little different.  Ubuntu 9.10 is connected to my 19" Samsung LCD display through a KVM switch.  When I boot, if the KVM switch is switched to the Ubuntu machine, then the login screen is in full (1024 x 768 resolution), but then if I login, it seems to mode switch to 800x600(?) and then fails.  If I login and then quickly switch the KVM witch to the other machine, then the desktop comes up in 800x600, but the dislay manager only lets me set the mode that high and lists the refresh rate as 60Hz. 
 
Your suggestion might be helpful, but I am afraid that something in the boot/login process might end up overwriting the modifications to the Xorg.conf file.

---

### Post by stmcc on 2010-01-03
asdeasde posted a reply that fix my problem . I would love to think him . I have been fighting this for two months. I had my screen resolution set at 1024X756. It was fine for my old eyes.I had know idea that the new kernel would not be able to handle this. I changed the resolution back to the default 1280X756. So far I have been able to reboot at least 10 times with no problem. I have a crt monitor. My friends with lcd monitors have not had this problem.
MAC

---

### Post by j_neish on 2010-01-26
I'm brand new to Linux so please be forgiving.
 
problem:
on start-up the login screen appears, on entering the
correct username and password start-up proceeds for a
while and then returns to the login screen. This loop
can continue indefinitely or just a few times.
 
The problem seems to be associated with a difference between
the default screen resolution settings used for login and
the user selected screen settings used for the desktop.
(Why are they different?)
At some point after login the system seems to flip to the
different screen settings and crash out back to login.
 
The temporary fix is to keep the desktop screen settings the
same as the default settings. Typically the default settings
seem to be the maximum resolution capability of the screen.
This is fine for an LCD screen but generally not for
a CRT screen. Many message boards are reporting that the problem
only affects CRTs but I suspect this is because only people
with CRTs would want to change screen settings.
In my case I have a DELL P790 CRT which Ubuntu defaults to
1600x1200 @ 60Hz which unfortunately I can't read because
it's too small and I get a headache from the flicker.
I want to run it at: 1280x1024 @ 85Hz.
 
Other message boards are reporting that it may be an NVIDIA
driver problem, I have a 32Mb NVIDIA TNT2 graphic card.
 
If you get the problem really badly, so that you can never
login then all I can think of is to re-install Ubuntu and
don't fiddle with the screen settings until you've applied
some of the following suggestions.
 
Some people are reporting that they've set login to
automatic and have never had to login before. This seems to
be because their first automated login fails after which it
reverts to manual logins.
 
Some message boards have suggested that you can adjust the
default login screen resolution by editing the appropriate
parts of a file called:
/etc/X11/xorg.conf
This maybe so if you know what you're doing and you have such
a file. Apparently Ubuntu 9.10 comes without it but will use
it if necessary!
 
From yet another message board I've found that you can
generate xorg.conf appropriate to your system using the
following commands after switching to one virtual console:
CTRL + ALT + F1 switch to one virtual console
sudo service gdm stop
sudo Xorg -configure
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
sudo service gdm start
 
On examination of this new xorg.conf file you might be able
to see screen resolution settings which could be adjusted.
In my case there was nothing obvious like 1600x1200_60Hz.
However there were horizontal sync and vertical refresh
parameters.
On yet another message board I found that there is a utility
to calculate HorizSync and VertRefresh as follows:
cvt 1280 1024 85
this yielded 91.46 and 84.84 in my case.
So I changed the following xorg.conf lines:
HorizSync 31.0 - 92.0
VertRefresh 50.0 - 150.0
 
to:
HorizSync 91.46 - 91.46
VertRefresh 84.84 - 84.84
 
Yep, I don't know what I'm doing but my CRT hasn't blown
up yet. Interestingly the new values are within the range
of the old values.
Having made these adjustments and re-booted my system, the
login screen comes up at my chosen resolution which matches
the desk top resolution so there is no longer a crash out and
I don't get stuck in the login loop.
However this is not a proper fix because someone could change
the desktop screen resolution, so once again there would be
mismatch between the login and desktop screen resolutions and
presumably my system would be stuck in the login loop again.
 
Please will someone understand and sort out this problem
properly. It's really too bad that my PC was reduced to
unusable junk, I almost gave up and went back to Microsoft.
 
This problem is   NOT SOLVED   even though the thread says so!

---

### Post by Chimmer on 2010-01-26
> **j_neish said:**
> 
This problem is   NOT SOLVED   even though the thread says so!

I was the one who started the thread. I found the solution that worked for me, therefore I marked it solved, because my problem was solved. If people are still having similar issues, maybe a new thread should be started for their specific problem.

I've been using Ubuntu since version 7.x on the same PC. I never had this issue until the 9.10 update, that's when the login resolution issue started happening for me. Luckily, google and these forums helped me to find a solution.

---

### Post by nokedimyo on 2010-01-26
When I bumped into this problem, the solution had to do with the . files in the home directory, as spider_ok had alluded to.  You see, before I was had the problem, I was trying to modify my .profile file and it seems the EOF (end of file for the noobs) flag had gotten screwed up.  Once I removed my .profile file from my home directory (using the recovery mode), I was able to once again login normally.

---

### Post by cgoo on 2010-02-07
I have the same problem. I installed Ubuntu 9.10 and reset my screen resolution on Jan. 8, it all worked fine until I ran updates about 2 weeks later when the login loop started. I had set up a guest account which worked for a few more days then went into the loop. I then did a clean install onto a new hard drive, set my resolution, ran updates and the problem returned. I tried this two more times with the same results. Then I did another clean install, set the resolution, ran only the important security updates and login seemed to work fine. Then four days later (Feb. 2) and maybe 8-9 restarts later the problem has returned. I can still log in to the guest account I created on the last install but I don't know how much longer it will work. I posted the problem on yelp but not one reply in four days.

 I have not encrypted any files and have added only a few apps. I tried Chimmer's fix but there is no file named xorg.conf in the ect/x11/ folder. 

 I really want to make this work but with this recurring problem and no support it might have to be bye bye to Ubuntu.

---

### Post by j_neish on 2010-02-07
Yep, Try reading through all the twists and turns in my Ubuntu adventure above.

---

### Post by Saghaulor on 2010-02-15
> **Chimmer said:**
> Well, looks like I spoke too soon. After several successful tries, I'm now stuck in the endless login loop again. This really sucks. 

I wonder if it has to do with the monitor resolution at the login screen? It's too large to fit the screen although once I get lucky and get Ubuntu to load properly, the resolution is fine. 

I wish someone could figure this out because I sure can't. :(

[COLOR="Blue"]**Edit:**[/COLOR] After some googling, I found I was able to change the login/password resolution screen by editing the xorg.conf file. Here is what I did:

sudo gedit /etc/X11/xorg.conf

I noticed the value for "virtual" was too high so I changed it to 1024 768 and now the login screen displays properly. Not sure if this will fix the loop that I was caught in, it will probably take me dozens of successful logins to confirm but I'm hoping it works. 

Below is the section of the xorg.conf file that I changed...changes are in blue.

Section "Screen"
	Identifier	"Default Screen"
	Device		"VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	[COLOR="Blue"]**1024	 768**[/COLOR]

Worked perfectly for me. Thanks for the help.

---

### Post by jv69 on 2010-02-17
I have had the same problem for about two weeks .  I tried to use the nvidia drivers update for my system, but that does not work.  

Finally,  I copied  the /etc/X11/xorg.conf.failsafe  to /etc/X11/xorg.conf  . This seems to work for now. 

Here is my system stats:
Computer: 1998 Dell XPS T600 P3
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic

Video: 
 *-display UNCLAIMED
                description: VGA compatible controller
                product: NV4 [RIVA TNT]
                vendor: nVidia Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 04
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-1.0 bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:f5000000-f5ffffff memory:fc000000-fcffffff(prefetchable)

---

### Post by combinatorix on 2010-02-28
I also just recently got caught in a login loop for no apparent reason.  I tried
everything in every thread I could find, but could never stop the loop.  The
best I could get was an xterm with no window manager.  So far, I've found it
more cost effective to just punt, reformat and reinstall.

So far, I've put 9.10 on three machines, which works fine at first.  As soon as I
let the updates run, it tends to completely hose everything up.  I think some
strange things are sneaking into configure files, because in one "conf" file
(can't remember which one, unfortunately) I found the word "Version" replaced with "V2rsion".

I think the login and desktop manager startup should be more resilient to
parse errors in general, perhaps giving the user a clear indication of what
went wrong, and not bombing out completely for a parse error on one line.
Figuring out how to do this in a way which doesn't compromise security
will likely be challenging, but I think it would be necessary to gain acceptance
from a larger non-expert community (that and more efficient graphics drivers
for non-mainstream graphics cards).

---

### Post by XDread on 2010-03-15
Hi!  I had the same problem, and I suggest you have a look at the file .xsession-errors in your home directory.

My problem was that I had an illegal export entry in my /etc/profile:

"export a.b.c=/opt/something"

that X didn't like or cared to inform more explicitly.

---

### Post by DigDesignEng on 2010-08-30
First of all, I am confused as to why this thread is marked as "SOLVED", when it seems that so many people are still having problems.  The only solution I can see will be an Ubuntu update which makes the problem go away, which obviously has not happened.  Here is my observations and workaround:

Computer Info:
1. I am running Ubuntu 9.10 on a Compaq Presario 7000 series.
2. Video card is nVidia NV5M64

History and Observations:
I started off running the machine in my home office with a CRT monitor and a KVM switch.  Later I took the machine to my work place where I used a KVM switch with a LCD monitor.  The problem has occurred randomly in both locations.  There have been times when the problem does not reproduce for several weeks.  Presently the problem reproduces every time I restart.  On the recommendation of another web site I removed my /etc/X11/xorg.conf file.  That did not help.  I think people may be fooled into thinking they have a fix because the problem is so random.  I am now in a state where I can reproduce the problem on boot or use the following workaround to guarantee entry into my OS:

Workaround: 
(Note: This only appears to work with a KVM switch.  I tried to do the same by turning off the monitor, but did not get the same effect.)
1. After first unsuccessful login click your username to retry the login.  Right after you click the "log in" button, switch the monitor to another computer using your KVM switch.
2. Wait for login to complete before switching back to your Ubuntu machine.
3. When you return you should get a login retry window, but this time it should be at the 800x600 resolution (as far as I can tell).  Login again at this new resolution.  If it works continue to next step.
4. Now that you have successfully entered your X Windows environment, check your resolution again (system->preferences->monitor).  It should give you a max resolution of 800x600.  Click the "apply" button to re-apply this resolution.  Apparently this changes the default values for the system.
5. Now reboot again with the new resolution saved.
6. The next time you login, it should be a success.  If so, continue reading...
7. After booting successfully using the 800x600 default resolution, go back to system->preferences-monitor and you should see that the options to change your resolution to higher values have been restored.

This workaround works for me repeatedly.  However, it does not fix the problem on a permanent basis.  However (hopefully) it can get you back into your OS so you can try other changes until you can find a permanent fix.

---

