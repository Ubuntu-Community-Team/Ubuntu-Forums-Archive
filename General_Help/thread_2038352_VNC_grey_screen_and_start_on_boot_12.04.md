---
title: "VNC grey screen and start on boot 12.04"
date: 2012-08-06
forum: General Help
---

### Post by Siriss on 2012-08-06
I have 12.04 LTS installed and I am trying to get VNC to work. I want to be able to connect to existing sessions, and have it start on boot. I followed [this]("http://coddswallop.wordpress.com/2012/05/09/ubuntu-12-04-precise-pangolin-complete-vnc-server-setup/") guide and have left a comment to try and fix my problems but no dice. I have also tried all solutions I have found on google, including the one here, but I could not get it to work (I am missing something easy I am sure).

When I connect to the VNC session I get a grey screen with three checkboxes:

Accept clipboard from viewers Send clipboard to viewers Send primary selection to viewers

Here is my xstartup:


```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
gnome-session -session=gnome-classic &

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
```


I have also edited my to include:

```
/usr/bin/vncserver -geometry 1024x768
```

It does not start on boot, but when I run the command it starts, but I get the grey screen.

Any help would be greatly appreciated. Thank you!!

---

### Post by steeldriver on 2012-08-06
Have you tried setting the session name to ubuntu-2d? I think maybe 

```
gnome-session -session=gnome-classic
```is not recognized as a current session name - afaik any name you specify here has to correspond to an actual .session file in /usr/share/gnome-session/sessions, which on my 12.04 system appear to be gnome.session, ubuntu-2d.session or ubuntu.session

FYI there's a specimen .vnc/xstartup file here:

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

In my experience you need a 2d session because compiz breaks things otherwise - in your case it may be defaulting to a 3d / compiz session which is why you get the dead gray screen

---

### Post by Siriss on 2012-08-06
How is that different than my line below?

> gnome-session -session=gnome-classic &

Does the & specify the session and so it needs to be removed? Thank you for the suggestion, I am trying it now.

---

### Post by Siriss on 2012-08-06
That did not work. I removed the & and it still shows the grey screen with three check boxes. Thanks!

---

### Post by steeldriver on 2012-08-06
Hi I think you misread my post - I'm not suggesting replacing the command with the same command minus the &, I'm suggesting replacing the session by ubuntu-2d, i.e.

```
gnome-session **-session=ubuntu-2d &**
```

---

### Post by Siriss on 2012-08-06
I did misread it before. I tried that and I still get the grey screen with 3 check boxes. Thanks again for the help

---

### Post by steeldriver on 2012-08-06
OK sorry in that case I don't know

---

### Post by Toz on 2012-08-06
A couple of comments:

1. > [ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
Do you have an /etc/vnc/xstartup file, and if so, what are the contents?

2. Try moving:
> gnome-session -session=gnome-classic &
...to the end so that it is the last command in the file:
```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources

xsetroot -solid grey
vncconfig -iconic &

gnome-session -session=gnome-classic &
```

---

### Post by Siriss on 2012-08-06
I don't even have a /etc/vnc folder which is interesting. What should go in my /etc/vnc/xstartup file when I create it? Nice catch.

---

### Post by Toz on 2012-08-06
> **Siriss said:**
> I don't even have a /etc/vnc folder which is interesting. What should go in my /etc/vnc/xstartup file when I create it? Nice catch.

The line reads "if the executable file /etc/vnc/startup exists, then run it", but since one doesn't exist, its a redundant line. Did you try the second suggestion and did it work?

---

### Post by Siriss on 2012-08-06
I did try the second suggestion and it still shows the 3 check boxes. I have checked 750 permissions on ~/.vnc and made sure only one session is running. Stumped.

---

### Post by Toz on 2012-08-06
I believe a log file gets created in the .vnc directory. Can you post back the contents of that file?

Can you also post back the contents of your ~/.vnc/startup file?

---

### Post by Siriss on 2012-08-06
I posted the xstartup file at the beginning. I fixed the problem actually by going back to the original post i found to set it up. it should be 

gnome-session --session=gnome-classic &

notably the -- instead of the - i had in the original post. Apparently I was not the only one confused and the original poster corrected the mistake. Thank you for all your help!

---

### Post by steeldriver on 2012-08-06
doh! should've spotted that -- sorry :(

---

