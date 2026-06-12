---
title: "Remote desktop"
date: 2011-12-08
forum: General Help
---

### Post by smartcard on 2011-12-08
How can I connect to my Lubuntu PC from a remote PC using VNC Viwer?  This was working by default in Ubuntu but not in Lubuntu.

---

### Post by bluexrider on 2011-12-08
> **smartcard said:**
> How can I connect to my Lubuntu PC from a remote PC using VNC Viwer?  This was working by default in Ubuntu but not in Lubuntu.
do you have a VNC Viewer client installed like Remmina if not use the software center and install one

---

### Post by smartcard on 2011-12-08
> **bluexrider said:**
> do you have a VNC Viewer client installed like Remmina if not use the software center and install one

The problem is not the vnc client, i have the client instead in my windows pc. I want to know if lububtu comes with vnc server installed like Ubuntu, if not then how to install it?

---

### Post by SteveDee on 2011-12-09
> **smartcard said:**
> ...I want to know if lububtu comes with vnc server installed like Ubuntu...

Not absolutely sure about 11.10, but vnc is not on earlier versions.

I install & use x11vnc then autostart during startup via a simple script.

These are my wiki notes:-
> 
**+++++Adding a Script to start VNC Server**
I just created a script like this:-
startvnc.sh
 #!/bin/sh
 x11vnc -forever -display :0

...then put it in /usr/bin (which is in the $PATH) and made it executable.
Then in autostart added:-
@startvnc.sh


Autostart refers to: /etc/xdg/lxsession/Lubuntu/autostart

---

### Post by smartcard on 2011-12-09
> **SteveDee said:**
> Not absolutely sure about 11.10, but vnc is not on earlier versions.

I install & use x11vnc then autostart during startup via a simple script.

These are my wiki notes:-


Autostart refers to: /etc/xdg/lxsession/Lubuntu/autostart

Thanks, when I tryied x11vnc -forever -display :0 I was promoting me to install, after installing it worked fine.

---

### Post by Artif on 2011-12-25
AFAIK after VNC authorisation VNC traffic is not protected. There are manuals in official Wiki on how to protect it via SSH.

1) Quick start for LUbuntu - [https://wiki.ubuntu.com/Lubuntu/RemoteDesktop](https://wiki.ubuntu.com/Lubuntu/RemoteDesktop)
2) VNC at all - [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)
3) VNC servers - [https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)
4) VNC clients - [https://help.ubuntu.com/community/VNC/Clients](https://help.ubuntu.com/community/VNC/Clients)

If one have small display on client, huge on remote and heavy loaded panels on remote, then may be there is a sense to use OpenBox with fbPanel (I do not know how to do it with Gnome). It will give you independent desktop space with it's own panels and their own sizes.

Approximate setup on "server" will be smth. like:
sudo apt-get install openbox fbpanel
Change gnome-session to openbox-session in ~/.vnc/xstartup - [https://help.ubuntu.com/community/VNC/Servers#Customising_your_session](https://help.ubuntu.com/community/VNC/Servers#Customising_your_session)
And add autolaunch for fbPanel in OpenBox:
mkdir -p "~/.config/openbox/"
 touch "~/.config/openbox/autostart.sh"
echo "" >> "~/.config/openbox/autostart.sh"
echo "fbpanel &" >> "~/.config/openbox/autostart.sh"

VNC server launch commands are here [https://help.ubuntu.com/community/VNC/Servers#Once_mode-1](https://help.ubuntu.com/community/VNC/Servers#Once_mode-1)

P.S. More about SSH - [https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
It can be used as 'ssh -XC [EMAIL="user@host.name"]user@host.name[/EMAIL]' - X-forwarder. And could be supplemented with the sshfs mounts of remote file systems. In such a case access is more smooth than VNC. Clipboard is shared, for example. But there will be some interference of local and remote Gnome on-the-run parameters.

---

