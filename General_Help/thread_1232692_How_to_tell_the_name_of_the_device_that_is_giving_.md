---
title: "How to tell the name of the device that is giving my internet connection"
date: 2009-08-05
forum: General Help
---

### Post by josephellengar on 2009-08-05
I need to know what my computer calls the ethernet connection, but the network manager applet is giving me no information or telling me that I have no connection when I definitely do.  Is there a terminal command?  :confused:

---

### Post by Scotty Bones on 2009-08-05
a wired connection is going to be eth0 and a wireless will be wlan0

you can use ifconfig in the terminal to check.

---

### Post by lvleph on 2009-08-05
If you want to know what card you have use the command.```

lspci
```

---

### Post by josephellengar on 2009-08-05
Got it!  Thanks.

---

