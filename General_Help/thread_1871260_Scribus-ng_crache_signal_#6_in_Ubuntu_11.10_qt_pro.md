---
title: "Scribus-ng crache signal #6 in Ubuntu 11.10 qt problem"
date: 2011-10-28
forum: General Help
---

### Post by neorg on 2011-10-28
Scribus craches and exit with Signal #6

After a update from Ubuntu 11.04 to 11.10 I can't use Scribus anymore. While starting scribus-ng crached with the message"

**Scribus crashes due to Signal #6**

After some search on Google I found  this on the Scribus support forum:* "I installed Qt 4 settings, set the gui style to Clearlooks and the same within Scribus' own preferences and I was overjoyed that it all worked as it should."* 
[forums.scribus.net/index.php/topic,268.0.html]("http://forums.scribus.net/index.php/topic,268.0.htm")

I changed Qt4 settings to Clearlook but still got the same problem. I can't set the same in scribus because of the fact that scribus crashes before I can do anything. 

I can start Scribus as root and than everything works fine: ```
sudo scribus-ng
``` Than I can change the preferences General -> Theme -> to Clearlooks.
Preferences files in /home/USER/.scribus are rewritten. (see timestamp)
After starting Scribus-ng again as a normal user still crach on Signal #6.

scribus-ng      1.4.0.dfsg~rc6-1 
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

Some solution would be great.

---

### Post by Ekhcsub on 2011-12-07
check [this]("http://ubuntuforums.org/showpost.php?p=11521156&postcount=4"), might help, after setting QT_ACCESSIBILITY=0 it worked like a charm

---

### Post by neorg on 2011-12-08
Thans for your reply.

Actually I solved the problem by doing a complete fresh install. (instead of a dist-upgrade).

Dist-upgrade is still a problem on Ubuntju :(

---

