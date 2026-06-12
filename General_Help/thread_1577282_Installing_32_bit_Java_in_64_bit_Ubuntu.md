---
title: "Installing 32 bit Java in 64 bit Ubuntu"
date: 2010-09-18
forum: General Help
---

### Post by AdamMPkins on 2010-09-18
I've been trying to use my work's SSL VPN. It uses Juniper Network Connect. I attempted setup from the VPN website and it would not install. As I later found out, this is due to the fact that it asks for the su password and Ubuntu doesn't use one.

I stumbled upon this link and script, which seems to be exactly what I'm looking for: [http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html). I tried to run the script and run network connect, but the script's setup needs a jre directory for 32 bit Java.

Is it possible to install 32bit java on a machine running a 64bit operating system? If so, How can I go about doing this?

---

### Post by dcstar on 2010-09-19
> **AdamMPkins said:**
> I've been trying to use my work's SSL VPN. It uses Juniper Network Connect. I attempted setup from the VPN website and it would not install. As I later found out, this is due to the fact that it asks for the su password and Ubuntu doesn't use one.

I stumbled upon this link and script, which seems to be exactly what I'm looking for: [http://mad-scientist.net/juniper.html](http://mad-scientist.net/juniper.html). I tried to run the script and run network connect, but the script's setup needs a jre directory for 32 bit Java.

Is it possible to install 32bit java on a machine running a 64bit operating system? If so, How can I go about doing this?

Those instructions have specific steps for 64-bit, why don't they work for you?

---

