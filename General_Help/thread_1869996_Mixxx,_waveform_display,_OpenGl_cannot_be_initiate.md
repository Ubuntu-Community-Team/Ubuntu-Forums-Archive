---
title: "Mixxx, waveform display, OpenGl cannot be initiated"
date: 2011-10-26
forum: General Help
---

### Post by murderd2death on 2011-10-26
So i got the latest version for mixxx up and running, and its going pretty good, except that i can't see a visual representation of the audio waves. It should look like[ this.]("http://www.mixxx.org/images/splash_mixxx_screenshot_deere.png") Instead i get [this]("http://i.imgur.com/Bf7WP.png"), and when i try to turn on the waveform display i get a response that says the [opengl cannot be initiated]("http://i.imgur.com/PQN11.png"). Im running natty on a lenovo b570. can you help me out so i can get waveform display turned on and working?

regards.

---

### Post by murderd2death on 2011-10-26
bump

---

### Post by murderd2death on 2011-10-27
Bump again

---

### Post by junkilo on 2012-02-18
opengl is messed up in your xorg configuration. I ran into the same issue on an intel gma 3000, but also have nvidia optimus onboard. purged nvidia packages, reconfigured x, reboot.

see [http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work]("http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work")

---

