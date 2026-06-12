---
title: "Unable to login after crash"
date: 2011-12-29
forum: General Help
---

### Post by hrok on 2011-12-29
Hi! I am using lubuntu for about half a year now without any problems, but today when i was doing some calculations in wolfram mathematica it just crashed. It showed the same lines it shows, when it shutdowns and froze there. I was able to write but the system did not respond to any of my commands, so i shut it down by force. Now i am unable to login. I get to login session and write username and password, but it doesn't accept it and just asks me again for username. I used recovery mode to see if something happened to my user acount, but the username and password works fine in recovery mode and my username is still in passwd and shadow. I would really appreciate if somebody has any idea what to do.

---

### Post by 2F4U on 2011-12-29
If you can get into the system there is a file called .xsession-errors in your home folder. This file may contain information about why you are unable to login.

---

### Post by hrok on 2011-12-29
The .xsession-errors is empty.

---

### Post by hrok on 2011-12-30
Another thing i notised in recovery mode. The su command doesn't accept my password (su: Authentication failure), while sudo -i accepts it, but says

sudo: Can't open /var/lib/sudo/myusername/console: Read-Only file system

And if i use passwd command to change my password (as user or root) it says

passwd: Authentication token manipulation error
passwd: password unchanged

One more thing (this might not be related to the main issue), it prints lines like this fom time to time by itself

[774.802030] usb 2-4: USB disconnect, device number 7
[775.072016] usb 2-4: new high speed USB device number 8 using ehci_hcd
[775.140244] hub 2-0:1.0: unable to enumerate USB device on port 4
[775.640015] usb 6-2: new full speed USB device number 3 using uhci_hcd
[775.784677] usb 6-2: not running at top speed; connect to a high speed hub

and i'm not doing anything with USBs. Does anybody now what might be wrong or what to do?

---

### Post by hrok on 2011-12-31
Ok no ideas... om going to reinstall lubuntu.

---

