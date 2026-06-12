---
title: "Bluetooth mouse connection corrupted - how to reset?"
date: 2009-12-28
forum: General Help
---

### Post by jacksenechal on 2009-12-28
My BT mouse (Logitech M-RCQ142) was running out of batteries, and lost the connection. When I deleted the device from the BT manager and tried to reconnect it, the connection failed. Now, I have new batteries but can't connect because, it seems, something has become corrupted in the configuration. 

When scanning for new devices, it always shows my mouse there immediately, whether the mouse is discoverable or not. When I try to pair it, it immediately says pairing failed. The mouse is not there in the preferences screen, so I can't delete it. But it does show up in the applet menu under "devices".

"hcitool scan" reports the mouse correctly when it's discoverable. "hcitool cc" doesn't complain, but neither does it connect the mouse. "hcitool dc" says it's not connected.

How can I reset the configuration to get rid of the ghost of the mouse, so I can start over and connect it?

---

### Post by pluto4ps on 2009-12-28
Disable and enable bluetooth then check...

---

### Post by jacksenechal on 2009-12-28
I solved it. 

Of course I had tried turning bluetooth on and off, restarting the machine, all the usual. 

In the end I used some grep magic to discover a set of files in /var/lib/bluetooth that contained reference to my mouse's bluetooth ID. I just deleted all the lines that contained the ID in those files and then I was able to set up the mouse again without issue. 

Good times. Hope this helps someone else :)

---

