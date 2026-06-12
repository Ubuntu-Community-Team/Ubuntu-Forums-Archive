---
title: "Activate wifi at startup"
date: 2011-03-02
forum: General Help
---

### Post by Cheryl J. Jones on 2011-03-02
Hello, 

Is there any way to automatically activate the wifi at system startup without using the keyboard switch?

I have tried this script in gedit, saved as .run and added to startup applications but it doesn't work: 

dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set stringrg.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true




thanks

---

### Post by daniel_andrei on 2011-03-02
Hello! Do you want that when ubuntu opens, to run automatically your wifi? Does you bluetooth manager starts automatically?

---

### Post by gandaran on 2011-03-02
> **Cheryl J. Jones said:**
> Hello, 

Is there any way to automatically activate the wifi at system startup without using the keyboard switch?

I have tried this script in gedit, saved as .run and added to startup applications but it doesn't work: 

dbus-send --system --type=method_call --dest=org.freedesktop.NetworkManager /org/freedesktop/NetworkManager org.freedesktop.DBus.Properties.Set stringrg.freedesktop.NetworkManager string:WirelessEnabled variant:boolean:true




thanks
if you mark the connect automatically box in the network manager » wireless tab » wireless setup doesn't this work?

---

### Post by cybergalvez on 2011-03-02
use wicd it will do what you want

---

