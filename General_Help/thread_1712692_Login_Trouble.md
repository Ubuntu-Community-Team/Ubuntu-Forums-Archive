---
title: "Login Trouble"
date: 2011-03-23
forum: General Help
---

### Post by dannyc116 on 2011-03-23
What Happened Before Problem:

I wanted to change some grub stuff, and figured I needed to login as root. I ONLY did the following: "sudo passwd root", and turned off the auto login feature.

Problem:

I logged out and the option to log in as root was not there so I clicked on my username to log in. My username and the box it was in disappeared then reappeared.

Things I Tried:

- I clicked a bunch of times on my username and I noticed that for a split second a message shows up on the login box that says something to the effect of "Error failed conversion(communicate?)"

- Restarted my computer and booted up in every possible mode to log in.

- I pressed ctrl + Alt + F1 to open a terminal and then logged in successfully that way, but when I switched back over to the graphical interface, it still presented the login screen but with a green check mark next to my username.

- I clicked on guest and other, but that does the same thing as clicking on my username

- I Googled problem then tried "sudo apt-get --reinstall ubuntu-desktop", but you need wired connection for that to work and I don't have an Ethernet cable (yet).

- Tried "sudo killall gnome-panel" - didn't do anything


Not sure if this problem can be fixed, but I am at least hoping that there is someone out there that can tell me how to turn off the auto login feature through a terminal. I thin that might at least get me back to my (probably not important) files.


Oh and I am a newb. I am (was) using Ubuntu Maverick(?) 10.10 (10.something?)

Thanks!

---

### Post by dannyc116 on 2011-03-23
Ok so I googled how to disable the auto login from terminal, and got back into my desktop. I am still wondering if anyone can help me fix my login.

What I did to get back in:

- ctrl + alt + F1 - to access terminal at login
- sudo vi /etc/gdm/custom.conf
- change autologin to true ( press "i" to insert, and "delete" (not backspace) key to delete )
- save ( press "esc" then type ":wq" )
- sudo reboot

---

