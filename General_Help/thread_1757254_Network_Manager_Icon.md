---
title: "Network Manager Icon"
date: 2011-05-13
forum: General Help
---

### Post by jim_deadlock on 2011-05-13
I just installed a new wireless card and it's working fine but I'm wondering how to put the icon for it on the panel because nothing is showing at the moment.

---

### Post by lithopsian on 2011-05-13
indicator-network package?

---

### Post by natehall on 2011-05-13
I have a similar problem. Instead of a wireless symbol an extra speaker symbol appeared! I got rid of the wrong speaker one but I'd like my little wireless symbol back.( I'm afraid to shutdown and restart because I've had troubles getting online by wireless and at least that is working now!)

---

### Post by matt_symes on 2011-05-13
Hi

If nm applet running ? What response do you get in the terminal if you type

```
nm-applet --sm-disable
```

Kind regards

---

### Post by natehall on 2011-05-13
this is what i got:

** (nm-applet:8867): WARNING **: <WARN>  constructor(): Couldn't initialize the D-Bus manager.

---

### Post by matt_symes on 2011-05-13
Hi

I have not seen that message from network manager before and i am not sure if that means it's running or not. For a quick test copy and paste this into a terminal and post back the results.

```
ps aux | grep [n]m-applet
```What version of Ubuntu are you using ? I assume you have a notification area ?

Kind regards

---

### Post by jim_deadlock on 2011-05-13
That gives no results for me on Natty.

I do have Network Manager Applet installed (network-manager-gnome) and I'm running Ubuntu Classic so I think the icon should be showing but it's not.

---

### Post by matt_symes on 2011-05-13
Hi

@jim_deadlock. Does entering

```
nm-applet --sm-disable
```

into a terminal startup the applet. Was it the ps command that returned nothing ?

kind regards

---

### Post by jim_deadlock on 2011-05-13
Yes the ps command returned nothing.

```
nm-applet --sm-disable
** (nm-applet:3249): DEBUG: old state indicates that this was not a disconnect 0
^C** Message: Caught signal 2, shutting down...
```

Also see above, I have network-manager-gnome

---

### Post by natehall on 2011-05-14
This command :  ps aux | grep [n]m-applet
gives this output:
      1456  0.1  0.3  49544 11728 ?        S    10:26   0:00 nm-applet --sm-disable
I'm running 10.04 right now. (For some reason 10.10 ran slow on my computer and the latest version I downloaded of 11.04 was for servers!

---

### Post by natehall on 2011-05-14
It's fixed. I just right clicked on the panel, add to panel and added "Notification Area". I got the answer off an earlier post. Thanks for the help anyways.:)

---

### Post by jim_deadlock on 2011-05-15
When I add Notification Area nothing happens

---

### Post by matt_symes on 2011-05-15
Hi

@jim_deadlock[FONT=monospace]

[/FONT]> DEBUG: old state indicates that this was not a disconnect 0

Let's check your state file. Can you post the contents of...

```
cat /var/lib/NetworkManager/NetworkManager.state
```

Kind regards

---

### Post by jim_deadlock on 2011-05-15
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

```

---

### Post by matt_symes on 2011-05-15
Hi

> **jim_deadlock said:**
> ```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=false

```

Openn a terminal and type

```
sudo service network-manager stop
```Edit the file

```
sudo nano /var/lib/NetworkManager/NetworkManager.state
```Change WWANEnabled=false to WWANEnabled=true

Press ctrl + o to save and ctrl + x to exit.

Then type

```
sudo service network-manager start
```Hopefully that will work.

Kind regards

---

### Post by jim_deadlock on 2011-05-15
I did that, my connection is still fine but still no icon...

---

### Post by matt_symes on 2011-05-15
Hi

Can you post the output of 

```
cat /etc/network/interfaces
```and if you could also repost the output of

```
[FONT=monospace]cat [/FONT]/var/lib/NetworkManager/NetworkManager.state 
```

Kind regards

---

### Post by jim_deadlock on 2011-05-16
```
cat /etc/network/interfaces

auto lo
iface lo inet loopback

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by matt_symes on 2011-05-16
Hi

> **jim_deadlock said:**
> ```
cat /etc/network/interfaces

auto lo
iface lo inet loopback

cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

That looks all right as well. As you have a notification area it should be displaying. It's check the other files it might be.

Can you post the output of

```
cat /etc/NetworkManager/nm-system-settings.conf
```and 

```
cat /etc/xdg/autostart/nm-applet.desktop
```It might be worth having a look in ~/.xsession-errors

Can you start up nm-applet with (*****use ALT + F2  and not the terminal for the command*****)

```
nm-applet --sm-disable
```Give it a minute and the post the output of 

```
grep "nm-applet" ~/.xsession-errors
```Lets see if that tells us anything.

At the moment though i am scratching my head.

Kind regards

---

### Post by jim_deadlock on 2011-05-16
I don't have nm-system-settings.conf but I do have...

```
cat /etc/NetworkManager/NetworkManager.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

```

```
cat /etc/xdg/autostart/nm-applet.desktop
[Desktop Entry]
Name=Network Manager
Comment=Control your network connections
Icon=nm-device-wireless
Exec=nm-applet --sm-disable
Terminal=false
Type=Application
OnlyShowIn=GNOME;XFCE;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=NetworkManager
X-GNOME-Bugzilla-Component=general
X-GNOME-Autostart-enabled=true
X-Ubuntu-Gettext-Domain=nm-applet

```

I ran nm-applet --sm-disable with ALT+F2, nothing happened...

```
grep "nm-applet" ~/.xsession-errors
** (nm-applet:13900): DEBUG: old state indicates that this was not a disconnect 0

```

I appreciate all your help Matt, if you're out of ideas don't worry about it, it can remain a mystery, my connection works fine that's the main thing, this is only a minor irritation.

---

### Post by matt_symes on 2011-05-16
Hi

It seems they changed the name of the file from nm-system-settings.conf to NetworkManager.conf between 10.04 and 11.04.

Was this a fresh install or an upgrade ?

The files look fine though and there is no extra information in the debug log. I am at a bit of a loss here. If i come across a solution i will post it for you but at the moment.....

If it becomes a problem you could try using WICD. I used that connection manager under 10.10 and it worked well. Download the deb file from Ubuntu packages site. Purge Network Manager and install WICD.

Kind regards

---

### Post by jim_deadlock on 2011-05-16
It was an upgrade from Maverick. I think I'll just leave it as it is, I'd rather not risk breaking my connection in pursuit of an icon, thanks anyway :)

---

