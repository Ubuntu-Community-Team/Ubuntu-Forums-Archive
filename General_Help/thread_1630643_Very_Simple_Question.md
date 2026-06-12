---
title: "Very Simple Question"
date: 2010-11-25
forum: General Help
---

### Post by george3095 on 2010-11-25
I'm stuck in Terminal. After installing the Nvidia 96 video driver, upon re-booting, the computer ended in Terminal.

I find everything anyone would ever want to know how to go to Terminal, but I've been spinning my wheels searching for one solitary simple command from Terminal. It must be a dark secret.

How does one get BACK to the GUI? I should have waited a month or so before upgrading to 10.10 from 10.04, so not waiting was a BIG mistake. Silly me. I expected 10.10 to be more highly refined than 10.04. I was dead wrong.

---

### Post by Hippytaff on 2010-11-25
try startx

---

### Post by psoup1965 on 2010-11-25
Your problem is most likely your xserver cannot find the proper video resolution or the driver did not install correctly.

You can try:
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart

---

### Post by Hippytaff on 2010-11-25
Sorry, didn't read the post properly, thought you were stick in the terminal. Didn't read the 'after rebooting' bit :-s

---

