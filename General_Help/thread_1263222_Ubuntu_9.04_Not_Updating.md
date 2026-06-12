---
title: "Ubuntu 9.04 Not Updating"
date: 2009-09-10
forum: General Help
---

### Post by mleonard2012 on 2009-09-10
Today I successfully installed Ubuntu 9.04 onto a Gateway LT3103u netbook with an AMD L110 processor and X1270 integrated graphics.  I did this through wubi, as none of the current live ubuntu cd's (8.04, 8.10, or 9.04) would boot with my BIOS version (.3201 or something similar).  Anyway, I was actually surprised to see that my graphics drivers were enabled by default and I was using compiz right away.  I had and still have no wireless, however can use an ethernet cable for the time being.  As I was done checking to make sure core functionality worked on this system, I realized that I could not use any form of Synaptic Package Manager, such as Update Manager, or Add/Remove Programs.  I have a valid internet connection, as I am writing this post on the netbook.  for some reason, however, no synaptics package manager will update.  Does anybody have any ideas as to why?

---

### Post by macalan on 2009-09-10
I'm having the same problem. Fresh 9.04 install in a virtual machine. Getting connection failed errors.

---

### Post by mleonard2012 on 2009-09-10
just wondering, what ISP do you have?

---

### Post by mleonard2012 on 2009-09-10
well thanks for at least letting me now that someone else was having a problem, and it wasn't just me having a bad configuration.  anyway, for all of those that had the same problem, it's working now

---

### Post by red_spyder on 2009-09-10
Sometimes I will activate new updates by opening a terminal and typing:
```
 sudo apt-get update
sudo apt-get upgrade

```

hope this helps!

---

### Post by mleonard2012 on 2009-09-10
thank you for the help, however it is not how i get to the update manager that matters, it was the fact that the update manager could not find the update server for some reason

---

