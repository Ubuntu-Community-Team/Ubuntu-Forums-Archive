---
title: "X-windows launch on host, not client, computer"
date: 2011-07-31
forum: General Help
---

### Post by jeremiahbuddha on 2011-07-31
Posted this over in ["Absolute Beginners"]("http://ubuntuforums.org/showthread.php?t=1812258") a week ago, but didn't get anywhere, so I'm reposting here if anyone has any ideas ... 

I have an Ubuntu 11.04 Desktop computer at home, and I have been trying to set up X11 so that I can ssh into this box remotely and launch x-applications on my Mac. I've edited both my /etc/ssh/ssh_config and /etc/ssh/sshd_config files (on my linux box) to include "ForwardAgent yes" and "ForwardX11 yes", and restarted my ssh server. 

I am able to ssh into my linux box just fine (ssh -X mycomputer), but when I launch an x-application, the window appears on my linux box (server) not my Mac (client)!

To make sure something wasn't wrong with my Mac setup, I was able to ssh into a work computer running RedHat and launch an x-application. It appeared on my Mac as expected.

Any idea what settings I have off on my linux box that won't allow me to launch x-applications on my Mac after I've ssh'd in?

---

