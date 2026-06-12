---
title: "disable popup notifications"
date: 2009-12-20
forum: General Help
---

### Post by Nevermore on 2009-12-20
I have some problems with my card in visualizing the notifications:
i see just a crushed black box.
I would like to completely disable those popup notifications
is there a way?
Thanks

---

### Post by howefield on 2009-12-20
Try opening a terminal and typing... (one command)

sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service
/usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled

---

### Post by TheOnlyMrK on 2009-12-20
I haven't tried this so I'm not sure but I think you could just delete it from start-up.
System - Preferences - Startup Applications - select "Indicator applet" and click Remove.

---

### Post by alexxroche on 2009-12-23
# I tried 
killall notification-daemon
ps auwxf|grep notification-daemon|grep -v grep # to see if it was still running
#[ 
killall -9 notification-daemon 
#or
kill -9 $(ps ux|grep notification-daemon |grep -v grep|awk '{print $2}')  
# for those really stubborn processes (try without -9 first!)
#]
#and when that seemed to work I did
sudo apt-get -y remove notification-daemon
#and I also did
sudo apt-get -y remove notify-osd pidgin-libnotify # but I don't think that last one is needed

---

