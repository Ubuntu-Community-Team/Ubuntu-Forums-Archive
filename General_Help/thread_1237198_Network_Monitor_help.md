---
title: "Network Monitor help"
date: 2009-08-11
forum: General Help
---

### Post by karthick87 on 2009-08-11
I am using ubuntu 9.04 and i have installed Network Monitor 2.26.0,and now i like to change this applet icon..Which file i have to edit to do this,Thanks in advance..

---

### Post by shiva.n on 2009-08-11
You should find it in /usr/share/icons/gnome or something like that.
 
Find nm-applet.desktop (Im on my work PC now, and dont remember the exact path), and you can change the icon in it.
 
Anyone know of groovy network icons with a handdrawn look?

---

### Post by karthick87 on 2009-08-11
Inside this path /usr/share/icons/gnome i found these directories having the folder name 8*8,16*16,22*22,24*24,32*32,48*48,scalable,index.theme..Which file i have to edit??Pls help i want to applet for  Network Monitor..

---

### Post by shiva.n on 2009-08-11
Depends on what icon theme you are using.

My /etc/xdg/autostart/nm-applet.desktop has Icon=nm-device-wireless

I use Tangerine icon theme. So I have

/usr/share/icons/Tangerine/scalable/status/nm-device-wireless.svg
/usr/share/icons/Tangerine/16x16/status/nm-device-wireless.png
/usr/share/icons/Tangerine/32x32/status/nm-device-wireless.png
/usr/share/icons/Tangerine/24x24/status/nm-device-wireless.png

---

### Post by karthick87 on 2009-08-12
I am using Clearlooks theme..But i cant find Clearlooks folder in /ur/share/icons/

---

### Post by shiva.n on 2009-08-12
Try looking in /usr/share/icons or /usr/share/pixmap

Or better 'man find'...

---

### Post by karthick87 on 2009-08-12
S i found and replaced the icons,but now my applet is not working..I have attached my screenshot below

---

### Post by shiva.n on 2009-08-12
mm I was trying to figure this out myself couple of days back when you posted. I was successfully able to change my nm-applet icon. Not on my laptop at the moment, but I will post exact details and screenshot later today.
 
Did you reboot? The icon change required a reboot for me. If it still doesnt work, it means you havent changed the correct icon file. Do you have any icons in ~/.icons ? 
 
I think any icons in you ~/.icons folder will override the ones in /usr/share/*. I am not too sure of this though...

---

### Post by karthick87 on 2009-08-12
I have customized my icons to Tangerine and as you said i have replaced the icons in /usr/share/icons/Tangerine...Now everything works fine for me thank you so much!:P

---

### Post by shiva.n on 2009-08-13
Glad it worked. But Im thinking theres got to be an easier way of doing this. Anyone?

---

### Post by karthick87 on 2009-08-13
Similarly how to add new icon packages??

---

### Post by shiva.n on 2009-08-13
Assuming you are using Gnome, or running gnome-settings-daemon, 

Extract your fonts to ~./icons and, 

Gnome Control Center -> Appearance -> Theme Tab -> Customize -> Icons Tab -> Choose your icon theme

---

### Post by karthick87 on 2009-08-14
Thank you once again.!

---

