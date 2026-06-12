---
title: "prayer to GODS of UBUNTU"
date: 2011-04-09
forum: General Help
---

### Post by moongya on 2011-04-09
hello ubuntu lovers

my prayer to you is to help me fix my ubuntu desktop.. it seems to suddenly haunted with invisible ghosts.. please excorsice (bad spelling). 

well it goes like this...my 2 month old ubuntu maverick installation was working wonderfully but all of a sudden while scrolling through an open office word document my mouse got possesed. started scrolling all over weirdly like it had a mind of it's own (A.I)

I saved the doc and rebooted (in 25 secs, am proud to reduce my boot time to 25 secs)

upon rebooting, i do not see any of my notification icons viz. network, bluetooth(yes i have bluetooth adapter) and missing others(which am unable to recollect now)

after reboot the mouse is still possesed.. 
also, am unable to un-install anything from ubuntu software center.. have tried apt-get update/upgrade/clean etc.. all structures are build correctly no issues there. just unable to uninstall anything from software center

then i tried to uninstall via snyaptic.. thankfully synaptic works as usual

then i tried to adminstration > user settings.. now here too i click on all buttons.. like uncheck the box which says do not required password for next login. but nothing happens..

is panel or gnome the culprit.. please help me

i love ubuntu and dont have (neither willing to pay) money to pay for windows.. 

and am s**t scared to re-install it.. that would be a nightmare

save me

while i get replies.. hopefully fast :) i will try this:
dpkg-reconfigure xserver-xorg
as suggested by other threads... lets c if my joy is restored by this

---

### Post by Bcrowes11 on 2011-04-09
sounds like a track pad issue, unless you're using a desktop, then you may have a virus.:(

---

### Post by spielball on 2011-04-09
I am just a newbie in Ubuntu. But if I would experience this problems, I would suspect a hardware failure. Sounds like your motherboard or hard drive is damaged or soon to fade away. I recommend you create an Ubuntu live cd. Then boot from the live cd and check if your system is still 'possessed'. If the same problems occur when you use a live cd, then you have a hardware problem. If not, then it's a software problem. And if it's only a software problem, someone in here might be able to help.

---

### Post by Bcrowes11 on 2011-04-09
I agree with spielball.;)

---

### Post by moongya on 2011-04-09
yes m using desktop... and virus in ubuntu is unheard of.. plus i always used latest version of clamav... so no virus

---

### Post by moongya on 2011-04-09
> **spielball said:**
> I am just a newbie in Ubuntu. But if I would experience this problems, I would suspect a hardware failure. Sounds like your motherboard or hard drive is damaged or soon to fade away. I recommend you create an Ubuntu live cd. Then boot from the live cd and check if your system is still 'possessed'. If the same problems occur when you use a live cd, then you have a hardware problem. If not, then it's a software problem. And if it's only a software problem, someone in here might be able to help.
not a hardware problem as am able to boot into windows and have complete control over mouse and other hardware

---

### Post by Bcrowes11 on 2011-04-09
Dude, you read any latest virus report, there are new viruses EVERYDAY! Don't be so naive! And just because it affects linux doesn't mean it'll affect Windows. If it's a virus it's obviously written for LINUX. K?

---

### Post by moongya on 2011-04-09
> **Bcrowes11 said:**
> Dude, you read any latest virus report, there are new viruses EVERYDAY! Don't be so naive! And just because it affects linux doesn't mean it'll affect Windows. If it's a virus it's obviously written for LINUX. K?
clamav with latest virus definitions does not detect it!!! any ideas how to detect if there is virus? by the way what antivirus you use?

---

### Post by moongya on 2011-04-09
Newbies with all due respect my prayer is to GODS of ubuntu not to you guys... we, u and me are in the same boat..so with all due respect please dont reply for the heck of it.. I need answer from Ubuntu GOD, not u guys..

---

### Post by d3v1150m471c on 2011-04-09
please post the output of the following:
```

sudo apt-get update
sudo cat /etc/apt/sources.list

```

---

### Post by moongya on 2011-04-09
thank u for interest (now i believe am getting closer to resolving my issue)..

i have done sudo apt-get update and everything went smoothly but nonetheless will post results to what you have asked me to post in about 4 hours.. as right now me works and am away my dear ubuntu machine.. please wait for my reply.. tnx

---

### Post by jerome1232 on 2011-04-09
Is your mouse usb or ps/2? I recall having an issue with a ps/2 mouse on one computer, the mouse would go sporadic moving rapidly and click inhumanely fast.

Ubuntu just had some issue with that mouse, bought a new one and everything was fine, note I didn't have a problem under Windows, same computer, same mouse.

Do you have any other mice you can test?

I also doubt it's any sort of malware... that's silly to me for many reason.

---

### Post by moongya on 2011-04-09
it is usb mouse, and besides the mouse issue the other weird part is my notification icons have mysteriously disappeared and am unable to click anything in admin > user settings..or in software center

