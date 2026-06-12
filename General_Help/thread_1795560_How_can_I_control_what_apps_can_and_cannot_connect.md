---
title: "How can I control what apps can and cannot connect to internet?"
date: 2011-07-02
forum: General Help
---

### Post by chazinams on 2011-07-02
Using lsof I noticed that everytime I open some apps (like Rhythmbox or Banshee) it connects to the internet over ports 80 and 443. All I'm doing though is surveying my music collection. Why is it connecting to the internet for this? I don't have podcasts or album covers or any of that stuff set. In fact I turned all that stuff off.

the problem is that I only get so much bandwidth on my mobile broadband plan. I don't want apps connecting when I don't need them to. 

I played around with the UFW but it appears to only allow port configuration. I can't see how to control the connections of applications. I can't block ports 80 and 443 because then I'd shut down the web browser. How do Linux users control the internet connections of installed applications? 

this is a major issue for me because I'm concerned its going to eat up all my broadband allotment unnecessarily.

---

### Post by chazinams on 2011-07-03
Anyone?

---

### Post by mikejonesey on 2011-07-03
ip tables, to make the config super easy, install webmin, deb file availible from their website (it's a web server management control panel but you can use it to configure ip tables then uninstall it again...)

once installed use firefox to goto [https://localhost:10000](https://localhost:10000) and goto networking and select firewall, then u can easily add rules to block whatever you want...

---

### Post by chazinams on 2011-07-04
> **mikejonesey said:**
> ip tables, to make the config super easy, install webmin, deb file availible from their website (it's a web server management control panel but you can use it to configure ip tables then uninstall it again...)

once installed use firefox to goto [https://localhost:10000](https://localhost:10000) and goto networking and select firewall, then u can easily add rules to block whatever you want...

Just to make sure, I can control whether or not applications can connect to the internet using Webmin?

It's not immediately apparent to me how I can set Webmin to control an Application's internet connections.

---

### Post by Larkspur on 2011-07-04
For Banshee, go to Edit>Preferences and tick the box marked "Disable Extensions Requiring Internet Access" or suchlike and see if that works.  I'm sure Rhythmbox has something similar.

---

### Post by Mud.Knee.Havoc on 2011-07-04
Maybe [this]("http://www.debian-administration.org/article/120/Application_level_firewalling") is what you're looking for? I imagine that it's the same thing that Webmin will get you (without the Webmin gui).

EDIT: I'd like to mention that I've never tried this before and wasn't even aware that you could use iptables to block *applications* (not just particular ports used by various applications - which won't help you if it's going over port 80!).  However, it seems that the instructions given in the link should work for any packets from the "commands" or applications you choose.

---

### Post by chazinams on 2011-07-07
> **Mud.Knee.Havoc said:**
> Maybe [this]("http://www.debian-administration.org/article/120/Application_level_firewalling") is what you're looking for? I imagine that it's the same thing that Webmin will get you (without the Webmin gui).

EDIT: I'd like to mention that I've never tried this before and wasn't even aware that you could use iptables to block *applications* (not just particular ports used by various applications - which won't help you if it's going over port 80!).  However, it seems that the instructions given in the link should work for any packets from the "commands" or applications you choose.

Hey, thanks for this. I'm not sure I can really use it because I'm not great with computers and am heavily dependent on GUIs. But I'll try studying IPTables on my off time and see if I can understand it enough.

Anybody know a program that offers these functions with a GUI?

---

### Post by mastablasta on 2011-07-07
gufw: [http://gufw.tuxfamily.org/](http://gufw.tuxfamily.org/)
 
it's in the repositories
 
also i think webmin is/was "abandoned".

---

### Post by srisharan on 2011-07-07
Disable the banshee extension for internet access

---

