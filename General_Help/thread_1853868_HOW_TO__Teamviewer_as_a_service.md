---
title: "HOW TO:  Teamviewer as a service"
date: 2011-10-03
forum: General Help
---

### Post by scorp123 on 2011-10-03
I just stumbled over this thread here:
[http://ubuntuforums.org/showthread.php?t=1471247](http://ubuntuforums.org/showthread.php?t=1471247)

... and I am a little surprised that the thread got closed "just like that". Necromancing? Oh come on. If the thread is like 5 years old or something and whatever was asked doesn't apply anymore to modern distributions... But that thread was just slightly over a year old and the question was never answered. And it's still relevant: Teamviewer for Ubuntu is still around, and people might want to run it as service ...


**_So here is my solution to the problem:_**


[LIST]
[*]We'll use ***/etc/rc.local*** to automagically start VNC for us at boot time
[/LIST]

[LIST]
[*]We'll then use VNC to automatically start Teamviewer for us once the virtual desktop has loaded
[/LIST]

**So the order is:**

We boot => boot process executes ***/etc/rc.local*** => ***/etc/rc.local*** triggers VNC => VNC launches Teamviewer ...


Here is what you need to make it happen:

[LIST]
[*]You need to get the newest *.deb package from here:
[http://www.teamviewer.com/en/download/](http://www.teamviewer.com/en/download/)
[/LIST]
[LIST]
[*]You need a desktop environment of some sorts on your Linux system: XFCE, Gnome, KDE, LXDE ...  (I personally have GNOME + LXDE on the same system)
[/LIST]
[LIST]
[*]You need a VNC server of some sorts, e.g. VNC4:
```
 sudo apt-get install vnc4server
```
[/LIST]
[LIST]
[*]You need a user account that you can use for this, e.g. ***"tviewer"*** (any user account will do; just **_don't_** use *"root"* please!!)
[/LIST]


Example from my system - my ***/etc/rc.local***:
```
 #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#

[B]# Launch VNC session for user tviewer
/bin/su - tviewer -c "/usr/bin/vnc4server :1 -depth 16 -geometry 1200x768"
[/B]
# By default this script does nothing.
exit 0 
```

What happens up there is that the ***"su"*** binary triggers a VNC4 server process. The part ***"su - tviewer"*** will make sure that whatever gets triggered, gets triggered as the user *"tviewer"* (and not as root!). The part ***"-c /usr/bin..... "*** defines which command needs to be executed on behalf of the defined user. The rest that follows are VNC parameters, e.g. I define that I want a color depth of 16-bit and that a screen resolution of 1200x768 is what I want (you can make up resolutions here).

To make sure VNC does the right things we need to manipulate the VNC launch scripts.

So the user account we use up there -- in this case *"tviewer"* -- needs to have this config file in his home directory:

**/home/tviewer/.vnc/xstartup**
```

#!/bin/sh
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -nowin &
/opt/teamviewer/teamviewer/6/bin/teamviewer &
lxsession &

```

What happens up there is that when this user triggers VNC (... or it gets triggered for him as we do via /etc/rc.local ...) the Teamviewer binary gets launched and then a virtual LXDE session is triggered (giving the binary we just launched window controls, etc.). And no: You can't do it in the other order. You have to do it in this order!! First launch the GUI programs, and only then launch the window manager.

To make sure you can access VNC you have to give it a password:
```
 su - tviewer
vnc4passwd

```

So ... Time to test it:

1.) do not reboot. Become "root" (e.g. via using ***"sudo"***) and then copy and paste the line from ***/etc/rc.local*** and try it out ... does it work as intended?

2.) Once you're sure that invoking the command manually works as intended you can try and see if it works when rebooting: reboot your system ... once it's up and running again Teamviewer should be running.


Taddaaaa ... Teamviewer as a service :D

I know, I know: You could set your GDM to auto-login and then have Teamviewer automatically loaded upon the start of your auto-login session. But I personally don't like the idea of an auto-login session being visible on the physical screen (so anyone who walks into the room can see what is happening and e.g. start fooling around ...?). So that's why I prefer VNC to give me a virtual desktop session that is not visible on the physical screen.

---

### Post by Jacuro on 2012-09-10
I have been reading alot about "Teamviewer as a service"

I have two shops, both with ubuntu, and need to remotely controll them both.

The easyest way to run Teamviewer on STARTUP is to do the following: First Configure the teamviewer client that people can not shut it down when running and add needed passwords and Co. so the id / pass wont change on bootup.

The go to -> System -> preferences and find the boot on start 
there you just add this:

Name:    Teamviewer
command:/opt/teamviewer/teamviewer/6/bin/teamviewer

Done you are

---

