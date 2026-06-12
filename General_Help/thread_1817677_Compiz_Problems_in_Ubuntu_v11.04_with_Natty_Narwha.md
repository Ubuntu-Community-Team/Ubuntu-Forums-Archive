---
title: "Compiz Problems in Ubuntu v11.04 with Natty Narwhal"
date: 2011-08-03
forum: General Help
---

### Post by KirdanRocks on 2011-08-03
Hello dear Ubuntu Community

I just installed Ubuntu the day before yesterday, so I am a complete, and utter, newbie. I am using a guide for Ubuntu called "Ubuntu - Lær Det Selv" by Kim Ludvigsen. The guide is in my native language, danish. 

This book also features a guide to get the sweet desktop-workspace-rotating-cube-thing. This is done by installing CompizConfig Settings Manager, Compiz Fusion Icon and two packages with Synaptic called compiz-fusion-plugins-extra and compiz-fusion-extra, I think. 

My mission was set: Try to get the cube working to impress my family with the great advantages of Ubuntu. So i tried to activate Compiz Fusion Icon, but it didn't work. So I figured, "What could possible happen if I screwed around with CompizConfig Settings Manager?". Well, as I discovered, the unity-thing disappeared, and I can't run any applications, even with Alt+f2. Alt+F2 simply doesn't work. 

I tried to active the cube-thing through the menu of CompizConfig Settings Manager, but alot of different messages pop-upped. They were all concerning that I couldn't run some different plugins, deactivate Desktop Wall and that I had to run some plugins and applications to activate the cube-thing. (Something with OpenCL, i think) I thought, "What the heck?" and simply clicked what I deemed appropiate, since my guide did not have any data on these messages. And BOOM, my desktop was simply f***ed. 

I can't activate the unity-thing nor run applications, even through alt+F2. There is simply nothing on my desktop, only the wallpaper. The only thing i could do, was restarting my computer and start Ubuntu in failsafe-condition. Everything works fine in failsafe-condition. 

Please Help

Sincerely
KirdanRocks

---

### Post by dj722000 on 2011-08-03
If you are able to get to your terminal, type in this code:

unity --reset

Ya, the cube and unity doesn't get along. Something to do with Unity having certain things set with large desktop or something,I cant remember.
 However, if your really bent on using it, when your log in screen appears, click on your name, look down at the bottom of the screen and you will see where you can switch your desktop back to Ubuntu Classic. Then type in your password to log on.

You have to go out and look for a way to get the cube setup. I believe it will still work, just not the way we are use to it. Personally, I quit using Unity desktop as I dont much care for it and like I posted above I switched to Ubuntu Classic Gnome. desktop.

---

### Post by dj722000 on 2011-08-03
Wont guarantee it will work, but you can try these steps in trying to get it to work in unity.

[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/]("http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/")

---

### Post by wildmanne39 on 2011-08-03
Hi, here is how to get the terminal open so you can run unity reset, let it run for about three minutes then restart your computer.

Open a terminal by hitting ctrl+alt+t or alt+f2, if  one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. 
```
Unity --reset
```
These commands to reset all the settings in compiz.
```
gconftool-2 --recursive-unset /apps/compiz
gconftool-2 --recursive-unset /apps/compiz-1
gconftool-2 --recursive-unset /apps/compizconfig-1
```

Here is a guide for setting up the cube and effects in natty with pictures for every step.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by obie17 on 2011-08-03
if you cannot open the terminal before you login, login as "ubuntu (safe mode)" then try alt+F2 then type this command** unity --reset. **

---

### Post by KirdanRocks on 2011-08-07
Thanks for the help!

Ubuntu working again :)

---

### Post by wildmanne39 on 2011-08-07
Hi, your welcome, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

