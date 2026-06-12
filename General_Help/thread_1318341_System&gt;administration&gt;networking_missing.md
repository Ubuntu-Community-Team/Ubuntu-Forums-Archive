---
title: "System&gt;administration&gt;networking missing"
date: 2009-11-07
forum: General Help
---

### Post by AceRB on 2009-11-07
I just did a fresh install of 9.10 and am trying to start network manager. The option isn't listed under administration although everything tells me it is currently installed.

What am I doing wrong? How do I start it?
 
Anyone have any ideas?

thanks!

---

### Post by wojox on 2009-11-07
It's not in the little tray applet in the top right?

---

### Post by NoVista on 2009-11-07
Right click on panel, add network manager, if you meant that.

Right click on Start Icon in panel, Edit Menus, then click on Administration in left pane, make sure Network Tools is checked in the right pane, if you meant this.

---

### Post by AceRB on 2009-11-07
> It's not in the little tray applet in the top right?

No it does not appear in the tray, nor when you look for networking under the **System>Administration** menu. There is a **Networking tools** option here, but that isn't what I want to set up my wireless.


> Right click on panel, add network manager, if you meant that.

Right click on Start Icon in panel, Edit Menus, then click on Administration in left pane, make sure Network Tools is checked in the right pane, if you meant this.


Ok, I am feeling really slow here but....
I am assuming the panel is the bar at the top and when I right click on it I see add to panel, delete this panel, new panel, etc. I don't see any way to add network manager here. And I am sorry to say that I don't know exactly what the start icon is; I assumed it would be obvious from your post. Is that missing too?

I appreciate the help and I am sorry I don't see what you are referring to. I am trying to start the utility to set up my wireless, got the driver installed and I am following step 1 from this guide:[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide), and the option is just not there.

> Open *System > Preferences > Network Configuration* - on Ubuntu 8.04 and later this should be *System > Administration > Network*.

---

### Post by mbeach on 2009-11-07
press Alt-F2 then type
```
nm-connection-editor
```
click 'Run'

does anything happen?

---

### Post by AceRB on 2009-11-07
Yes, I get a network connections window. Is this it?

I have a wireless tab but nothing in it. This doesn't seem to follow the document. If I go ahead and fill in the values here, is there a doc to follow? I have no idea where to find the mac address, or what he difference is between ssid and bssid.

thanks for the reply.

---

### Post by AceRB on 2009-11-07
I used ```
gnome-session-properties
``` to bring up the startup applications menu and found network manager listed, when I edit it the command field shows **nm-applet --sm-disable**.

Is this what it should say? Disable is very suspicious.

---

### Post by mbeach on 2009-11-07
who setup your wireless network - they should have the ssid, the security method.

if your ssid (the network name more or less) is broadcast, it should be listed in the Wireless tab. If not, you might have some issues with your wireless adapter.

A place to start:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

