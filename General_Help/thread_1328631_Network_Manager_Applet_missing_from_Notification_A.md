---
title: "Network Manager Applet missing from Notification Area"
date: 2009-11-16
forum: General Help
---

### Post by C!pheR on 2009-11-16
Hi all,

I don't know why this would happen but when I created a new user account in 9.10 it did not have all the icons I would usually expect to see in the Notification area. In fact, the only icon in the Notification Area is the Sound Preferences applet. The other user account has both this icon and the NetworkManager applet.

I've tried removing and readding the Notification Area and this has not worked. I've tried adding nm-applet to the panel but this did not work either.  I'm not really sure what to do next. Any ideas how I can get this to appear?

---

### Post by F-3000 on 2010-06-09
I'd be interested to hear a solve to this problem, as my girlfriend has NetworkManager Applet missing from the Notification area, and neither of us have any idea why. Applet itself is running, but it does not appear in the area. I've tried to dig out info about this, but so far nothing that would have helped.

-Logs say nothing.
-nm-applet is running all the time, as is NetworkManager.
-Ubuntu is 9.10 - from fresh install (not update from older).
-Restarting either does nothing.
-Notification Area itself seems to be working as supposed to.
-Hardly any changes to G/UI.

---

### Post by Louisraritan on 2010-06-09
Interesting, I am not having that problem.  Curious, if you log in your sudo or admin account and go to System, Amin, Users & Groups.  Highlight the offending user account and then click on advanced.  Do the Sudo Password thing.  Click User Privilege and see what is check and what isn't, are the Use Internet and Modem boxes checked?  Im still pretty new to Ubuntu and Linux so don't throw beans at me If I am way off.

---

### Post by dineshs on 2010-06-09
I think NM has issues when
1)nm-system-settings.conf says *managed=false*
To solve this
```
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
```
and set
```
managed=true
```
OR
2)/etc/network/interfaces contain anything other than
```
auto lo
iface lo inet loopback

```
To solve this comment other lines(or backup the file and edit it so that it contains only those lines)
Should restart the machine after doing this
Ref [http://wiki.debian.org/NetworkManager](http://wiki.debian.org/NetworkManager)
Note :Always backup files before editing

---

### Post by nyxm on 2010-06-09
I have this same problem myself. I am using 10.04 from cd. I had an icon to click on next to the volume button and now it is missing?

---

### Post by robot_chicken_parm on 2010-06-09
i am also having this problem.  i upgraded to lucid from 9.10 using update manager.  network manager applet will load somtimes  eventrually after 5 min or so, and sometimes it doesn't.

---

### Post by zbyszek on 2010-06-10
It is some miunderstanding with latest distributions of ubuntu and visibility of nm-applet. My advice is this: instal through Synaptic ->gnome-netstatus-applet.

---

### Post by puzzleclocks on 2010-06-13
I'm a pretty new user(since January) and had struggled with this issue in Karmic 9.10 and after browsing forums forever with nothing successfully solving my problem, gave up because I was still connecting to my home and school networks so I decided to wait for 10.04 and see if the upgrade would fix it.

It didn't and in tackling the problem again I'm running into the same issue: things that have worked for other people aren't working for me for some reason.

I had high hopes for the solution offered by dineshs after changing my nm-system-settings.conf   had "managed=false"  but changing it and rebooting still hasn't brought network manager back.

Also, in browsing the forums, I find that this has been a problem in several earlier versions of ubuntu before the one I got started on.  I'm wondering if this is a "known bug" or if something I did or am doing is likely to have caused this problem.

Thanks for anyone trying to help on this problem in any way.  This has become an interesting challenge for me to solve before I can go back to hitting wireless hot-spots around town! ](*,)

::edit:: also tried the netstatus-applet install suggested above and it doesn't seem to have any effect whatsoever.

---

### Post by lars-i on 2010-06-19
Hello everybody:

I had the same problem mentioned above.
Doing the things dineshs tells us it worked at my Ubuntu 10.4:

dineshs  	
Re: Network Manager Applet missing from Notification Area
I think NM has issues when
1)nm-system-settings.conf says managed=false
To solve this
Code:
gksudo gedit /etc/NetworkManager/nm-system-settings.conf
and set
Code:
managed=true


Thank you dineshs and to everybody else: don't give up :-)

With kind regards,
Lars

---

### Post by warfacegod on 2010-06-19
> **zbyszek said:**
> It is some miunderstanding with latest distributions of ubuntu and visibility of nm-applet. My advice is this: instal through Synaptic ->gnome-netstatus-applet.

If memory serves, the Net Status applet will only give you information regarding your connection. It won't/can't let you change networks, for example.

---

### Post by QwUo173Hy on 2010-06-26
What happens to me is that the first user to log on gets the applet icon, but subsequent users do not. So if I'm the first to log on to the computer, I get the icon. But if someone else has logged on and I switch from their account, I don't get it.

---

### Post by ilgaar on 2010-08-06
I have exactly the same problems as mentioned above. Although Network Manager Applet is installed, and the curious thing is that it is running, when I try to start it vi terminal, giving me this warning message:

[HTML]An instance of nm-applet is already running.

** (nm-applet:6226): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager[/HTML]

But the nm-manager is entirely missing, it's literally no where to be found, other than folder it is installed by default, I can't add it to Panel it is missing the too, it is missing in notification area, and what am i gonna do? any ideas?

I'm using Ubuntu 10.04 i386, and by the way I already tried changing the managed from false to true, but that doesn't help either.

[HTML]# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true[/HTML]

I also checked /etc/network/interfaces, but there is nothing unusual.

[HTML]auto lo
iface lo inet loopback[/HTML]

Maybe it is an issue with notification area!? I'm really stuck at this point

---

### Post by warfacegod on 2010-08-06
It's in Indicator Applet now.

---

### Post by schwascore on 2010-08-09
I had this problem when I did an upgrade from 9.10 to 10.4 without doing a clean install.

A dirty fix is to delete the hidden files/directories in your home directory. This removes some of the legacy configurations and settings left from the 9.10 install. After a restart, the network manager applet returned, along with several others that were missing in my case.

I have not narrowed down which file/directory contains the offending content yet. Someone with a bit more experience than me might be able to point us in the right direction.

If you use my "dirty" approach, please be careful! I am not posting the command here because I don't want anyone removing important hidden files without thinking it through first (.ssh keys, etc). **Make sure you know what you're deleting before you do this.**

---

