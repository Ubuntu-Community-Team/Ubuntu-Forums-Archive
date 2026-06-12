---
title: "Cinnamon Desktop Icon Label Text"
date: 2012-09-19
forum: General Help
---

### Post by Mr Nemo on 2012-09-19
I just downloaded cinnamon 1.6. It works fine so far, but the text color on the desktop for the icons is too light and i can hardly see it. I'm pretty sure it changed when switching over to nemo file manager. Is there anyway i can change the color for the label text? Google hasn't yielded anything so far.

---

### Post by Dave Gravox on 2012-09-19
Ditto.

I've also got 1.6 and looking to change the text colour.

---

### Post by vaibhav on 2012-09-19
+1

---

### Post by belipowa on 2012-09-19
I observed that changing GTK theme the text color changes, so tried gnome-color-chooser without results.

Regards.

---

### Post by mustanggt408 on 2012-09-19
Bump...I'd also really like to know this. I have been searching for the solution on and off all day and everything I find seems to be antiquated.

---

### Post by Mr Nemo on 2012-09-19
I've had one successful attempt at changing the icon text on the desktop. I changed a color configuration in the /usr/share/themes/Ambiance/gtk-3.0/gtk.css file. (I'm using Ambiance, I noticed that changing to certain themes will change the desktop text color. I got to this specific file by reading through a series of webpages, can't really remember how though) Changing bg_color or text_color to black yielded white text for me for the desktop icons, but turned the backgrounds of my windows black where i couldn't even see icons within the windows. Not to sure if this is helpful at all, but maybe it will help someone more skilled than me come up with a solution.

---

### Post by Hazzabin on 2012-09-19
G'day mate, I've just changed my 'Theme' to 'Zukitwo-Dusk' and got clear white readable text and icons with an almost transparent background......oh yeah and I use top panel

regards
Hazz

---

### Post by Mr Nemo on 2012-09-19
Thanks for the reply Hazzabin. I'm trying out that theme now, but I still really like to know how to fix the Ambiance theme. Mostly for educational purposes.

EDIT: That theme did the trick, and it looks really nice too. Thanks again. I'd still like to know why the text changes when using nemo though.

---

### Post by mustanggt408 on 2012-09-19
Can one of you guys throw up a link to the Zukitwo-Dusk theme? I have found the Zukitwo but not the Dusk variant. I've been comparing the CSS files for the ambiance theme and TraditionalOKClassic to try to find the css controlling the desktop but nothing seems to work.

---

### Post by Mr Nemo on 2012-09-19
[http://karashata.deviantart.com/art/Zukitwo-Colors-310434222](http://karashata.deviantart.com/art/Zukitwo-Colors-310434222)

Here is the link for the themes, there are a few in a zip. I believe Hazzabin was actually referring to the zukitwo-dust theme. I haven't been able to find dusk.

---

### Post by mustanggt408 on 2012-09-20
Yes that's what I was thinking also I found the Dust but couldn't find Dusk. Changing to the Dust theme still didn't change my desktop font from the grey it is to anything else.

---

### Post by Mr Nemo on 2012-09-20
Strange. As I was changing to random themes I noticed some of them worked and some didn't. My only advice to you at the moment is to keep downloading and trying different themes. I'm going to continue to look into the problem.  Also, where did you install the new themes?

---

### Post by mustanggt408 on 2012-09-21
I tried in the full /usr path and also in my home directory in .themes. The themes show up, they just don't always change things like they're supposed to. My guess is the themes I've got are being over ridden by another variable. /shrug

---

### Post by mustanggt408 on 2012-09-21
I finally figured it out when I noticed that my Nautilus add on scripts weren't loaded. I had been ignoring it since I accidentally updated Cinnamon yesterday. The deal is they are using the Nemo fork now so none of the old GTK Nautilus themes are compatible with Nemo.
[http://www.fandigital.com/2012/08/zoncolor-elegant-theme-your-own-color.html](http://www.fandigital.com/2012/08/zoncolor-elegant-theme-your-own-color.html)

This is what I ended up using to fix it. It was one of those duh moments lol!!!

---

