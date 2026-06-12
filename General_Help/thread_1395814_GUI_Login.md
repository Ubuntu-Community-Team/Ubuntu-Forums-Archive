---
title: "GUI Login"
date: 2010-02-01
forum: General Help
---

### Post by dss.chandra on 2010-02-01
Hi,
When I installed Ubuntu on my laptop, I had chosen "automatic login" . So i was not asked ofr username and password everytime I switched on. I later wanted to change the settings. So I went to systems-->administration-->login window-->security. There I disabled automatic login and I reboot the computer. Now the GUI does not allow me to enter USername and password. It says "Authorization denied" at the login screeen.. PLease help me.

---

### Post by ajgreeny on 2010-02-01
Which version of ubuntu?
Do you actually get to enter your username and password, and then get thrown out, or do you not even get that far?
In 9.10, you don't type in your username, it is there for you to click.

---

### Post by dss.chandra on 2010-02-01
i don't get to enter username and password.. Using jaunty jackalope

---

### Post by underdog512 on 2010-02-01
At the login Screen, you should have an option in there that says something like "Use Other".  Click that and enter your username then password.  The next time you boot up it should be listed for you to click on.

---

### Post by ajgreeny on 2010-02-01
> **underdog512 said:**
> At the login Screen, you should have an option in there that says something like "Use Other".  Click that and enter your username then password.  The next time you boot up it should be listed for you to click on.
Not in 9.04, I'm afraid.

I can't see why you have the problem at all if the system autologged you in in the past, but if you can get to the command line at boot time, either by using Ctrl+Alt+F1, or recovery mode, you could try reinstalling gdm, though I don't think it sounds as if that is the problem.

It seems more likely that there is some glitch in the system, and I wish I copuld help more but regrettably, it is all beyond me.  Just check that the /etc/sudoers file looks right, like this one, as that may just be at fault for this to happen.

> # /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults    env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


---

### Post by gadolinio on 2010-02-01
I'm afraid i don't get what your problem is, exactly. I mean, what happens when you turn the computer on? Does it ask you for a username and password? what happens immediately before you're told you are not allowed to login?

---

### Post by dss.chandra on 2010-02-01
After I turn on the computer, I reach upto the login screen. I'm not able to type my username in the box. Instead I get a window saying "Authentication Failed"

---

### Post by ajgreeny on 2010-02-02
It sounds as if the autologin is not completely disabled in some way, that it is still trying to start up as your user account as before, but that the authorisation only, is somehow disabled.

I wonder if it is worth trying to purge gdm, noting all the other apps it takes with it, then re-install gdm and the other apps that went as well.  In theory that should get rid of any configurations that were made before, and allow you to start again.  I have no real idea if this will work or not, but even without gdm you should still be able to start a gui with the ```
startx
``` command from the command line screen.

---

