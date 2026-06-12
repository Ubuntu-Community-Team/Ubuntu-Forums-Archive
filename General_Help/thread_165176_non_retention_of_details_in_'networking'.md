---
title: "non retention of details in 'networking'"
date: 2006-04-24
forum: General Help
---

### Post by rumrat on 2006-04-24
Hi all,
I have just built and Acer 3300 laptop with ubuntu, and am having trouble with the retention of details in the networking setup.

In as much I setup several profiles for use in various locations, including a profile dedicated to the use of in built modem.  Upon reboot only one set of details is retained 'somewhere', but is not visible in networking applet, the network (eth0) functions.  None of the other locations have retained the relevant detail.

---

### Post by shof2k on 2006-04-24
I've had similar problems.  The settings saved in the networking applet aren't stored in /etc/networking/interfaces, so I end up hacking this by hand.

Are networking details held somewhere different?

---

