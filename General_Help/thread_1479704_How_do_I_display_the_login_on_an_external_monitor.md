---
title: "How do I display the login on an external monitor"
date: 2010-05-10
forum: General Help
---

### Post by tjw09003 on 2010-05-10
I run Ubuntu on a MacBook Pro with an external monitor connected. But currently the external monitor only works with one user account. The External gets no signal and the laptop display is used on the login page. Is there any way of having the login page and possibly startup displayed on the external at all times for all accounts.

System > preferences > Display Doesn't work for me, I use NVIDIA X Server Settings

---

### Post by tjw09003 on 2010-05-11
Never mind I figured it out with Google :D

In NVidia X Server Settings I had to click "Save to X Configuration File", but that didn't work. so I deleted the file /etc/X11/xorg.conf then I made a new one. But Nvidia still couldn't save the file for some reason even with root privileges, so I took the preview it created and copied-n-pasted it manually with edit into xorg.conf. Now it all works :D

---

