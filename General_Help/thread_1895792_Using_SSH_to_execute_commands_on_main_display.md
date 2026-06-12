---
title: "Using SSH to execute commands on main display"
date: 2011-12-15
forum: General Help
---

### Post by BlackWidower on 2011-12-15
I'm trying to find an efficient way to play multimedia on an Ubuntu Server I put together.

I have a display hooked up, but no keyboard, and have been accessing the machine through SSH and X11VNC.  So I **can** run VLC by starting an X11VNC server, connecting through a VNC viewer (using SSH tunnelling, obviously), and starting VLC the old fashioned way, then controling it though the HTTP interface.  I hate doing that.

I am looking for a simple command that can start VLC through SSH and have it run on the main display so I can see the video on the monitor and will stop getting errors.

I know there is an X11 forwarding function, but as far as I can tell, that's used to connect to an X11 server running client-side, not on the original machine; or at least, it doesn't work if you try to use it that way.

---

### Post by Lars Noodén on 2011-12-15
Set the [font=Courier New]DISPLAY[/font] variable on the remote server.  Then run VLC or another graphical application

```

export DISPLAY=:0.0
vlc

```

---

### Post by BlackWidower on 2011-12-15
Thanks a bunch, worked like a clock!  Though I wish I didn't need to enter it in each time.  Oh well, add it to the list.

---

### Post by Lars Noodén on 2011-12-15
Add it to [font=Courier New].bashrc[/font] and it will be there whenever you connect.

---

