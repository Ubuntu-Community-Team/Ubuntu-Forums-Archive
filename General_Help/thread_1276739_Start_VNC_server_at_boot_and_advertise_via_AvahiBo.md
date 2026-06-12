---
title: "Start VNC server at boot and advertise via Avahi/Bonjour"
date: 2009-09-27
forum: General Help
---

### Post by mikealtieri on 2009-09-27
I have a problem that I believe is two separate issues:


1.  I would like to start a VNC server at the login screen.

The way Remote Desktop is currently set up, you must perform a local login before you can access the machine.  I have wake-on-LAN set up, so I would like to be able to remotely turn on the machine and then VNC into the standard login window.

2. I would like to advertise this VNC server under Avahi/Bonjour.

I connect to the Ubuntu machine via a MacBook Pro running Snow Leopard.  Right now, when Remote Desktop is running on the Ubuntu box it shows up in the Bonjour network devices on my Mac.  This is an excellent and easy way to connect, and I'd love to keep the configuration.



Any suggestions? I've installed tightvncserver, but I don't know how to configure it properly/start it at boot.  I also have Avahi up and running, and advertising AFP file-sharing as per this how-to: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

Thank you very much!

~Mike

---

### Post by maxbaldwin on 2009-09-27
Hmm... as far as VNC on startup, you should be able to do it by doing this:

```
sudo echo 'xtightvncserver' >> /etc/rc.local
```

Note that that's a systemwide thing. So, if you have two users, both would be able to do this. If it works.

```
sudo echo 'xtightvncserver' >> ~/.profile
```

This would make it so that it is run when you log in.

Also of note, the 'xtightvncserver' command may not be correct, but it's the closest thing I could remember to how to start it...

EDIT: also, don't think that you really need to configure too much on the vncserver. And I have no idea about the Avahi problem.

---

### Post by juancarlospaco on 2009-09-27
You can login via SSH and then use X redirect to use GUI.


example:
ssh -X remote-user@remote-ip gnome-panel

---

### Post by bodhi.zazen on 2009-09-27
The default VNC server in Ubuntu is vino and it is a shared VNX / X session.

Use another VNC server, vnc4server or FreeNX.

You should be able to configure them under System -> Services or via boot / init scripts .

In terms of avahi, should be running out of the box, append ".local" to your server host name.

vnc hostname.local

---

