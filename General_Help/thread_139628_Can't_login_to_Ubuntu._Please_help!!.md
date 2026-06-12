---
title: "Can't login to Ubuntu. Please help!!"
date: 2006-03-04
forum: General Help
---

### Post by cro.smiley on 2006-03-04
Ok, so my problem is a bit hard.

I had some problems with restarting xserver (ctrl+alt+backspace).
I was stuck with tty1 thing (you get it when you press ctrl+alt+f1).
And so i made a log in and then my experiment started:-?

I wanted to run GUI step by step.
I used these commands to create a default gnome interface:

```

xinit - I got a mouse and some kind of desktop
gnome-panel - This created both panels
gnome-settings-deamon - Everything looks nicer, and some icons appear
gnome-wm - This makes windows look normal with titel bar and everything

```

So, now i got everythig work great, except it all looked like default gnome look (like the first time I installed Ubuntu)

But things got much worst when I restarted computer.
After a log in screen i got the following error:

```

Your session only lasted less than 10 seconds.
 If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.
Try logging in with one of the fail safe sessions to see if you can fix this problem.
View details (/.xsession-errors file)

```

- I'm not out of space
When I click OK it returns me back to login screen.

Here is the xsession-errors file content:
```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "smiley"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/smiley:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/smiley:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/smiley:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:8130): WARNING **: Unable to read ICE authority file: /home/smiley/.ICEauthority

```

The only thing i can do is to login on failsafe console.
And then I repeat the procedure that i described above to get GUI.

I would like to login to my Ubuntu as before, but also I wouldn't like to reinstall it.
Please help me

---

### Post by cro.smiley on 2006-03-04
Thak you Google, you are my best friend :D 

So the answer is to change premissions of .ICEauthority file.

```

sudo chown yourusername ~/.ICEAuthority
sudo chmod 777 ./.ICEAuthority

```

Well, that was a nice adventure!

---

### Post by mattTheNewb on 2006-03-26
Worked like a charm!

(except ICEauthority is spelled with a small 'a').

Thanks!!

---

### Post by Krzysztof on 2006-03-29
Thanks man. That helped me too.

The question is wh y .ICEauthority was suddendly taken by root?
Anything I was doing was installing gdesklest and playing with some of them.

---

### Post by Zombiac82 on 2006-04-03
Great thank you so very very very much 
this worked great and I was able to log back in a remove the 
kubuntu desktop that I installed 

All I can say is this is my new home for ubuntu and linux, all 
other distros that I've tried failed on me but ubuntu is the first 
that worked and the last that'll be on my pc

---

### Post by Kropotkin on 2006-04-17
I am having the same problem at the moment, but the last line is slightly different:

```
$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:20.Xservers" -h "" -l ":20" "colin"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/cirrus:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/cirrus:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/cirrus:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco
SESSION_MANAGER=unix/cirrus:/tmp/.ICE-unix/10527

```

In my case, solution above doesn't help; the permissions were ok. Anyone have any ideas what is going wrong here?

---

### Post by mattTheNewb on 2006-04-26
Umm... that last line seems fishy. Try clearing your tmp folder.

---

### Post by Arjunanda on 2006-05-19
I am having the same issue after installing lots of stuff without reboot. I installed at least wine, winetool, winesetuptk, lot of dependencies, and what else? And after this,  login was not possible. Renamed .ICEauthority to .ICEauthority.bak, and I was able to log in, though my session and panel settings were gone. Now I am trying to revert back to the old .ICEauthority file to see if I get them back.

---

