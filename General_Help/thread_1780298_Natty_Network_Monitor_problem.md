---
title: "Natty Network Monitor problem"
date: 2011-06-11
forum: General Help
---

### Post by jfbooth on 2011-06-11
At the bottom of my 'desktop' is a 'task bar' (another one at the top).  On the bottom one are some icons.  Mousing over them presents:

Minimize all open windows and show the desktop
Take a screenshot of the entire screen
NOTES
NET
Switch to workspace 2

I customized it some time ago to hold most of these icons.  Panel Property ITEMS list the items I customized for the panel.  One is Network Monitor (shown as NET on the panel/bar 'thing')

Before upgrading to Natty, that item (NET) would animate in yellow and red when I had network traffic.  It no longer does that.  When I mouse over the NET icon, it says "<< >>(Interface down)"

PROPERTIES of that item (Network Monitor):

Text to Display   NET
Network device    empty field
Update interval   .25 s
Automatic maximum   checked
Bar color incoming  RED
Bar color outgoing  YELLOW

The computer is connected with an Ethernet cable going to an Eth port on a home router which is connected to a cable modem.

I am ASSUMING I need to put something in that empty Network device field.

Can anyone help me get Network Monitor to work as it did before the upgrade?  The system works fine .. by the way.

Thank you in advance.

---

### Post by Toz on 2011-06-11
Try **eth0**. If that doesn't work, open a terminal window, type in:```
ifconfig
```and post back the results.

---

### Post by jfbooth on 2011-06-11
> **Toz said:**
> Try **eth0**.

That DID it for me.  I thought about trying that .. but am such a noob I hesitated.

Thank you for your quick reply.

---

