---
title: "Unable to login via graphic login screen"
date: 2011-07-11
forum: General Help
---

### Post by techiebiker on 2011-07-11
Don't know for sure how to explain. Have been using 64-bit Natty Narwhall since release. Logging in to Unity shell for at least a month.

Changed some packages, add/delete, with apt-get. My bad don't remember which ones. For some reason not finding the commands in .bash_history.

Now cannot log in via graphic login prompt. 
e.g. 
- turn computer on
- wait for prompt
- select my user name
- enter password

Login prompt goes away as in past, then screen all orange briefly, then white text on black scrolls too fast to read, back to all orange, back to login prompt.

Select any alternate session, Recovery Console, Ubuntu, Ubuntu Classic, etc. produces same result.

Alt+Ctrl+F1 at login screen and get text login prompt. Able to login there no problem.

Think it must be a graphics problem but don't know where to start. Have searched forums and tried a number of things found there. 
- Typing "startx" fails and reports /tmp/.X0-lock in use. Can't delete it because /tmp on drive is locked when I boot from thumb drive
- Typing "unity --repair" fails. Says no --repair parameter. Didn't want to try --reset parameter because it seems Unity is not only problem. No Gnome sessions will start either.

Home folder is encrypted and accessible when logging in at text login prompt.

Suggestions? Additional info needed?

Thanks.

---

### Post by wildmanne39 on 2011-07-11
Hi, reboot and choose recovery thin choose repair broken or missing packages.

---

### Post by techiebiker on 2011-07-11
Um... you mean choose "Recovery Console" session? Can't. Any session, including Recovery Console, selected from the session menu has same login behavior...
- orange screen
- white text on black screen scrolling too quickly to read
- orange screen
- back to login screen

Can recovery console be run from tty? If yes, what command invokes recovery console? Only hits for "recovery console" searching help.ubuntu.com were related to Windows dual boot, WiFi and GRUB.

Not a GRUB problem, is it? System boots and Alt+Ctrl+F1 gets terminal where login is successful.

Also no relevant hits searching "repair broken or missing packages" on ubuntuforums.org, help.ubuntu.com or general WWW search with Google. 

So, how to get Recovery Console session? It won't load via GDM same as other session options.

And, once in Recovery Console, what command to "repair missing or broken packages"?

Thanks.

---

### Post by techiebiker on 2011-07-11
New info...

press either shift key after BIOS message and GRUB menu appears

recovery is option on GRUB menu

with Ethernet (not WiFi) connected select and run recovery option

many packages updated

reboot

still same problem as original post

Unable to login via GDM regardless of session type selected.

What next?

---

### Post by wildmanne39 on 2011-07-12
Hi, you can have a look at this link it may allow you to boot so you can fix your problem if its a video driver issue and such,it would be a lot easier if we new what you added and deleted that started this problem.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by wildmanne39 on 2011-07-12
Hi, if that link does not work you can try this. Boot to recovery choose root prompt with network then type.
```
apt-get update && apt-get install ubuntu-desktop && apt-get upgrade
```
then reboot.

---

### Post by techiebiker on 2011-07-12
Boot is/has been working. 

With shift key now able to get to repair option. Running repair didn't work.

tried apt-get remove gdm && apt-get install gdm
didn't work

tried suggestions on uforums threads 1672145 and 1750548 didn't work or didn't have indicated files/directories

even creating new user, acct does appear on gdm user list, new user has same problem. login via gdm returns to gdm doesn't go into any session available on session menu however new user can login via tty!

cat ~/.xsession-errors for my user account and new user both contain
/etc/gdm/Xsession: Beginning session setup
.: 20: Can't open /usr/share/im-config/xinputrc.common

there is no im-config directory in /usr/share

Now thinking perhaps is X11 issue, not gdm issue? What package(s) to remove/install X11?

will try apt-get update && apt-get install ubuntu-desktop && apt-get upgrade

in the meantime

---

### Post by dino99 on 2011-07-12
then bypass the login stuff: 
from grub menu: select "recovery" mode then select "netboot"

you then will be root and be able to check synaptic, logs ...

---

### Post by techiebiker on 2011-07-12
will try synaptic and see if that gives me any clues.

Which logs? 
xorg.0.log comment line shows flags as (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

the only flags in the xorg.0.log are (WW) as follows...

[    26.190] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.190] 	Entry deleted from font path.
[    26.190] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.190] 	Entry deleted from font path.
[    26.190] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.190] 	Entry deleted from font path.
[    26.190] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.190] 	Entry deleted from font path.
[    26.190] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.190] 	Entry deleted from font path.
[    26.190] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins

---

### Post by techiebiker on 2011-07-12
synaptic wouldn't start Gtk-WARNING cannot open display

used aptitude to install the missing fonts. still can't get past gdm to desktop

---

### Post by wildmanne39 on 2011-07-12
Hi, did you try what I mentioned in post#6, it worked for another user last night and we had been trying for a week to fix her computer.

---

### Post by techiebiker on 2011-07-13
Thanks wildmanne39 I gave that a shot too. Didn't work either. :(

Finally decided to stop troubleshooting and just reinstall. Booting from my thumb drive and selecting "install" provided an option I hadn't realized was there...

Install Ubuntu 11.04 over 11.04 and preserve /home

Tried it. During install was prompted for user and password. Provided same user and password as was set up on my system already. Install completed as normal. And encrypted home folder was preserved too! No need to restore from backups.

Only thing needed has been reinstall a few apps. Basically those that aren't part of the standard install.

Still wish I knew what got borked so I'd learned a bit more rather than do reinstall. Enough time was spent without full use of computer though so went the green field route to get back to normal.

---

