---
title: "Xbox 360 Connection"
date: 2010-02-02
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2010-02-02
Wasn't sure where to put this, so sorry to the moderators in advance :P.   I'm trying to use my wireless laptop as a &quot;gateway&quot; between my wireless router (at the other side of the house) and my xbox 360 (in my room) so that I can connect to xbox live.  Okay so I've spent hours reading online and trying different things, but nothing seems to work.  However by fluke I've managed to get the xbox live connection test to succeed on the network stage (right clicked on the wireless icon on the taskbar and changed the ethernet and wireless to shared to computer). The only problem with this is that i then lose internet connectivity on my laptop until I change the wireless setting back (which is a minor irritation compared to $100 for the wireless adapter from Ms).  Anyway when I get to stage 2 (connection to internet) it comes up with a DNS error saying something like couldn't resolve the hosts xbox.com and xboxlive or whatever.   I have tried changing my primary DNS to manual and to auto, with no success. I don't appear to have a secondary DNS, so when attempting manual I used the same as the primary.  Still the error comes up.  Can anyone please suggest a way to get this to work?   Thanks in advance.

---

### Post by marshmallow1304 on 2010-02-02
Set your IPv4 settings for your wireless connection to "Automatic (DHCP)" or whatever you need to set it to for it to work.  Set your IPv4 settings for your wired connection to "Shared to other computers".

---

### Post by Dalek Draco ON LINUX on 2010-02-02
> **marshmallow1304 said:**
> Set your IPv4 settings for your wireless connection to &quot;Automatic (DHCP)&quot; or whatever you need to set it to for it to work.  Set your IPv4 settings for your wired connection to &quot;Shared to other computers&quot;.

  The only way I seem to be able to get the connection to the network on the xbox is to change both to shared to other computes.   I'm okay with that I can change it back when I want to use the internet on my laptop, but I fall down at the next hurdle, DNS (says it can't connect).

---

### Post by Dalek Draco ON LINUX on 2010-02-02
BUMP  Anyone got any ideas? I've spent ages using different guides, and either I'm doing something really simple wrong or I've missed something :P

---

### Post by marshmallow1304 on 2010-02-02
> **Dalek Draco ON LINUX said:**
> The only way I seem to be able to get the connection to the network on the xbox is to change both to shared to other computes.   I'm okay with that I can change it back when I want to use the internet on my laptop, but I fall down at the next hurdle, DNS (says it can't connect).

But if you set your wireless connection to Shared, your laptop won't actually be connected to your router, and thus you'll get DNS errors because the only thing the XBox can connect to is the laptop.

You might also try [this guide]("http://ubuntuforums.org/showthread.php?t=508145"), even though it's a couple years old.

---

