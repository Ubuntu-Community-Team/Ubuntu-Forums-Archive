---
title: "TouchPad help."
date: 2012-03-11
forum: General Help
---

### Post by MoreThan9000 on 2012-03-11
I just got Ubuntu about an hour ago (although I'm not really a newbie when it comes to computers, I know two programming languages fairly well), and like other people, I'm having problems with my touchpad. I've installed synapstiks, but it didn't register that I even had a track pad (mentioned something about drivers). I don't have a button to disable/enable the touchpad, so that is out of the question. I tried 
sudo add-apt-repository ppa:atareao/atareao
sudo apt-get update
sudo apt-get install touchpad-indicator
but that didn't work. Any and all help is appreciated. Thanks.

Edit: I fixed the problem myself. Went snooping on the internet, and found
Sudo modprobe  -r psmouse
Sudo modprobe psmouse proto=imps
Which corrected the problem nicely. Thanks anyways

---

### Post by tom king on 2012-03-14
Using dconf Editor, which is free download from software center, you can manipulate your touchpad several ways: on / off and off only when typing, using the chek boxes.):P

---

