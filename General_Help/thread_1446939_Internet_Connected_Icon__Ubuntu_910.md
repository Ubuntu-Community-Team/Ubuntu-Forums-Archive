---
title: "Internet Connected Icon  Ubuntu 9:10"
date: 2010-04-04
forum: General Help
---

### Post by Dyffo on 2010-04-04
I have upgraded to  Ubuntu 9:10,- when I had Hardy Heron I had an Icon in the Launcher panel that told me when I was connected to the Internet. How can I configure this Icon for Karmic 9:10. My connection is direct to a Cable Router.At the moment my only way of establishing my connection status us by opening Evolution / Firefox or Skype to see if we are connected.

---

### Post by NightwishFan on 2010-04-05
Run this command, does the network manager appear?
```
nm-applet --sm-disable
```

If it shows up, then go to System -> Preferences -> Startup Applications. Create a new entry called Network Manager and make the command exactly as the one above. You can leave the comment blank if you want.

If not, run this command:
```
sudo aptitude install network-manager-gnome
```

If it reports this program is already installed, run this command:
```
sudo apt-get install --reinstall network-manager-gnome
```

Then reboot.

---

### Post by Dyffo on 2010-04-05
> **NightwishFan said:**
> Run this command, does the network manager appear?
```
nm-applet --sm-disable
```

If it shows up, then go to System -> Preferences -> Startup Applications. Create a new entry called Network Manager and make the command exactly as the one above. You can leave the comment blank if you want.

If not, run this command:
```
sudo aptitude install network-manager-gnome
```

If it reports this program is already installed, run this command:
```
sudo apt-get install --reinstall network-manager-gnome
```

Then reboot.

Thanks for this - when I enter  "nm-applet --sm-disable" into the terminal , then network manager appears. When I close the terminal of course this goes.

In Start up apps  I have Network Manager installed :with the correct command.I have also reinstalled. Problem is I still don't have Network manager appearing at start up.

---

### Post by xifer on 2010-04-05
Could be something else is installed that is taking over at startup.

Or do you have any manual config in /etc/network/interfaces file?

Might be an idea to try the alternative network manager - wicd

```

apt-get install wicd

```

---

### Post by Dyffo on 2010-04-05
> **xifer said:**
> Could be something else is installed that is taking over at startup.

Or do you have any manual config in /etc/network/interfaces file?

Might be an idea to try the alternative network manager - wicd

```

apt-get install wicd

```

This is getting crazy - I have installed wicd - this appears in the Start up apps but does not appear in the launcher.

---

### Post by NightwishFan on 2010-04-05
That is bizarre. I could only think the startup file is missing but it should create it. I will get back to you.

Perhaps try suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=1360695](http://ubuntuforums.org/showthread.php?t=1360695)

---

### Post by Dyffo on 2010-04-05
> **NightwishFan said:**
> That is bizarre. I could only think the startup file is missing but it should create it. I will get back to you.

Perhaps try suggestions in this thread:
[http://ubuntuforums.org/showthread.php?t=1360695](http://ubuntuforums.org/showthread.php?t=1360695)

Also got this problem - seems they might all be related to start up issues.

 Sound Problem on Karmic
I have an annoying problem with SOUND on my Karmic installation. Most times when I boot up or add/ Remove programes I have no sound. I find that if I check Sound preferences my Output Vol has gone to mute. This keeps on happening. This is not serious but annoying particularly when using Skype- any ideas of a solution.

---

### Post by NightwishFan on 2010-04-05
If the problems continue perhaps test if they are apparent on a live CD. As for the sound try running this command to sort out the volume.
```
alsamixer -c0
```

---

### Post by djoxyk on 2010-04-05
cable connection its network on eth0 + pppoe for internet, loaded on startup? if yes, wicd does not show if pppoe is connected, it show only network status (at least for me). And even if you will not have assigned network address you will have internet access so wicd is useless for cable.

you can use ifconfig in terminal to see if you have connection on ppp0. usually cable connection loaded on boot so basically you have it before you open firefox.
i use dsl-provider to manage connection sometimes and plog to see status of this manual connection.

---

### Post by Dyffo on 2010-04-06
Hi Guys - problem Solved- thanks for your support and suggestions.

The solution was :- when I boot up the opening screen when asking for Password offers 3 alternative start up modes.  Failsafe  Gnome - Gnome - or Term. I was using by default failsafe, but now have transfered to Gnome and thats it - problem solved.

---

### Post by NightwishFan on 2010-04-06
Ah, I was going to suggest that but I fell asleep before I got around to it. The same thing happened to me a while ago. I am glad it works for you!

---