saving grace is that m still able to boot and surf net but can not admin machine using any gui, which makes me believe prob is with panel or gnome..also thankfully am still able to sudo, so am hoping a fix can be achieved soon

also, i doubt it is virus as i have scanned my machine with clamav with up to date virus definitions..

anyways cant wait to output what d3v1150m471c has suggested... eagerly waiting to get back to my ubuntu machine

---

### Post by SeijiSensei on 2011-04-09
Try another mouse.

---

### Post by moongya on 2011-04-09
will definitely try that, meanwhile any suggestions for absence of notification icons or inability  to click anything in admin > user settings..or in software center?
as I believe they are not mouse related

---

### Post by moongya on 2011-04-09
> **d3v1150m471c said:**
> please post the output of the following:
```

sudo apt-get update
sudo cat /etc/apt/sources.list

```
reply to d3v1150m471c

```

sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_IN
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_IN
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages
Reading package lists... Done


sudo cat /etc/apt/sources.list
# 
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.

deb [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main
deb-src [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu) maverick main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security universe main restricted multiverse #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe main restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates universe main restricted multiverse #Added by software-properties
```

---

### Post by d3v1150m471c on 2011-04-10
it looks like it completed without any errors. you might try using the following to see if it works:
```

sudo apt-get install figlet
sudo apt-get remove figlet

```are you having any other issues other than your machine not installing software?

additionally:
```

gksudo software-center

```

if it won't let you install anything running it from the terminal, should in theory tell us the problem

---

### Post by moongya on 2011-04-10
posted something stupid 
deleted it

---

### Post by d3v1150m471c on 2011-04-10
when apt, synaptic, update manager, software center, ect is running it locks dpkg so that another similar program can't run simultaneously and screw up your system. it seems to me another process is running that has it locked or it didn't become unlocked. give me a second and i'll play around on my system and see what i can uncover. also, post the following please:
```

top -n1

```additionally, you may want to try this:
```

sudo rm /var/lib/dpkg/lock
sudo apt-get install figlet

```also, i found this link:
[http://www.linuxquestions.org/questions/linux-newbie-8/e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-temporarily-unavailable-360554/](http://www.linuxquestions.org/questions/linux-newbie-8/e-could-not-get-lock-var-lib-dpkg-lock-open-11-resource-temporarily-unavailable-360554/)

---

### Post by moongya on 2011-04-10
sudo apt-get remove figlet
[sudo] password for amit: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  adobe-flashplugin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  figlet
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 913kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 189743 files and directories currently installed.)
Removing figlet ...
Processing triggers for man-db ...

was able to add and remove figlet

next am able to install and remove software using 'gksudo software-center' but not when I start software center by going to applications > software center

this is what I see upon running 'gksudo software-center'

 gksudo software-center
