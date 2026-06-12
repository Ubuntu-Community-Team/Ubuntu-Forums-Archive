---
title: "Conky Wireless Info Not Displaying"
date: 2010-11-07
forum: General Help
---

### Post by ctparmenter on 2010-11-07
I'm trying to display Wi-Fi network info using Conky. I've got it to display the IP address and the upload/download speeds, but for some reason it won't display the network SSID or wireless signal strength. Here's the relevant portion of my conky configuration:

Wi-Fi:
**Network: ${wireless_essid eth1}**
**Signal Strength: ${wireless_link_qual_perc eth1}%**
IP address: ${addr eth1}
Download Speed: ${downspeedf eth1} Kb/sec
Upload Speed: ${upspeedf eth1} Kb/sec

I appreciate any and all help. It's not the most frustrating problem in the world, but I've been unable to figure out the solution myself after several hours of perusing previous similar problems with Conky configs.

---

### Post by Quackers on 2010-11-07
Welcome to UF :-)
My wireless network is called wlan0 - eth is usually for ethernet as far as I'm aware. Here is the relevant section in my conky (but no ssid for mine)

```
${font Terminus:style=bold:size=11}WIRELESS NETWORK $hr
Connection Quality: $alignr ${wireless_link_qual wlan0}%
D/L: ${downspeed wlan0}/s $alignr ${totaldown wlan0}
U/L: ${upspeed wlan0}/s $alignr ${totalup wlan0}
```

---

### Post by ctparmenter on 2010-11-07
Thanks, Quackers. I was surprised that my connection was "eth1" as well, but when I click Connection Information, that's what it tells me is the type of connection. The thing is it works for half of the variables and not the other half. I've tried substituting "wlan0", "ath0", and even "eth0" in for "eth1" to no avail.

---

### Post by Quackers on 2010-11-07
That does seem odd. Can you right-click on your wifi network icon and select "connection information" and post a screenshot of the opened window please? You will need to click on New Reply for that and upload an attachment.

---

### Post by ctparmenter on 2010-11-07
Here's the screen shot.

---

### Post by Quackers on 2010-11-07
Thanks for that, it does seem odd. 
The problem is that I don't think conky has a variable for ethernet connection quality (because it is always 100% with a cable) and I suspect that conky thinks that's what you're asking for. Do you see my point?

---

### Post by ctparmenter on 2010-11-07
Yeah, I get you. Is there anyway to alter the connection type? That may be a really dumb question. Haha. I mean, if I can't get it to display this info, it's obviously not the end of the world and my system will run fine regardless.

---

### Post by Quackers on 2010-11-07
The truth is, I don't know. My wireless was named wlan0 by default. Maybe try a search here or go to the Networking & wireless forum and ask. Or Google. Maybe somebody else will see this and come up with an answer.

---

### Post by Quackers on 2010-11-07
Maybe you could try setting up a new wireless network?

---

### Post by ctparmenter on 2010-11-07
Perhaps. I'll google it and see what comes up. Thanks for your help, Quackers.

---

### Post by Quackers on 2010-11-07
Ok, let us know? Good luck :-)
Did you try setting up a new wireless network?

---

### Post by laserbeam on 2010-12-23
I'm using wireless on eth1 too (weird driver... I know), but getting that signal info should be possible, I mean that wireless icon gets it from somewhere. Would it be possible to run some external script to find it from the same source the wireless icon does? I'm asking because I have no idea where the icon gets it from.

PS. I'm not sure how that networking applet is called, that's why I'm referring to it as "the icon".

---

