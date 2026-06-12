---
title: "Network manager disappeared"
date: 2010-05-02
forum: General Help
---

### Post by Taak on 2010-05-02
I was setting up my internet connection in Ubuntu 10.04, while I had to reboot.
 
After the reboot Network icon in the top-right corner was disappeared! Really, I can't understand why...
 
These are the console lines I inserted **before** the reboot:
 
```
 
sudo pppoeconf
pon dsl-provider
plog
poff dsl-provider

```
 
I tried to open synaptic, totally remove network-manager and network-manager-gnome and then I tried to reinstall them. After the reboot, still, there wasn't Network icon.
 
I tried to press ALT+F2 and insert "nm-applet --sm-disable" but nothing happends.
 
I tried to right-click on upper-toolbar and then to go on "add panel" but I can't find out network manager (or similar).
 
If I write on my terminal "sudo nm-applet" it says that there's already an nm-applet running but where? And how can I open it?
 
On System/Administration/Network Tools (I don't know if this is the exactly translation...) all network parameters are 0 such us 0.0.0.0 on IPs. Of course internet connection does not work!
 
So my question is... How can I restore Network Manager? 
 
Thanks

---

### Post by spiky001 on 2010-05-02
I think the appelet is notification area

---

### Post by Taak on 2010-05-02
Sorry I don't understand... what should I do?

---

### Post by nitstorm on 2010-05-02
ubuntuforums.orgubuntuforums.org/showthread.php
ubuntuforums.orgubuntuforums.org/newreply.php
Try this. Install ubuntutweak and then open it up. In the startup tab in the auto start programs section there is Network Manager so add it. Next time you reboot it should probably show up at the right hand corner. The place where everything that you are running shows up as icons is called the notification area.

if you can see the volume icon but not the network manager icon try the above, but if you can't see it then you are probably missing a notification area on your taskbar thing. right-click on the panel, choose Add to panel and choose the Notification Area and add. Your missing icons should show up hopefully.

---

### Post by Taak on 2010-05-02
In my startup list there is already Network Manager. Should I try this however?

Edit: yes, I can see volume...

---

### Post by Taak on 2010-05-02
I have some problem to install Ubuntu Tweak without Network Manager... is it important?

I can't believe there isn't a way to fix it without install other software..

---

### Post by Taak on 2010-05-02
up...

---

### Post by Michl on 2010-05-03
My network manager icon is gone, but the manager works.
Also, adding the notification area doesn't fix this.
I did a clean install.

---

### Post by Taak on 2010-05-03
Still network manager doesn't work for me...

---

### Post by Roasted on 2010-05-03
Just upgraded to 10.04. Same issue.

EDIT - Just added notification area and sure enough it appeared...

Also - just make sure that you don't see a little tiny black divider in between the notification area vs another applet. When I was running the Release Candidate and this happened, my notification area was hidden by another applet, but I had to right click on the black divider in between and move it to the side to expose it. Just a thought.

---

### Post by Taak on 2010-05-03
I have battery level, volume and email in the top-right corner. There are 3 dots before them and nothing else.
 
However I don't think this problem is only about the icon because my internet connection doesn't work and I can't set my network parameters...
 
I think something is corrupted. Is there a way to totally restore Ubuntu 10.04 files and config files?

---

### Post by Taak on 2010-05-03
I tried this:
 
```
sudo /etc/init.d/networking restart
```
 
The result was:
 
```
"plugin rp-pppoe.so loaded. RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5"

```
 
And then I tried:
 
```
nm-applet
```
 
And the result was:
 
```
nm-applet is already running.
 
** (nm-applet:1767): WARNING **: <WARN> costructor(): Couldn't initialize the D-Bus manager."
```
 
Is this the problem?

---

### Post by Taak on 2010-05-03
I tried also this:
 
```
killall -9 nm-applet
sudo /etc/init.d/networking restart
nm-applet

```
 
and now the result is:
 
```
** (nm-applet:1755): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1755): DEBUG: old state indicates that this was not a disconnect 0

```
 
Really, I can't understand this...

---

### Post by Taak on 2010-05-03
Up!
 
I understand that maybe there isn't a way to fix it. So I would like to reset my installation. Is there a way to restore all original Ubuntu's files?

---

### Post by Taak on 2010-05-03
Ok, I have just discovered something new:
 
nm-applet is running but in the notification area his icon is a thin invisible line. If I click on it says:
 
"Cable connection
Disconnected (in gray - I can't click on it)
 
Wireless connection
Not managed / controlled (in gray - I can't click on it).
 
I would like that nm-applet controls my wirless connection!
 
How can I do?
 
Thank you

---

### Post by Taak on 2010-05-03
I tried this:
 
```
 
lspci -v | less

```
 
My wireless card is detected and it says that the kernel driver in use is "iwlagn".
 
However network manager still says "wireless connection not controlled"
 
Please, I really don't know how to start to solve this issue...

---

### Post by Taak on 2010-05-04
Fixed removing everything from /etc/network/interfaces and replacing it with:
 
```
 
auto lo
iface lo inet loopback

```
 
:popcorn:

---

### Post by xpluto on 2010-06-06
ty  
it's 2 weeks im searching net to solve this problem!

solved :guitar:

---

### Post by dkuhlman on 2010-06-08
> **Michl said:**
> My network manager icon is gone, but the manager works.
Also, adding the notification area doesn't fix this.
I did a clean install.

Check the file /etc/NetworkManager/nm-system-settings.conf

If it says:

```
managed=false
```

then change it to:

```
managed=true
```

You might need to reboot.

That worked for me.  Hope it helps you too.

- Dave

---

