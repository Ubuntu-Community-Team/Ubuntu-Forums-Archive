---
title: "Remote desktop and Nvidia driver"
date: 2010-04-30
forum: General Help
---

### Post by UrbanGorilla on 2010-04-30
When either of the proprietary Nvidia drivers are enabled, viewing the desktop using a remote client (Windows TightVNC) does not work. The initial remote screen display is ok, but no updates to the remote display occur. Reverting back to the non-proprietary driver solves the problem. I have also tried using a 10.04 Live CD and used Remote Desktop Viewer on the client machine, and it behaves the same way.

---

### Post by solitaire on 2010-04-30
Think it's a known bug between nvidia and compiz.

On the remote machine, turn off compiz and try connecting to it again, the screen should refresh now.

---

### Post by UrbanGorilla on 2010-05-01
Thanks solitaire, that works. I wonder if/when it will be fixed?

---

