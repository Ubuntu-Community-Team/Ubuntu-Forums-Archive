---
title: "VNC to Ubuntu 10.10 workstation."
date: 2011-03-28
forum: General Help
---

### Post by robfindlay on 2011-03-28
Is there a way to have the remote desktop capabilities of Ubuntu 10.10 start at boot time? 

As it is I have to log in first and start the service.

Sorry if this is a newbie question. 

Thanks.

-R

---

### Post by ridgeland on 2011-03-30
I use VNC over SSH to remotely connect from my study to the living room PC (HTPC).  HTPC only needs to be on.  No one needs to at the HTPC to OK it or to start a program.

Is that what you are wanting to do?

Are you wanting a startup script that automatically connects a remote computer each boot?  using VNC?

---

### Post by robfindlay on 2011-03-30
> **ridgeland said:**
> I use VNC over SSH to remotely connect from my study to the living room PC (HTPC).  HTPC only needs to be on.  No one needs to at the HTPC to OK it or to start a program.

Is that what you are wanting to do?

Are you wanting a startup script that automatically connects a remote computer each boot?  using VNC?

I want the VNC service to start at boot-up.  Other wise I have to hook up the monitor/keyboard/mouse each time and log in and start the the VNC server. 

Rather it runs automatically after I login, I just want to be able to VNC in before logging in. 

Hope that explains...

-R

---

### Post by ridgeland on 2011-03-30
Staying with my HTPC example.  The PC auto logs in a user.  That user ID allows remote access.  So once turned on I can log in to it.  The TV is the monitor, it doesn't have to be on.  It's keyboard and mouse don't do anything.

You want to run VNC without first logging in a user?

---

