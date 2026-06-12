---
title: "Strange SSH behavior for arrow keys"
date: 2009-07-05
forum: General Help
---

### Post by aphexcoil on 2009-07-05
I am using a different server and when I SSH into the box, the up arrow key will show "^[[A" instead of showing previous commands.
 
The down arrow key also is not working as expected. 
 
Any ideas?

---

### Post by t4thfavor on 2009-07-06
Looks like either the terminal client doesn't support the up arrow binding, or the shell on the other end has no history support, try running bash then pushing the up arrow over the ssh session. I see that sometimes when I telnet into routers/switches, or the ocasional linux based embedded device.

---

