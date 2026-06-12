---
title: "xinit: Server error."
date: 2010-02-10
forum: General Help
---

### Post by shabs on 2010-02-10
Hi!
I've been running 8.10 on a desktop for a month now. Its been working fine. I've been using it for some project work. 
I had to reboot the computer (I used to have it on all the time) and when it rebooted it takes me to the CLI and there is no GUI.
When I "startx" at the terminal I get an error that says "xinit: Server error"

Here are the things I've already tried:
1. sudo dpkg-reconfigure xserver-xorg
This skips the steps for the graphics card, does the keyboard configuration and then ends without the mouse and monitor configuration.

2. sudo apt-get install --reinstall gdm
Gets stuck at 'setting up ssl-cert (1.0.23)

3. sudo aptitude install ubuntu-desktop (I guess same command as above)
Gets stuck at 'setting up ssl-cert (1.0.23) again.

It was working fine so I don't know if its really a problem with my video driver.

Anybody has any other ideas? Any help would be appreciated as I'm stuck with this and this computer has a lot of information and configuration that I've been working on lately and don't wish to reinstall.

Warm wishes,
Shabs.

---

