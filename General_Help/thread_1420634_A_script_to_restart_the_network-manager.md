---
title: "A script to restart the network-manager"
date: 2010-03-03
forum: General Help
---

### Post by iaculallad on 2010-03-03
I'm currently running Karmic on my laptop and I want to do something to this wireless connectivity (connection drops) problem that's bugging me everytime I leave my laptop turned on for the whole night.

I want a script which I can place on my cron so if it detects (like pinging google.com every 20 minutes) that there is no Internet connectivity it will tend to restart the network-manager and have it reconnected again without me interfering.

*The only solution I could do is to restart the laptop so I can be connected again, Logging out does not solve the problem either*

TIA.

---

### Post by spiderbatdad on 2010-03-03
well I tried the following and it worked for me...your results may vary:
```
#!/bin/bash

if eval "ping -c 1 www.google.com"; then
    exit
else 
sudo restart network-manager
fi
    exit
```
Obviously this script uses sudo and I ran it from /home/*, so it will be necessary to have it run as root without the use of sudo...or some other edit of sudoers file.

---

### Post by iaculallad on 2010-03-03
I'll try the script if it does it's purpose - Thanks.

---

### Post by iaculallad on 2010-03-04
We're almost there and here's a follow-through!

Waking up early this morning, I observed that I was again dropped from my connection last night. The script I placed on cron did not work because I was prompted with a window which asked my wireless security password, but after closing the said window and manually running the script - I was reconnected. I don't know if the script did the trick so I would like to know how I could kill the window process and add the code on the script below:

> #!/bin/bash

if eval "ping -c 1 www.google.com"; then
    exit
else 
sudo restart network-manager
fi
    exit 

Thanks again.

---

### Post by 2hot6ft2 on 2010-03-04
IF network manager is causing the problem have you considered disabling network manager in System > Preferences > Startup Applications
Seems it takes doing it a couple times for it to take for some reason.

And setting up your connection in /etc/network/interfaces
?
I have done it and I use WPA2 AES Personal for encryption. You can find more on how I did it here if interested.
[http://ubuntuforums.org/showthread.php?t=1418254&page=2](http://ubuntuforums.org/showthread.php?t=1418254&page=2)

The first page wouldn't help so that links to page 2 where I started setting that up.

---

### Post by iaculallad on 2010-03-05
I'll try to post an update whenever I'm prompted with the same password window. Surely terminal's ps would give the detail for me.

---

### Post by spiderbatdad on 2010-03-05
why not have wlan0 or wireless interface auto? Your keyring should store all your wireless passwords and auto connect.

---

### Post by dcstar on 2010-03-06
> **iaculallad said:**
> I'm currently running Karmic on my laptop and I want to do something to this wireless connectivity (connection drops) problem that's bugging me everytime I leave my laptop turned on for the whole night.
.......

Why not just find out what power management setting is shutting down the connection?

---

### Post by iaculallad on 2010-03-06
> **dcstar said:**
> Why not just find out what power management setting is shutting down the connection?

Actually it's not in the power management setting because I always leave my laptop turned on day-in and day-out. It only happens when our wireless connectivity gets choked because some users (all are connected wireless) abuse their use of P2P applications.

The reason why I wanted a script to autoconnect on our network's access point whenever I get dropped.

---

### Post by iaculallad on 2010-03-06
[CENTER][IMG]http://i48.tinypic.com/2zp2jab.jpg[/IMG][/CENTER]

This is the window which is interfering with the script, If only I know the name of this so I can kill it first before restarting the network-manager:

Does anyone know the name?

---

### Post by spiderbatdad on 2010-03-06
The wireless connection needs to have the keyring store the password and auto connect. So I'm not sure what the problem is...either your keyring password is not the same as your login password, or your wlan0 is not auto...for example the connection in Network Manager might be named Auto <connection> as shown in screen shot.

---

### Post by iaculallad on 2010-03-07
Thanks for following up Spiderbatdad. You see, the password for the wireless connectivity is already added on keyring as shown on the figure below and has the "auto" connection on nm-applet. I'm still wondering why it can't auto-reconnect me when I'm dropped of my wireless connection. Could I be missing something here or Keyring tends to forget my wireless password which I doubt because I could just click on the 'X' (close) on the windows asking for the password and manually run the script above and I get connected.

What could I be missing here? I really want to solve this problem as it had been bugging me for sometime now.

[CENTER][IMG]http://i48.tinypic.com/2n0twn8.jpg[/IMG][/CENTER]

---

### Post by spiderbatdad on 2010-03-07
in the screenshot above where the word "login" is in the keyring window...right click on that word and select change password from the menu. Change the password to match your user login password. Then disconnect from network and try the script.

---

### Post by iaculallad on 2010-03-10
I tried configuring seahorse (Accessories->Password and Encryption Keys) with my login password and still it incurs the same problem I've been dealing before. It still prompts me with the same password window whenever I got dropped from my wireless connection. After doing some trial-and-error methods, I've found a workaround which might be of help to someone encountering the same problem as I was before.

Using the same script above (executed by cron every 10 minutes), I added the command: killall NetworkManager, as shown below.

> #!/bin/bash

if eval "ping -c 1 www.google.com"; then
exit
else
**[COLOR="DarkRed"]killall NetworkManager [/COLOR]**
restart network-manager
fi
exit

With the script above, I get re-connected whenever I got dropped from the wireless connection. I don't know if this is an existing Karmic bug or is it just me experiencing this.

I posted the complete step-by-step process I did for this to work in this [site]("http://ianace.blogspot.com/2010/03/karmic-koala-ubuntu-910-wireless.html").

HTH.

---

