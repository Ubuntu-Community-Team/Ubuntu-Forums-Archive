---
title: "How to setup dual screen"
date: 2009-10-31
forum: General Help
---

### Post by PaulM1985 on 2009-10-31
Hi

I have just got a new monitor and I want to set it up so that I have a monitor for each of the ubuntu desktops and be able to move my mouse off the right of the left hand screen onto the left of the right hand screen.

Is this possible?  I have a Nvidia GeForce 6150 LE graphics card.  It has a normal output monitor socket and another one which I think might be a digital/hdmi output..?  I don't know much about computer hardware.

Any help or advice would be greatly appreciated.

Paul

---

### Post by scouser73 on 2009-10-31
Please follow these instructions for setting up dual monitors.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Then go to **X Server Display Configuration** then set up your monitors to your liking

**3** - Once you have done so click **Apply** then click **Save To X Configuration File**

You will now have dual monitors working.

---

### Post by PaulM1985 on 2009-10-31
Thanks for your quick response.  The other thing I wanted to check was how to plug in a second monitor.  Is the other connection that I mentioned a hdmi connection?  Do I just need to buy an adapter to convert the socket to a "normal" monitor connection?

Paul

---

### Post by scouser73 on 2009-10-31
Is the connection that you're referring to the long white one?

[[IMG]http://img442.imageshack.us/img442/1325/screenshotpu.th.png[/IMG]](http://img442.imageshack.us/i/screenshotpu.png/)

If it is, then that is a DVI connection.  So you'd need a VGA to DVI lead, the VGA slotting into your monitor, and the DVI slotting into your card.

I've added a link for a VGA to DVI lead, so you know what to look for.

[[COLOR="Red"]**VGA to DVI lead**[/COLOR]]("http://www.maplin.co.uk/Module.aspx?ModuleNo=97372")

---

### Post by PaulM1985 on 2009-10-31
Yep, thats the one.  Thanks so much with all the help.

Paul

---

