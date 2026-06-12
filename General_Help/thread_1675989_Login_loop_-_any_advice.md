---
title: "Login loop - any advice"
date: 2011-01-26
forum: General Help
---

### Post by wulkenator on 2011-01-26
This is my 1st attempt at linux.  I installed Ubuntu 10.10 as it describes itself to be an easy install and detects most hardware.
 
Here is the problem that I have:
 
Process from boot:

[LIST=1]
[*]BIOS screen
[*]purple Ubuntu 10.10
[*]splash screen with short roll of drums
[*]**[COLOR=#ff0000]login[/COLOR]** screen < correct **[COLOR=#ff0000]login[/COLOR]**
[*]splash screen with long roll of drums
[*]brief glimpse of menu bar, then screen goes black
[*]loops back to#3 above
[/LIST]So i am able to login in safe mode and on occassion I am able to login to normal desktop mode.  Sometimes I during this loop I get a quick flash of the desktop before it goes back to step 3.
 
Sometimes (but very rarely) I am able to quickly click on the toolbar when the desktop flashes and I am able to get a normal login and desktop. On a few other very rare occassions it will load normally without any looping or requiring any quick clicks.
 
I'm hoping someone will be able to offer any advice.  I like Ubuntu and when it loads it works very well.
 
W

---

### Post by Rubi1200 on 2011-01-27
Hi and welcome to the forums :-)

What graphics card do you have installed?

---

### Post by SpadeIV on 2011-01-27
I had the same problem last week.
I somehow deleted the "ubuntu-desktop" package and therefore ended in a login loop.
Try starting up in safe mode, where you should be able to access the command line and check if you have the package installed. If not "sudo aptitude install ubuntu-desktop", then "startx" and everything should be fine again.

cheers

---

### Post by Rubi1200 on 2011-01-27
Aptitude no longer ships on the default installation (as far as I am aware), so you would need to install it first.

apt-get would also work.

If the > ubuntu-desktop package is missing as SpadeIV suggests. I would also run > sudo apt-get update as well.

---

### Post by smashsupermario on 2011-01-31
good mornig.
Saturday i upgrade to 10.10.
Then i try to install tethering  for iPhone from [http://www.xappsoftware.com/wordpress/2010/10/26/ubuntu-10-10-and-iphone-tethering-solved-updated/](http://www.xappsoftware.com/wordpress/2010/10/26/ubuntu-10-10-and-iphone-tethering-solved-updated/)
I reboot the system and the log in start to loop.
There is no choice for the session's type in the lower desk.
I can log in with terminal  session by alt+crt+F1.
I try to create a new account, but it doesn't work too.
i try to reinstall X-Server for my nvidia graphic card. but it continue to loop.
the file "messages" in /var/log is:
Kernel[655.346916] type=1400 audit (1296412227.390:21): apparmor="DENIED" operation="open" parent=2115 profiles="/usr/agate/gdm/guest-session/Xsession" name="/home/massimo/.profile" pid=2213 comm="Xsession" request_mask="r" fsuid=1000 pois 1000#-o
best regards Massimo.

---

