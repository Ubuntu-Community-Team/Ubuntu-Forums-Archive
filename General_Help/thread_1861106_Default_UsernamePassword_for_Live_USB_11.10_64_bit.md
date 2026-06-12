---
title: "Default Username/Password for Live USB 11.10 64 bit"
date: 2011-10-15
forum: General Help
---

### Post by Elias the Pious on 2011-10-15
Hello there....


I am running Ubuntu 11.10 64 bit right off my USB drive. All is well, but I have one issue: I installed Gnome Shell from the Software Center, and to activate that I know I must do so via the login screen. When I log out to access that screen I cannot use any password to re-enter. I tried the following

Username: Ubuntu
Password:

Username: ubuntu
Password:

Username: Ubuntu
Password: Password

etc. etc.

I even tried resetting the password using this site [http://www.pendrivelinux.com/what-is-the-default-root-password/](http://www.pendrivelinux.com/what-is-the-default-root-password/)

I google searched and can't reset this thing. What is the default username and password, please?

---

### Post by Elias the Pious on 2011-10-15
I just tried about 10 more username/password combinations with no luck. ;-(

Is there just no way to change window managers on Live USB

---

### Post by Elias the Pious on 2011-10-15
Is there simply no way? If there (really) isn't can someone let me know. I don't want to go chasing a ghost.

---

### Post by mc4man on 2011-10-15
The only way on a live session to use gnome-shell or gnome fallback (classic) is to create a new user, log out & log in to that newly created user picking the session you wish
(assuming gnome-shell & or fallback-session are installed

The default ubuntu user cannot use those sessions

---

### Post by Elias the Pious on 2011-10-15
Awesome, worked like a charm. Thanks a ton!

---

### Post by jharris1993 on 2011-11-27
You can use CTL-ALT-F1 to get to a console screen, run "passwd" and give yourself a password.  When you return from the console session (CTL-ALT-Fsomething) you should be able to login or whatever with the username "ubuntu" and the password you selected.

Jim (JR)

---

