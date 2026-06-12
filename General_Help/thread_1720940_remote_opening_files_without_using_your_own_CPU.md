---
title: "remote opening files without using your own CPU?"
date: 2011-04-03
forum: General Help
---

### Post by princeofnam on 2011-04-03
I have a laptop that's not up to par with opening 1080p video.  I do however have a PC that can.  I've connected my laptop to my TV as a media center.  I can remotely access files from the PC to play but because the laptop's resources are being used to play it I still encounter some slowdown.  Is there any way to remote access the other PC while using its resources to play the video?

---

### Post by blueridgedog on 2011-04-03
You could play the video on your desktop, then use VNC to connect to and view the desktop via the laptop.

Alternatively, if the desktop is running Linux, you could export the display to the laptop.

```
export DISPLAY=IPADDRESSOFLAPTOP:0.0
```

Then, in the same terminal, run your movie with the player of your choice.

Alternatively, you could export the display of a particular program:

```
vlc -display IPADDRESSOFLAPTOP:0.0
```

You will need to tell your laptop to accept the display:

```
xhost +IPADDRESSOFDESKTO
```P

---

### Post by princeofnam on 2011-04-16
i'm not sure if i did something wrong. i exported and then it simply said that the desktop IP was being exported to the contact list with no display.

---

### Post by princeofnam on 2011-04-16
I ended up trying the VNC viewer with Remote Desktop Viewer on my laptop.  It was incredibly slow.  Is that how it usually is?

---

### Post by blueridgedog on 2011-04-16
I would use the export method (first example) and get it working with a simple application first (xcalc or gedit for example) then move on to the movie player of your choice.  

Post your export command and the resulting output so we can see why it is not working.

---

### Post by princeofnam on 2011-04-17
how should expect the exported video to appear after xhost IPADDRESS.  automatically?

---

### Post by blueridgedog on 2011-04-17
If you issue the xhost command allowing the remote IP to display graphically on the local machine, it should appear automatically.

---

