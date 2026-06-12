---
title: "Help with Ubuntu-Desktop in a XenServer 6.0-based 10.04 VM"
date: 2011-11-18
forum: General Help
---

### Post by doriandeluca on 2011-11-18
[COLOR=#1F497D]This is a pretty specific request, and it's probably better suited for a Citrix forum somewhere, but I'm hoping that someone here has some insight that might help me.[/COLOR]
[COLOR=#1F497D]
[/COLOR]
[COLOR=#1F497D]I’ve been testing XenServer 6.0 on a test server in anticipation of rolling out several production VMs in our network.  My issue is with attempting to run Gnome Desktop on an Ubuntu Server 10.04 64-bit VM running on XenServer 6.0.  Based on some reading that I’ve done (most helpfully, [here]("http://forums.citrix.com/message.jspa?messageID=1488653")), I suspect that this cannot be done because, in this scenario, Xorg is looking for a physical graphics device that simply does not exist.  I hope I am wrong about this.[/COLOR]
  
  [COLOR=#1F497D]When I use the command *startx* while logged in as any user (including root), I am given the following error:[/COLOR]
  
```
Primary device is not PCI
  (EE) open /dev/fb0: No such file or directory
  (EE) No devices detected.
   
  Fatal server error:
  no screens found
   
  Please consult the The X.Org Foundation support 
   at [http://wiki.x.org]("http://wiki.x.org/")
  for help. 
  Please also check the log file at "/var/log/Xorg.0.log" for additional information.
   
  ddxSigGiveUp: Closing log
  giving up.
  xinit:  No such file or directory (errno 2):  unable to connect to X server
  xinit:  No such process (errno 3):  Server error.

```
  [COLOR=#1F497D]My question is, can Gnome Desktop be run in a XenServer virtual environment?  Can I configure the Xorg.conf file to use a virtual device rather than a hardware device?[/COLOR]


[COLOR=#1F497D]Thanks much for any help with this!
[/COLOR]

---

### Post by blueridgedog on 2011-11-18
I recommend you try and reconfigure the xserver to work with the new/different graphic card as reported by the server:

```
sudo dpkg-reconfigure xserver-xorg
```

You can also post in the citrix forum:

[http://forums.citrix.com/forum.jspa?forumID=503&start=0](http://forums.citrix.com/forum.jspa?forumID=503&start=0)

---

### Post by doriandeluca on 2011-11-21
> **blueridgedog said:**
> I recommend you try and reconfigure the xserver to work with the new/different graphic card as reported by the server:

```
sudo dpkg-reconfigure xserver-xorg
```You can also post in the citrix forum:

[http://forums.citrix.com/forum.jspa?forumID=503&start=0](http://forums.citrix.com/forum.jspa?forumID=503&start=0)

Gave that a shot, and it didn't work.

I'll try the Citrix forum.  Thanks for the help.

---

