---
title: "Changing Graphics Drivers"
date: 2009-07-29
forum: General Help
---

### Post by KeilanS on 2009-07-29
I am having a fan issue with my Dell XPS M1330 with Ubuntu 9.04 and have been told that the solution is to switch to an older driver (Version 173).

So how do I do this? I went to hardware drivers under the administration menu and the Nvidia graphics driver wasn't listed. So could someone walk me through how to do this?

---

### Post by fcuk112 on 2009-07-29
download driver from nvidia.com.
open up synaptic package manager, search for nvidia and remove all packages.
type modprobe -l | grep nvidia and remove all .ko files

ctrl-alt-f1 to enter terminal
sudo killall gdm
sudo sh NVIDIAxxx.run
startx

---

