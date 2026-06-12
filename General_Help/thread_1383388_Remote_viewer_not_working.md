---
title: "Remote viewer not working"
date: 2010-01-17
forum: General Help
---

### Post by Ant01 on 2010-01-17
The problem I have is that my remote viewer to Ubuntu doesn't work from my laptop. I am not sure if this is as a result of updating the nvidia drivers. (link to post [http://ubuntuforums.org/showthread.php?t=1379251]("http://ubuntuforums.org/showthread.php?t=1379251")

I can view remotely but the mouse cursor only works on the ubuntu machine and not my laptop, the screen doesn't change on my laptop once the viewer is loaded in the ubuntu machine so moving the mouse on the laptop moves on the both machines but doesn't control from the laptop.

Secondly the keypad from my laptop works externally, so I can type on my laptop and it shows on the ubuntu machine.

Lastly, the screen on my laptop doesn't change with the ubuntu machine.

---

### Post by gradinaruvasile on 2010-01-17
First of all disable screen compositing (desktop effects) on the target machine. It doesnt work right if its on.
Second get a better VNC viewer - the default one is crap. I recommend Remmina:

[https://launchpad.net/~llyzs/+archive/ppa](https://launchpad.net/~llyzs/+archive/ppa)

---

### Post by Ant01 on 2010-01-17
Thanks, I removed the desktop effects via preferences/appearence/visual effects   and it sorted the problem out. :D

Please explain how to add remina to ubuntu

---

### Post by JetPack on 2010-02-08
I had the same problem but turning off visual effects on the remote machine did not fix it.

Both machines are running Ubuntu 9.10.

I solved it by installing gnome-rdp on the local machine, along with having visual effects on the remote machine turned off.

I like this viewer better than the default viewer and it seems to be faster.

---

