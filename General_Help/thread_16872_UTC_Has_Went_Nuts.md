---
title: "UTC Has Went Nuts"
date: 2005-02-24
forum: General Help
---

### Post by Thanatos9602 on 2005-02-24
I searched & learned how to change it where UTC didn't come on on boot. Now whenever I boot, it may show the next morning or afternoon in the systray. Maybe even two or three days later. I hit set time & date & everything is correct. How can the settings show the correct time & date, but the tray show whatever the hell it wants to?? This one makes no logical sense at all. Can someone please help? Thanks for your time & trouble.[img]http://www.ubuntuforums.org/images/smilies/icon_confused.gif[/img]: [img]http://www.ubuntuforums.org/images/smilies/confused.gif[/img]

---

### Post by nocturn on 2005-02-25
[QUOTE=Thanatos9602]I searched & learned how to change it where UTC didn't come on on boot. Now whenever I boot, it may show the next morning or afternoon in the systray. Maybe even two or three days later. I hit set time & date & everything is correct. How can the settings show the correct time & date, but the tray show whatever the hell it wants to?? This one makes no logical sense at all. Can someone please help? Thanks for your time & trouble.[img]http://www.ubuntuforums.org/images/smilies/icon_confused.gif[/img]: [img]http://www.ubuntuforums.org/images/smilies/confused.gif[/img][/QUOTE]
 I think your system time and hardware time are out of sync.

In a terminal, check the output of:
date

and 
cat /proc/driver/rtc

---

### Post by Thanatos9602 on 2005-02-25
I went in & went to check it again before I ran your checks. Ends up, I hadn't turned off UTC in the systray clock. I turned it off in the boot-up controls, but never thought to turn it of in the tray. My mistake. I guess I'm still pretty much a noobie. Thanks for your time & trouble.:smile::-P

---

