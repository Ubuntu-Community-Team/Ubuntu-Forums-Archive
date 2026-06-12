---
title: "startup script management problem"
date: 2010-05-24
forum: General Help
---

### Post by zhangr on 2010-05-24
As I know, ubuntu systems adhibit a different startup scripts method rather than rc.d from Karmic. In Jaunty I can still use update-rc.d to enable/disable adjust start/stop sequence of the scripts, make a script for my application. But in "Lucid" seems it is not available.

For example, we have several vpn links which I want the openvpn daemon start before shorewall, since if the vpn interface has not been brought up, shorewall can not identify the interfaces and zones, and refused to start. I've tried to set "wait_interface" in /etc/default/shorewall, no improvements, just increase the time cost on bootup, Anyone have a solution?

Another problem, I made an start/stop script of my own todo something during system bootup and shutdown, how to make it work? seems update-rc.d does not take effect. Any ideas?

Thanks a lot:KS

---

