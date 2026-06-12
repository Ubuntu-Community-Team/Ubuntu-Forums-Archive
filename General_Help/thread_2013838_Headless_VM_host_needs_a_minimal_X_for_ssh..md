---
title: "Headless VM host needs a minimal X for ssh."
date: 2012-07-01
forum: General Help
---

### Post by ant2ne on 2012-07-01
I will be installing an ubuntu server 12.04 soon. It will be a virtual box VM host running headless VMs. It will not have a monitor connected to it regularly.


I need this server to have a minimal X server mainly so I can connect to it using "ssh user@server -X" and then launch apps like VirtualBox. What would be the lightest method to do this preserving the most resources on the server? Can I install just the X and not the entire desktop package?

will this, ```
sudo apt-get install xserver-xorg xserver-xorg-core xterm
```get me to where I need to be?

Does ubuntu server support default run levels so that it will not launch the X on boot up, but be available for when an ssh connects via the -X switch? Or in order to pass the -X does the X need to be running at the monitor?

---

### Post by hunter.allen on 2012-07-02
Yes. That should work. If it doesn't, just install more x11-related packages. 

To verify that it is enough, install the x11-apps package:


```
sudo apt-get install x11-apps
```

then run xeyes in ssh. You should get some eyes.

---

### Post by Cheesemill on 2012-07-02
Just install a package that you want to run using X forwarding, it will install the minimal needed dependencies for you, for example:
```
sudo apt-get install nautilus
```

---

### Post by ant2ne on 2012-07-04
Thanks!

---

