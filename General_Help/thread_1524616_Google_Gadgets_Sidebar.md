---
title: "Google Gadgets Sidebar"
date: 2010-07-05
forum: General Help
---

### Post by Vesko96 on 2010-07-05
Hi,

I just installed Google Gadgets from a tutorial on here (sorry, I can't remember who made it), and they work perfectly. Although, I do have a little aesthetic issue. The sidebar is solid grey, while I think I remember the Google Sidebar for Windows is transparent. IS there any way I can change the sidebar to be transparent? Thanks.

Also, a screenshot of how it looks right now:
[[IMG]http://img149.imageshack.us/img149/2022/googlegadgets.th.png[/IMG]]("http://img149.imageshack.us/i/googlegadgets.png/")

---

### Post by bug67 on 2010-07-16
Right click on the individual gadget and select "Undock from Sidebar."  Then, in the Google Gadgets menu, uncheck "Sidbar."  Place gadgets wherever.

---

### Post by diandal on 2010-07-24
Another question on same topic--

I too have installed the google gadget but everytime when i start my pc i have to start google gadget-

How can i have it to auto start when pc is switched on?

I have tried System-Preferences-Start up Applications-Add  but didnt understand what command to put in?

Sorry found answer few threads below- i know shouldv properly scanned forums first.

---

### Post by geezerone on 2011-01-21
Go to startup applications and use the command "ggl-gtk" which will auto-start for you :)

I still cannot make the solid grey sidebar transparent :(

---

### Post by geezerone on 2011-01-23
[This Link]("http://ubuntuforums.org/showthread.php?p=10389854#post10389854") helped me with removing solid grey sidebar and will also auto-start google gadgets.

In startup applications create one with the following command attributes:
[B]
sh -c "sleep 5 && ggl-gtk &"[/B]

---