2011-04-10 22:03:36,365 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2011-04-10 22:03:36,365 - root - WARNING - failed to add sca db Couldn't detect type of database
2011-04-10 22:03:38,161 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2011-04-10 22:03:38,162 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/update.py', 367, '_error_cb')'
2011-04-10 22:03:38,162 - root - WARNING - error: Operation not supported
2011-04-10 22:03:38,336 - softwarecenter.app - INFO - software-center-agent finished with status 1
2011-04-10 22:03:48,584 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-04-10 22:03:48,584 - dbus.proxies - ERROR - Introspect error on :1.42:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.65" (uid=0 pid=3523 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.42" (uid=0 pid=2122 comm="/usr/bin/python))
amit@ubuntu:~$ gksudo software-center
2011-04-10 22:04:08,416 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/database.py', 96, 'open')'
2011-04-10 22:04:08,415 - root - WARNING - failed to add sca db Couldn't detect type of database
2011-04-10 22:04:10,571 - softwarecenter.backend.scagent - WARNING - error in query_info 'Operation not supported'
2011-04-10 22:04:10,572 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/db/update.py', 367, '_error_cb')'
2011-04-10 22:04:10,572 - root - WARNING - error: Operation not supported
2011-04-10 22:04:10,750 - softwarecenter.app - INFO - software-center-agent finished with status 1
2011-04-10 22:04:40,717 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
2011-04-10 22:04:40,716 - dbus.proxies - ERROR - Introspect error on :1.42:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.68" (uid=0 pid=3546 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.42" (uid=0 pid=2122 comm="/usr/bin/python))

lots of errors there, may be you would know..

I believe my userid is unable to achieve elavated privilages.. please help me d3v1150m471c

---

### Post by d3v1150m471c on 2011-04-10
> **moongya said:**
> 
next am able to install and remove software using 'gksudo software-center' but not when I start software center by going to applications > software center

I am assuming you're selecting software center by the default menu. If you right-click your menu button you can change your menu preferences. Navigate to the software-center entry in your menu preferences and change its launch command to gksudo software-center, like the command above that worked. I think that would prettymuch wrap it up no? :D

---

### Post by moongya on 2011-04-10
many thanks my joy is partly restored... but still bunch of issues.. if you are not bored please continue helping..

I get this error when i run 'gksudo login-screen' I see administrative privilage dialog starting but closes automatically and nothing happens

please tell me what you make of this error log:

Apr 11 00:16:34 ubuntu gdm-session-worker[1536]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" was met by user "amit"
Apr 11 00:16:34 ubuntu gdm-session-worker[1536]: pam_unix(gdm:session): session opened for user amit by (uid=0)
Apr 11 00:16:34 ubuntu gdm-session-worker[1536]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Apr 11 00:16:36 ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=1725 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=920 comm="/usr/sbin/console-kit-daemon))

I get this error when i run 'gksudo login-screen'

---

### Post by penn07 on 2011-04-10
> **moongya said:**
> hello ubuntu lovers

my prayer to you is to help me fix my ubuntu desktop.. it seems to suddenly haunted with invisible ghosts.. please excorsice (bad spelling). 

well it goes like this...my 2 month old ubuntu maverick installation was working wonderfully but all of a sudden while scrolling through an open office word document my mouse got possesed. started scrolling all over weirdly like it had a mind of it's own (A.I)

I saved the doc and rebooted (in 25 secs, am proud to reduce my boot time to 25 secs)

upon rebooting, i do not see any of my notification icons viz. network, bluetooth(yes i have bluetooth adapter) and missing others(which am unable to recollect now)

after reboot the mouse is still possesed.. 
also, am unable to un-install anything from ubuntu software center.. have tried apt-get update/upgrade/clean etc.. all structures are build correctly no issues there. just unable to uninstall anything from software center

then i tried to uninstall via snyaptic.. thankfully synaptic works as usual

then i tried to adminstration > user settings.. now here too i click on all buttons.. like uncheck the box which says do not required password for next login. but nothing happens..

is panel or gnome the culprit.. please help me

i love ubuntu and dont have (neither willing to pay) money to pay for windows.. 

and am s**t scared to re-install it.. that would be a nightmare

save me

while i get replies.. hopefully fast :) i will try this:
dpkg-reconfigure xserver-xorg
as suggested by other threads... lets c if my joy is restored by this
You need to eliminate the the possibility that its the OS, my advice would be to reinstall Ubuntu or another distro say Mint if the problem remains then it is probably a hardware issue.

---

### Post by pqwoerituytrueiwoq on 2011-04-10
out of curiosity what mouse do you have 
command:
*lsusb*

*gnome-mouse-properties* may have something useful
install anything just before this happened?

---

### Post by d3v1150m471c on 2011-04-10
> **moongya said:**
> 
Apr 11 00:16:36 ubuntu dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.33" (uid=1000 pid=1725 comm="nautilus) interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.6" (uid=0 pid=920 comm="/usr/sbin/console-kit-daemon))

I get this error when i run 'gksudo login-screen'

```

d3v11@d3v11m4ch1n3:~$ man login-screen
No manual entry for login-screen
d3v11@d3v11m4ch1n3:~$ login-screen --help
login-screen: command not found
d3v11@d3v11m4ch1n3:~$ login-screen
login-screen: command not found
d3v11@d3v11m4ch1n3:~$ login-screen
login-screen: command not found
d3v11@d3v11m4ch1n3:~$ 

```

`login-screen' is non-existent to the best of my knowledge. What are you trying to accomplish with that command?

---

### Post by moongya on 2011-04-11
I see login screen under system > administration
it lets you modify login parameters. may it's a package i installed.
also am unable to make any changes to system > administration > user settings, for example add or remove myself from a certain group.
please refer this image [screenshot]("https://2709750144308226791-a-amitlele-com-s-sites.googlegroups.com/a/amitlele.com/family/screenshotsa/Screenshot.png?attachauth=ANoY7cqzZSdMH-MKNVHFCD581rbuvY--GAm9MZja8Qkfc6TrSQDcXAaFVUz2DV8Oyc2MVaYlu3E_vAZY6x6SJaGkQqauTCuqot0i-10pTqlL-b3FH-tb1DMeDOO7-nxJBNm1bj0Wi68-I0Xttm8zJ9EvMFj5_vHMU1zhf0ztvEDddCtX8ZznaKiiLsa4dNRciXtlYXNfbuB2bOjrlNGMTo9gYwLxWFScBA%3D%3D&attredirects=0")
nothing happens when I click on these buttons..I just see a dialog 'starting administrative privileges', and thats it. nothing happens

another pain is I can not modify system > preferrence > appearance > visual effects
i select extra and i get pop the selected option is not available
weird cause both the above mentioned problems were non-existent couple of day before..
i even un-installed all packages installed prior to 2 days hoping that would restore my system...

---

