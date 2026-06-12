---
title: "Keep getting prompted for my wifi password"
date: 2012-07-28
forum: General Help
---

### Post by Mazate on 2012-07-28
Howdy

Everytime I turn on my computer I get prompted for my wifi password.  What can I do to get it to keep it so that it doesn't keep asking?

---

### Post by Scott Goodgame on 2012-07-28
Right click on the Network Manager icon in the tray Click Edit Connections
Click on the Wireless tab.
Click on your wireless network.
Click the Edit button
Click the  "Available to all users" &  "Connect automatically" boxes.
Next time you shouldn't be asked.

---

### Post by Mazate on 2012-07-28
> **Scott Goodgame said:**
> Right click on the Network Manager icon in the tray Click Edit Connections
Click on the Wireless tab.
Click on your wireless network.
Click the Edit button
Click the  "Available to all users" &  "Connect automatically" boxes.
Next time you shouldn't be asked.

The "Available to all users" box isn't highlighted so I can't click it.

---

### Post by Scott Goodgame on 2012-07-28
You already have the info filled (SSID, etc...) right?

---

### Post by Mazate on 2012-07-28
> **Scott Goodgame said:**
> You already have the info filled (SSID, etc...) right?

Yes, and I have the mode set to infrastructure and the MTU is set to automatic.  (Whatever those are.)

---

### Post by Scott Goodgame on 2012-07-28
I googled around a bit and there seem to have been quite a few problems with network manager in 11.10 (I have wireless built in, but use wired so I never noticed) I know this is sorta a workaround, but how about removing network manager and installing wicd instead? I usually do that anyways just out of habit I guess.
 sudo apt-get remove network-manager
 sudo apt-get install wicd

Wicd will ask you to add a user to a group, highlight your user and press space, then enter to ok it.
Then you can just add wicd to your startup applications.

I hope this helps...

---

### Post by Mazate on 2012-07-28
> **Scott Goodgame said:**
> I googled around a bit and there seem to have been quite a few problems with network manager in 11.10 (I have wireless built in, but use wired so I never noticed) I know this is sorta a workaround, but how about removing network manager and installing wicd instead? I usually do that anyways just out of habit I guess.
 sudo apt-get remove network-manager
 sudo apt-get install wicd

Wicd will ask you to add a user to a group, highlight your user and press space, then enter to ok it.
Then you can just add wicd to your startup applications.

I hope this helps...

Thanks.  I need to update my signature since all of it is wrong now.  I'm actually using 12.04.

---

### Post by Scott Goodgame on 2012-07-28
Just shooting from the hip here, but worth a try, what if you kill network manager with sudo pkill -9 nm-applet  ... then run gksudo nm-applet ??
Mabey.. but it won't hurt anything...

---

