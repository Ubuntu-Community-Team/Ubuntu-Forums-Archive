---
title: "Help with X Remote Display Please - 3rd Request"
date: 2009-11-12
forum: General Help
---

### Post by subuta on 2009-11-12
Hello,

Since I upgraded my main Ubuntu host to 9.10:

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"

I am no longer able to display X applications running on other machines.  In the past I did this with xhost, but it no longer works:

 connect scapps1 port 6000: connection refused

I will also need to run X forwarding over SSH.  That too is is not working.  I have searched the web and fiddled with the various configuration settings, although I have not been able to change the setting in Gnome System->Administration-Login Screen ->Security because my login administration screen doesn't have any tabs(! - I haven't been able to find any help for that issue).

Note that my x server is starting with tcp nolisten turned on:

root      1422  1416  0 09:33 tty7     00:00:13 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-BpQqZZ/database -nolisten tcp vt7

I have not been able to change this regardless of the settings  in /etc/X11/xinit/xserverrc: 

$ more /etc/X11/xinit/xserverrc
#!/bin/sh

# $Id: xserverrc 189 2005-06-11 00:04:27Z branden $

#exec /usr/bin/X11/X -nolisten tcp
exec /usr/bin/X11/X

or in /etc/gdm/gdm.conf:

$ grep TCP /etc/gdm/gdm.conf
DisallowTCP=false


Thanks for your help.

-Dan

---

### Post by kjohri on 2009-11-12
Try this link

[http://www.softprayog.in/troubleshooting/linux/x-window-remote-display.shtml](http://www.softprayog.in/troubleshooting/linux/x-window-remote-display.shtml)

---

### Post by sainth on 2009-11-12
It used to be you could use the gdmsetup GUI to make the change, but it seems with 9.10 you have to do it manually. Only two things need to be done.

First add to /etc/gdm/custom.conf:
```
[security]
DisallowTCP=false
```

Then restart GDM:
```
sudo /etc/init.d/gdm restart
```

You should be able to open a terminal and run:
```
ssh -X (REMOTE)
```

And then run any X application which should display on your local desktop.

---

### Post by subuta on 2009-11-13
Hi Kjhori and Sainth,

Thank you both very much for your replies.  Although the problem is not yet resolved, I sincerely appreciate your efforts.

Kjhori, I had already taken the steps recommended in the "X Forwarding" section of the excellent article for which you sent a link.

Sainth, I was full of optimism when I saw your suggestion but, unfortunately it has not resolved the problem.

The situation is still this:

If I try to run an xterm from a terminal on another machine with DISPLAY set to my 9.10 machine's display I get "Can't open display scapps:0.0"  This is a procedure that I used routinely prior to the upgrade.

If I use ssh -X (or Y) from my 9.10 machine to another host, then try to run an xterm I get the same error.  If I unset the value of DISPLAY in the ssh shell before I try to run xterm then I get 

$ xterm
xterm Xt error: Can't open display: 
xterm:  DISPLAY is not set

I note that the x server on my 9.10 machine is still started with nolisten tcp:

root      1446  1435  1 07:41 tty7     00:00:30 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-rveJrz/database -nolisten tcp vt7

which I think would prevent the xhost method from working but not the x forwarding.

So it seems that the formerly reliable xhost capability is lost, and I am unable to activate the new (to me) X forwarding feature of ssh.

If you have any additional suggestions I would be most grateful.

-Dan

---

### Post by pvravi on 2009-11-18
Bump. I need this functionality as well.

---

### Post by JBAlaska on 2009-11-18
Did you update your ssh key after you upgraded to 9.10?

---

### Post by Giblet5 on 2009-11-18
Are you setting a DISPLAY variable out of .bashrc on the remote system? Don't do that. It will break ssh's X11-Forward capability.

Do an ssh -X to open an interactive shell on the remote and enter ```
echo $DISPLAY
```

If it says anything other than ```
localhost:10.0
```
then you broke it. Find where you're defining your broken DISPLAY variable and remove it.

A workaround that will make it work "your way" is to open a terminal on the local machine and enter: ```
xhost +
```

Now, anyone in the world can connect to your X server. Including me.

No, click the other button. Yes! Now enter your password. Wow, "password" is a really bad password. I'll be right back after I [strike]empty your bank account[/strike] get some coffee.



Pro tip:

Add entries to your ~/.ssh/config file like ```
Host websrv
  ForwardX11 yes
Host larry
  ForwardX11 yes
Host curly
  ForwardX11 yes
Host mo
  ForwardX11 yes
```

And you can do stuff like ```
ssh curly amarok
``` and blow curly's eardrums with Celine Dionne music.

---

### Post by subuta on 2009-11-19
Resolved!

Sainth, I went back and reviewed my work and found that I had made a mistake when trying to follow your advice.  I corrected my error and now the problem is resolved.

As near as I can tell, the upgrade to 9.10 resets X/GDM(?) to disallow X clients from other hosts.  It also appears to have removed the tab from the Security admin program that would have allowed me to set it back.  Sainth's suggestion of adding DisallowTCP=false to the custom.conf file (see his/her post for correct syntax and filename) fixes the problem.

Many thanks to all who tried to help out.

-Dan

---

### Post by mountmike on 2010-10-13
I had the same problem and [sainth]("http://ubuntuforums.org/member.php?u=954045")'s response solved it for me.

Thanks!

---

### Post by rickyrockrat on 2010-11-16
I just posted this, which should take you step-by-step.

[http://ubuntuforums.org/showthread.php?t=1623135](http://ubuntuforums.org/showthread.php?t=1623135)

---

### Post by pricetech on 2010-11-16
In the process of trying the tutorial.

---

### Post by pricetech on 2010-11-16
Still fails.  When I try to start the X server I get:

```

--
no protocol specified

```

Over and over again until it gives up.

---

### Post by rickyrockrat on 2010-12-12
You are not looking for remote X client, you are looking for a whole desktop - that's what you are trying to do with the startX.

Use vncserver on the remote and vncviewer on local.
They are 

tightvncserver
xtightvncviewer
in apt.

---

