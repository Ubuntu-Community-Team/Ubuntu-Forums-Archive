---
title: "vncpasswd not populating ~/.vnc/passwd"
date: 2010-09-29
forum: General Help
---

### Post by msaqib on 2010-09-29
I have an account on a remote Ubuntu machine. I started the vncserver on that box, it used display number 7. From my Windows machine, I connected to the remote box on port 5907. It connected, but said, "no password configured for vncauth". I noticed that the ~/.vnc/passwd file is empty, alongwith the log file. I typed vncpasswd to set the password again, but no use. I tried vncpasswd ~/.vnc/passwd as well, but no use.
The VNC server is running. Any clues to what is wrong or on how to trace what's wrong?
Thanks
Saqib

---

### Post by msaqib on 2010-09-30
Solved! We were running out of disk space on the drive. Funny the command didn't complain about that.

---

