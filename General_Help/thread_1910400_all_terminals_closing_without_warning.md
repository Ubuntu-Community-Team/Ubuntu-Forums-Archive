---
title: "all terminals closing without warning"
date: 2012-01-17
forum: General Help
---

### Post by jdmcbr on 2012-01-17
There seem to be a few actions that I can take in a terminal that may randomly cause all open terminals to close instantaneously. These include opening a file with vim, opening a file with evince, and moving a terminal tab in one window to another window. 

I've had this problem for the past month or so, and cannot seem to find on google any other examples of people having this problem (perhaps due to using poor terminology in searches?). I'm running 11.10, and the only changes made to my system around the time when the problem started happening were the updates suggested by the automatic updated.

I'd be very pleasantly surprised if this is enough information for anyone to help me with this issue. Can anyone tell me how to get more information about what is going on? Since all my terminals close, I don't get to see any sort of error messages. The problem is also not easily reproducible, unfortunately, since it occurs randomly. Anyway, thank you for any help!

---

### Post by TeoBigusGeekus on 2012-01-17
Corruption in your .bashrc file maybe?
Try renaming it to .bashrc_backup or something and monitor the behaviour of your terminal.

---

### Post by jdmcbr on 2012-01-18
I gave that a shot, but the problem struck again. This time, while pressing shift-G in vim.

---

