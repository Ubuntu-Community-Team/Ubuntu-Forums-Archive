---
title: "Login Problems"
date: 2010-10-01
forum: General Help
---

### Post by jgeralnik on 2010-10-01
I'm using 10.10 beta. When I start the computer it shows the screen listing all the usernames and the 'other' button to login as a different user. However, when I click any button it does not show the password textbox (or user textbox in the case of the 'other' button). It does show only that username for a second as make the screen smaller just like it is does when it works but the textbox doesn't appear and after half a second it reverts to the list of all the users.

On the other hand, booting into recovery mode, pressing escape, logging in through the terminal there, and using startx loads GNOME just fine.

Doing the same with ctrl+alt+f2 on regular boot doesn't work because startx fails since it is already running. After logging in on that terminal and going back to the login screen it shows that I am logged in but again pressing my username does not take me anywhere.

---

### Post by Silent Warrior on 2010-10-01
Sounds like you have an excuse to go back to the official 10.04-release. *AHEM* :)
I understand the RC was recently released. Are you fully updated? How's about a dpkg-reconfigure gdm?
In case you're still out of luck, consider installing KDM and using that until you see an update for GDM.

---

### Post by jgeralnik on 2010-10-22
After a few weeks of suffering, I decided to do a clean install. I then reinstalled any important programs, updated ubuntu, and restarted the computer. I was met with an "enter password to unlock default keyring" prompt. I wanted it to unlock automatically on login so I looked up libpamkeyring on google and added whatever line the tutorial told me to to the end of my /etc/pam.d/gdm file. I logged out and tried to log back in and found that the problem had returned. It turns out I had done the same exact thing previously except without testing to see if it works. The next day when I had tried to log on, I couldn't and didn't remember that I had changed that file.

---

