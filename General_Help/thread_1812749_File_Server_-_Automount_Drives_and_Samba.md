---
title: "File Server - Automount Drives and Samba"
date: 2011-07-26
forum: General Help
---

### Post by i3design on 2011-07-26
Hi,

I am really new to Ubuntu but thus far I have managed to do the following:

Install Ubuntu Server
Install the GUI (I wanted it this way)
Install Samba

Now, I understand that drives are not automatically mounted. When I click on them from the home folder they come up correctly on the desktop and I can access them, but I need this to happen automatically. Can someone explain how to do this please?

Furthermore, I have had no luck understanding how to add these drives to the Samba share list, so that they can be seen over the network. Is anyone able to offer some dumbed down advice for me on this please?

Regards,

James

---

### Post by galvatron408 on 2011-07-26
sounds like autofs is right for you.

sudo apt-get install autofs5

---

