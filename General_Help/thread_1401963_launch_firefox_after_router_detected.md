---
title: "launch firefox after router detected"
date: 2010-02-08
forum: General Help
---

### Post by ant-monkey on 2010-02-08
Hi
I am launching my web browser from start up.
How can i detect that the wireless network has been detected and connected before the 
browser launches?

---

### Post by Joeb454 on 2010-02-08
Moved to General Help.

I imagine you (or somebody else) could write a small bash script that would check if you have an IP address, and then launch the web browser.

You could probably write it so that if there's no IP address, wait 5 seconds, then try again, until the browser is launched :)

---

### Post by doas777 on 2010-02-08
if you are using /etc/network/interfaces then it looks like you can run a post-up command.
not sure if it would run with your user or appear on your session though.

---

