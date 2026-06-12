---
title: "USB Gamepad, PLEASE HELP!"
date: 2010-07-27
forum: General Help
---

### Post by comptontravis on 2010-07-27
I've spent the last 8 hours straight trying to get this to work and I'm not willing to quit yet. I'm trying to use my Gamemon Gamepad (model no. FT2E92) in zsnes. I'm using Ubuntu Netbook Remix 10.04. First and foremost, my netbook detects all my other USB devices, and my gamepad works just find under my windows desktop. So I know it's not an issue with the gamepad or USB ports, but for whatever reason the netbook does not detect the gamepad. I've read countless sites and posts saying the I need to install joystick (sudo apt-get install joystick) that installs just fine but I need my computer to detect my gamepad before I can do anything with joystick. I also tried installing jscalibrator, when I try 'sudo apt-get install jscalibrator' I get "E: couldn't find package jscalibrator". In my opinion the most important thing at this point is to get the netbook to realize that there is something plugged into the USB drive. 

Seriously I'm about to go crazy, anything anyone can tell me will definitely help. I appreciate everything and thank you in advance for any help.

---

### Post by rusivi on 2010-08-05
Hey I have the same GAMEMON Model: FT2E92 gamepad (I'm using Ubuntu 10.04, though not the netbook remix) and it worked in ZSNES. 

At first, I had ZSNES running, plugged the gamepad in, and ZSNES did not respond when I tried to map the keys to the gamepad. I restarted ZSNES, unplugged, then plugged back in the gamepad, then it worked.

```
apt-cache policy zsnes
zsnes:
  Installed: 1.510-2.2ubuntu3
  Candidate: 1.510-2.2ubuntu3
  Version table:
 *** 1.510-2.2ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Packages
        100 /var/lib/dpkg/status
```

---

