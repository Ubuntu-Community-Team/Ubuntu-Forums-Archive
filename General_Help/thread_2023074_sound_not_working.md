---
title: "sound not working"
date: 2012-07-11
forum: General Help
---

### Post by chapra on 2012-07-11
I have no sound on my laptop.  I have tried following the steps on the following page:  [https://help.ubuntu.com/community/SoundTroubleshooting/](https://help.ubuntu.com/community/SoundTroubleshooting/)

After all of the above failed, I tried upgrading ALSA, by following the link on the page, and entering these commands:

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa 

sudo apt-get update 

sudo apt-get install linux-alsa-driver-modules-$(uname -r)

After the last command, I got the message:

E: Couldn't find package linux-alsa-driver-modules-2.6.32-41-generic-pae

It would seem that the above procedure does not supply the proper package that my laptop needs.  Any ideas?

Chapra

---

