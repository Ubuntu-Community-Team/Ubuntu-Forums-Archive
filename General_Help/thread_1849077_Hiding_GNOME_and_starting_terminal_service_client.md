---
title: "Hiding GNOME and starting terminal service client?"
date: 2011-09-23
forum: General Help
---

### Post by Tylerofl on 2011-09-23
The company I work for is getting a large shipment of new medical equipment, and each machine has a tower and monitor built in. The towers, by default, run Ubuntu 9.04, and I don't want to install Windows to cut costs. As the IT guy, it's my duty to get these machines connected via RDP to a Windows Server 2003 terminal server. The terminal server client Ubuntu ships with is just fine for this.

My goal is to basically make these towers into thin clients. I would like to disable the GNOME panels, and make it so it automatically starts the terminal services client and connects to the specified server.

A bonus objective would be to script this process, so when more of these machines come in the future, we could save a lot of time (although that's probably a little too much to ask, if you can't suggest something for this, that's okay).

Thanks in advance!

---

### Post by alquery on 2011-09-23
I've never tried to do anything like this, so this is probably not optimal, but I would:

A. install Boot-up Manager (package name is "bum")
B. go to System -> Preferences -> Startup Applications and uncheck everything you don't need (gnome-panel etc.)
C. open up bum and uncheck everything you don't need
D. go back to Startup Applications and add Terminal Server Client to the startup list (app name is tsclient to save you some time)
E. you could set up automatic login since anyone using the box will have to log in to the remote computers anyway (depending if the server has a password I guess)

This is part of the solution I would use. However, I have no idea how to get tsclient to automatically go to a certain server. Also, I am running 11.04 not 9.04, so you menu locations and names of apps might be different. You also might run into some other problems because that version of Ubuntu is officially unsupported to my knowledge.

Sorry, but I have no idea how to script this.

---

