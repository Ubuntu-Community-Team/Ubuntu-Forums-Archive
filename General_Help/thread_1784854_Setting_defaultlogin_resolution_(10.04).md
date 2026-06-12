---
title: "Setting default/login resolution (10.04)"
date: 2011-06-17
forum: General Help
---

### Post by PenguinLust on 2011-06-17
When my system starts it has what I think is too high a resolution for  my monitor (didn't think that was possible w/modern PnP!) How do I set  it to the resolution I want for the login screen? All the advice I get  sends me to /etc/X11/xorg.conf but there isn't one.
I'm running Ubuntu 10.04.

---

### Post by ajgreeny on 2011-06-17
You could try installing **startup-manager** and playing with the resolution in that.

It is not as useful a package as it used to be but still can make a difference to the settings of the things you asked about

---

### Post by pqwoerituytrueiwoq on 2011-06-17
if you are using nvidia graphics card
alt+f2
gksudo nvidia-settings
look at my attachment
then click "save to x configuration file"

---

### Post by PenguinLust on 2011-06-18
Actually, it's **startupmanager** (amazing how Ubuntu is about spelling mistakes). It didn't work. When I ran it, it told me that that there was an error and gave me these details:
> Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
Then on the "Boot Options" tab it told me that the "Display" resolution is 640x480, which it obviously isn't. Setting it to 1280x1024 didn't change anything.

It's not nVidia. Here's what I get from an lspci -v:
> 05:07.0 VGA compatible controller: XGI Technology Inc. (eXtreme Graphics Innovation) Z7/Z9 (XG20 core)
        Subsystem: Dell Device 01ae
        Flags: 66MHz, medium devsel
        BIST result: 00
        Memory at fc000000 (32-bit, prefetchable) [size=32M]
        Memory at fe6c0000 (32-bit, non-prefetchable) [size=256K]
        I/O ports at d880 [size=128]
        Expansion ROM at fe600000 [disabled] [size=64K]
        Capabilities: <access denied>
        Kernel modules: sisfb


---

### Post by Enigmapond on 2011-06-18
Try this app. Grub Customizer. Really works good for what you  are doing...

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update && sudo apt-get install grub-customizer
```

Hope this helps.

---

### Post by PenguinLust on 2011-06-19
I've tried that, too, now and it makes no difference.
I don't think these grub-based attempts are working, because the problem is not with grub it's with the login screen. I need a way to just prevent the card from going into these toxic video modes before my monitor blows up.

---

