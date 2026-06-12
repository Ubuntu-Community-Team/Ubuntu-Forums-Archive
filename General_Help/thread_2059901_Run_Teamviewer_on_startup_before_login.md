---
title: "Run Teamviewer on startup before login?"
date: 2012-09-19
forum: General Help
---

### Post by riahc3 on 2012-09-19
Hello

I would like Teamviewer to startup in Ubuntu even before I login so this way I always have remove access to the PC. How can I do this?

Thanks.

---

### Post by Quarkrad on 2012-09-19
I've done this a number of times.  The detail depends on the version of ubuntu you have.  Basically you need to launch a program called **Startup Applications**. In 12.04 launch the Dash and type in start - you will then see the **Startup Applications** icon.  Double click on it and you will see the list of apps that start on startup.  Press the add key and add Teamviewer in the name and command boxes.  Don't forget to put a tick in the box to the left of Teamviewer.  Restart on your own machine and see if it works.

---

### Post by Rokel on 2012-09-19
I'm not sure about teamviewer. With VNC there are many options: 

1. connect to existing session
2. start virtual desktop in the background (someone else keeps using other desktop on the foregroud)
3. connect to the gdm login screen.

VNC is maybe a bit harder to setup over unsecure and/or NAT'ed (behind router) networks. You probably want to use SSH tunneling for that.

---

