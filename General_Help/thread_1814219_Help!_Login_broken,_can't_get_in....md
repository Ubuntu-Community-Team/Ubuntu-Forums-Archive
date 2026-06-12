---
title: "Help! Login broken, can't get in..."
date: 2011-07-29
forum: General Help
---

### Post by ceejay on 2011-07-29
Ubuntu 11.04.  I was trying to solve a problem with a keyring  - there are loads of threads suggesting all sorts of things, which I was trying to follow with no success. 

Eventually I deleted ~/.gnome2/keyrings/default.keyring and then set the login screen option to "show the screen for choosing" (it had previously been set to autologin). 

Ooops!

Now, when I reboot, I get the login gui with the list of users (actually there is only one) but when I click on the name the window just gives a little shimmy and does nothing else. There are no other options open to me at this point except to restart or shut down.

So, I've restarted into the recovery console. I have copied the default.keyring file back from the Trash folder to its original location - no change.

I have reinstalled ubuntu-desktop.  No change.

Any more ideas as to how I can get my computer back??

TIA

---

### Post by ceejay on 2011-07-29
Never mind - fixed it.  As part of my thrashing around earlier trying to fix my keyring problem I had followed a direction to add "@include common-pamkeyring" to the end of /etc/pam.d/gdm ... removing this fixed my problem.

---

