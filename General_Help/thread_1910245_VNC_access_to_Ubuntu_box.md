---
title: "VNC access to Ubuntu box"
date: 2012-01-16
forum: General Help
---

### Post by serverpimp on 2012-01-16
Systems - Mac Mini running Lion Server & Ubuntu 11.10 Desktop

I am trying to manage a headless install of Ubuntu Desktop via my Mac Mini running Lion server.  The odd thing is I can connect and see the Ubuntu desktop via Chicken of VNC, JollyFastVNC, and RealVNC but can not appear to make keyboard or mouse actions.  Mac ScreenSharing launched from Finder just hangs.

I have two scenarios on the Ubuntu box I have tried with the same results.  I used the native Ubuntu 'Desktop Sharing' application and I have installed the 'X11vnc Server' application.  With both solutions and the VNC clients listed above on the Mac I can see the Ubuntu screen and move the mouse but can not type or take action with the mouse.  I have a temporary monitor on the Ubuntu Desktop and ironically I can see my actions (can type and click) of my Mac Mini mouse and keyboard.  So the Mac is able to control the Ubuntu box but I don't see the action on my Mac screen, only the mouse moving around.

I tried Chicken of VNC on wife's Mac Air (Lion) and experienced the same results.  

Any ideas of what to check/config?

---

### Post by serverpimp on 2012-01-17
Since the mouse and keyboare is showing up on the VNC target (Ubuntu box) is this a problem with the client image displaying initially and immediately not updating anymore?

---

### Post by krunge on 2012-01-17
Not sure if this is your problem, but try the "-noxdamage" cmdline option for x11vnc and see if that corrects the problem.  Search for "noxdamage+x11vnc" in these forums for more info.

---

