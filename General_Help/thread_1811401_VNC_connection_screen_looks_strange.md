---
title: "VNC connection screen looks strange"
date: 2011-07-24
forum: General Help
---

### Post by Dr.iCe on 2011-07-24
[IMG]http://gyazo.com/bd334c5c033f3076b45772b20eae5899.png[/IMG]

That's how the VNC Viewer window looks like when connecting to the vncserver, what is wrong and how do I fix it?

---

### Post by Dr.iCe on 2011-07-24
after changing $HOME/.vnc/xstartup

to
```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &
unset SESSION_MANAGER
sh /etc/X11/xinit/xinitrc

```

the VNC Viewer now look like this:
[IMG]http://gyazo.com/5eb5e632d3220516b00fd5148e20e163.png[/IMG]


but still no Graphical Desktop Environment, anyone?

---

### Post by Dr.iCe on 2011-07-25
bump

---

### Post by Dr.iCe on 2011-07-25
another SHAMEFUL bump

---

### Post by stunet on 2011-07-25
have you tried using a different VNC viewer? I know i had that issue and switching viewers solved my problems :)

---

### Post by Azdour on 2011-07-26
Hi,

My xstartup looks like this:

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
gnome-session &

```

This works for me.

---

### Post by Dr.iCe on 2011-07-26
> **stunet said:**
> have you tried using a different VNC viewer? I know i had that issue and switching viewers solved my problems :)
well the server is down at the moment, the staff is working on getting it up but I will be sure to try that out when it's back up. hope that helps, thanks anyway

---

### Post by pAsM on 2011-07-26
Hello,
    Personally I am not a fan of VNC at all (Security reasons mainly). I would advise you try X Fowarding, IMHO it works better performance wise. This assumes you are running Linux on both ends.

ssh -X username@122.122.122.123

Once you are dropped into the shell, launch an application by typing its name (firefox for example). 


If you really need full remote desktops, Try NoMachine

---

### Post by Dr.iCe on 2011-07-26
> **pAsM said:**
> Hello,
    Personally I am not a fan of VNC at all (Security reasons mainly). I would advise you try X Fowarding, IMHO it works better performance wise. This assumes you are running Linux on both ends.

ssh -X username@122.122.122.123

Once you are dropped into the shell, launch an application by typing its name (firefox for example). 


If you really need full remote desktops, Try NoMachine

I am running Ubuntu Server 10.04 and Windows 7 Ultimate (running Windows for gaming etc.

---

### Post by Dr.iCe on 2011-07-26
i was wondering if the problem was that it says "Root's X Desktop" ?

---

### Post by Dr.iCe on 2011-07-26
bump

---

### Post by Azdour on 2011-07-27
Hi,

Are you using vnc4server?

Did you start vnc4server as root? If you did that's why I think you are seeing 'Root's X Desktop'. At a guess I think the xstartup it is reading is /root/.vnc/xstartup.

I typically ssh into the remote machine as the user I want to vnc in as. I then launch vnc4server as that user (I do not use sudo or anything like that).

vnc4server is then running with the xstartup located in /home/<username>/.vnc

---

### Post by Dr.iCe on 2011-07-27
> **Azdour said:**
> Hi,

Are you using vnc4server?

Did you start vnc4server as root? If you did that's why I think you are seeing 'Root's X Desktop'. At a guess I think the xstartup it is reading is /root/.vnc/xstartup.

I typically ssh into the remote machine as the user I want to vnc in as. I then launch vnc4server as that user (I do not use sudo or anything like that).

vnc4server is then running with the xstartup located in /home/<username>/.vnc
how do I create another user then root user? I only got SSH access, really need help here


EDIT: I created a new user, SSH into it and started VNCServer (without sudo or anything) but it still shows as the same (yes I edited the xstartup @ /home/<username>/.vnc to be EXACTLY like the one you posted (I am running Win7 on client and Ubuntu 10.04 Server on the server)

---

### Post by spiky001 on 2011-07-27
Correct me if i,m wrong but dose the server addition have a desktop to view on it I was lead to believe it was command line only

---

### Post by Azdour on 2011-07-28
Hi,

@spiky001 - That is a good point.

Without a desktop it will not be able to start a gnome-session which is why you could be seeing the grey screen.

---

### Post by Dr.iCe on 2011-07-28
tried installing desktop using:
```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

it installed and everything but still same problem, some configuration I need to do?

---

### Post by Azdour on 2011-07-28
Hi,

I'm running out of ideas.

As a sanity check is gnome-session installed on the server? It should be under /usr/bin - cannot see any reason why it would not be installed...

---

### Post by spiky001 on 2011-07-28
Is it possible to connect a monitor to see that the desktop is working.

---

### Post by Dr.iCe on 2011-07-28
> **Azdour said:**
> Hi,

I'm running out of ideas.

As a sanity check is gnome-session installed on the server? It should be under /usr/bin - cannot see any reason why it would not be installed...

there are no folder called gnome-session.
the folder which starts with gnome- in the /usr/bin are:

```
gnome-calculator
gnome-character-map
gnome-help
gnome-panel-screenshot
gnome-settings-daemon
gnome-text-editor
```


@ the other guy, the server is located in Germany, I live in Norway



**EDIT:** I did "apt-get install gnome-session" in SSH and it says gnome-session is already the newest version.. :S

---

### Post by Dr.iCe on 2011-07-29
bump

---

### Post by Dr.iCe on 2011-07-30
a VERY VERY shameful bump here, please guys

---

