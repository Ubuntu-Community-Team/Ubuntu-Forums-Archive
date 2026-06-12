---
title: "[CentOS 5] vncserver: geometry 1024.768 is invalid"
date: 2010-08-23
forum: General Help
---

### Post by pro511 on 2010-08-23
hello

i follow **[COLOR=DarkOrange][this steps ]("http://filesharefreak.com/tutorials/how-to-speed-test-your-seedbox/")[/COLOR]**to use remote desktop
but i get this message at last step 

Starting VNC server: 1:{_username_} vncserver: geometry 1024.768 is invalid
                                                           [[COLOR=Red]FAILED[/COLOR]]
..

how i can fix it ? 
i have vps 

***i removed my username and i replaced with **{_username_}

:)

---

### Post by pro511 on 2010-08-23
up

---

### Post by Toz on 2010-08-23
Please show the contents of your ~/.vnc/xstartup and /etc/sysconfig/vncservers file. Ensure that you have 1024x768 ( instead of 1024.768 ) listed.

/ToZ

---

### Post by pro511 on 2010-08-24
> ~/.vnc/xstartupfrom [COLOR=Red]root

[/COLOR]```
root@server.xxxx.com[~]# ~/.vnc/xstartup
xsetroot:  unable to open display ''
vncconfig: unable to open display ""
twm:  unable to open display ""
root@server.xxxxx.com[~]# Warning: This program is an suid-root program or is being run by the root user.
The full text of the error or warning message cannot be safely formatted
in this environment. You may get a more descriptive message by running the
program as a non-root user or by removing the suid bit on the executable.
xterm Xt error: Can't open display: %s
xterm:  DISPLAY is not set

```and from user 
```
-bash: /home/xxxxx/.vnc/xstartup: Permission denied

```

-----------------------------------

> /etc/sysconfig/vncserverssame msg from root and user

```
-bash: /etc/sysconfig/vncservers: Permission denied
```

---

### Post by itcotbtoemik on 2010-08-24
It's been quite a while since setuid was needed for xterm with
Linux, since Unix98 pty's were introduced.

---

### Post by Toz on 2010-08-24
Try:
as root:
   ls -l /etc/sysconfig/vncservers
and
   cat /etc/sysconfig/vncservers

as user:
   ls -l ~/.vnc/xstartup
and
   cat ~/.vnc/xstartup

/ToZ

---

### Post by pro511 on 2010-08-24
> **Toz said:**
> Try:
as root:
   ls -l /etc/sysconfig/vncservers
and
   cat /etc/sysconfig/vncservers

```
 -rw-r--r-- 1 root root 1015 Aug 23 12:10 /etc/sysconfig/vncservers
```and 
```

# The VNCSERVERS variable is a list of display:user pairs.
#
# Uncomment the lines below to start a VNC server on display :2
# as my 'myusername' (adjust this to your own).  You will also
# need to set a VNC password; run 'man vncpasswd' to see how
# to do that.
#
# DO NOT RUN THIS SERVICE if your local area network is
# untrusted!  For a secure way of using VNC, see
# <URL:http://www.uk.research.att.com/archive/vnc/sshvnc.html>.

# Use "-nolisten tcp" to prevent X connections to your VNC server via TCP.

# Use "-nohttpd" to prevent web-based VNC clients connecting.

# Use "-localhost" to prevent remote VNC clients connecting except when
# doing so through a secure tunnel.  See the "-via" option in the
# `man vncviewer' manual page.

# VNCSERVERS="2:myusername"
# VNCSERVERARGS[2]="-geometry 800x600 -nolisten tcp -nohttpd -localhost"

VNCSERVERS="1:**{username}**"
VNCSERVERARGS[1]="-geometry 1024.768 -depth 16"
VNCSERVERARGS[2]="-geometry 800.600 -depth 16"
VNCSERVERARGS[3]="-geometry 1024.768 -depth 16"

```> 
as user:
   ls -l ~/.vnc/xstartup
and
   cat ~/.vnc/xstartup
```

-rwxr--r-- 1 bin {username }368 Aug 23 11:44[COLOR=Lime]/home/{username}/.vnc/xstartup*[/COLOR]

```and
```
wing two lines for normal desktop:

    unset SESSION_MANAGER

    exec /etc/X11/xinit/xinitrc

    [ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup

    [ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources

    xsetroot -solid grey

    vncconfig -iconic &

    xterm -geometry 80.24+10+10 -ls -title "$VNCDESKTOP Desktop" &

    startx &

    exec gnome-session &

```:)

---

### Post by Toz on 2010-08-24
/etc/sysconfig/vncservers file is incorrect. The last 3 lines should read (note the 'x' in place of '.'):

VNCSERVERARGS[1]="-geometry 1024x768 -depth 16"
VNCSERVERARGS[2]="-geometry 800x600 -depth 16"
VNCSERVERARGS[3]="-geometry 1024x768 -depth 16"

Then restart the vncserver service via:
'service vncserver restart'

and see what you get.
/ToZ

---

### Post by pro511 on 2010-08-24
> **Toz said:**
> /etc/sysconfig/vncservers file is incorrect. The last 3 lines should read (note the 'x' in place of '.'):

VNCSERVERARGS[1]="-geometry 1024x768 -depth 16"
VNCSERVERARGS[2]="-geometry 800x600 -depth 16"
VNCSERVERARGS[3]="-geometry 1024x768 -depth 16"

Then restart the vncserver service via:
'service vncserver restart'

and see what you get.
/ToZ

greats :)

it work now 
thanks a lot :)

---

### Post by Toz on 2010-08-25
Glad I can help. Please mark the thread as solved.
/ToZ

---

