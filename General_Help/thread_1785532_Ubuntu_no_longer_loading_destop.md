---
title: "Ubuntu no longer loading destop"
date: 2011-06-18
forum: General Help
---

### Post by sarikan on 2011-06-18
Greetings.
I've tried to hibernate with Ubuntu 10.10, and it did so. I've started the system, but it loaded only an empty desktop with the mouse pointer (I'm using a dual monitor setup btw, with the laptop screen normally turned off, and the external monitor the only monitor I'm using)

I've switched to another tty, and stopped gdm using sudo service gdm stop. Then I've shut down the system. When I started the system again, it complained that there was a disk error, and I've chosen the option to fix it automatically. It ended up resetting the machine

Now when the machine boots, I get no errors, but I end up with the terminal login only. Starting gdm says that it is already running, though I can't seem to access it in any way (ctrl + alt +f8 does not get me to it...) 

Any ideas? This is a system I've worked on for over a week to configure so that I can do some development, and now my desktop is gone!

---

