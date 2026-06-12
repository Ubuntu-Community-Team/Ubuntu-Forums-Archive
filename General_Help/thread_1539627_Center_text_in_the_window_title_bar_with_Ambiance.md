---
title: "Center text in the window title bar with Ambiance"
date: 2010-07-26
forum: General Help
---

### Post by The Maxx on 2010-07-26
Hi, I was just wondering how I would go about centering the text in the title bar for the Ambiance theme. Currently it is on the left side after the buttons, but I want to center it in the middle of the bar. Does anyone know how I could accomplish this?

---

### Post by Unkuiri on 2010-12-21
Hi, There is a way to do this...:)...do this in terminal:
> cp -r /usr/share/themes/Ambiance/ /home/[your username]/.themes/
gedit /home/[your username]/.themes/Ambiance/metacity-1/metacity-theme-1.xml

go to the "<!-- Window Title -->" section, edit the "x=" and "y=" clearing them and adding "x="((3 `max` (width-title_width)) / 2)"" and "y="(((height - title_height) / 2)+1)"" in all of them.

it will look as follows:
> <!-- Window Title -->

<draw_ops name="draw_title_text_normal">
  <title color="#333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#dfd8c8"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>

</draw_ops>

<draw_ops name="draw_title_text_inactive">
  <title color="#333333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#333333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#333333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#333333"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
  <title color="#99958b"
         x="((3 `max` (width-title_width)) / 2)"
         y="(((height - title_height) / 2)+1)"/>
</draw_ops>

<draw_ops name="draw_title">

Save the file, log out and log in again to see the results...:)

Hope this helps

(P.S.:If anyone wants to put the buttons to the right I used for this the program ubuntu tweaks, but maybe there is a way to do this by editing the same xml file...)

---

