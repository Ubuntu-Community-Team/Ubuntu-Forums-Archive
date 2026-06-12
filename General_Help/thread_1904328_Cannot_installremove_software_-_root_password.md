---
title: "Cannot install/remove software - root password"
date: 2012-01-04
forum: General Help
---

### Post by Toafan on 2012-01-04
I had recently installed the gnome-3 desktop, and went to uninstall some of the cruft that it dragged along with it, when the Software Center asked for the root password.
That's not right, as I haven't *set* the root password, and it's disabled by default.  

After some unrelated futzing around, an attempt to uninstall the cruft with sudo apt-get, the creation of a new group (for my own purposes), and a reboot, I discovered I couldn't use sudo any more either, apparently I'm not in the sudoers group anymore. ```
toafan@toafan-HP-ubuntu-11:~$ sudo man man
[sudo] password for toafan: 
toafan is not in the sudoers file.  This incident will be reported.
``` (it's possible that I accidentally kicked myself out of sudoers when I added my group. What's the significance of group # 2000?)

I don't mind going root via recovery mode to fix the problem, but since it's of this type/magnitude I don't want to muck about without knowing what I need to change.  I *DO* mind not being able to use the software center, and not being able to sudo.

Help?

---

### Post by Buntumatic on 2012-01-04
You can edit /etc/sudoers 

or you can add yourself to admin group or sudo group.

---

### Post by Toafan on 2012-01-04
Alright.
Given that, re-adding myself should solve both problems, correct?
(frankly my worry is that my new group somehow collided and kicked me out)

---

### Post by Toafan on 2012-01-04
Alright.  Upon reboot, I discovered the source of my original problem: I had used the -G option, to set groups, without the -a option, to *append* groups.  Argh.
But then it turned out that it wouldn't let me mod users/groups from recovery mode.

I think that, by setting the root password, booting up and loging in, adding my account back, and then re-locking root, I can solve my sudoers problem.  Now the question is, what groups should I be in?  But I believe I should be able to reference this off a different install.

---

