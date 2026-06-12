---
title: "tty1 not always opening on reboot / shutdown"
date: 2010-12-01
forum: General Help
---

### Post by dazzlepm on 2010-12-01
I am running Ubuntu 10.10 on a command line install using it for MythTV 0.24, which I have compiled and installed myself.
 
I boot into a command line and use an autologin (rungetty or mingetty) and .xinitrc to automatically start Xorg and MythTV. The box is connected to a flat screen TV via HDMI. I also use Mythwelcome with MythTV to shutdown when no recordings are taking place.
 
On occasion, more often than not, the PC boots fine but then fails to open tty1 (it stops after the final run init scripts line) thus if the TV is not turned on I get no display, and Xorg with Mythwelcome fails to run. The PC is working fine though and if there is a display (start boot with TV turned on)   I can CTRL-ALT to another tty and manually login and start Xorg.
 
I have tried different shutdown commands (shutdown -h, shutdown -P, poweroff) and it seems to work and then it goes wrong again.
 
Has anyone else had this problem and solved it or any other ideas?
 
Mobo is an ASUS AT3N7A-I with an Atom 330 CPU and Nvidia ION GPU.
 
All help appreciated,
 
Paul

---

