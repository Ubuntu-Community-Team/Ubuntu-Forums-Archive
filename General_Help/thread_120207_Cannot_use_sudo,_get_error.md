---
title: "Cannot use sudo, get error"
date: 2006-01-21
forum: General Help
---

### Post by bloodborne on 2006-01-21
Hey guys, I just started getting the weirdest error. I cannot access the update manager, or any other process that requires sudo. Instead I get: 

```
Failed to run /usr/bin/update-manager as user root:
 No password was supplied and sudo needs it.
```

Can someone help me out? I feel this is a pretty serious problem. :confused:

---

### Post by aysiu on 2006-01-21
Try this.
Close whatever windows are open.
Go to Applications > Accessories > Terminal
Type ```
gksudo synaptic
```
You'll be prompted for a password. Enter your user password.
What shows up?

---

### Post by bloodborne on 2006-01-21
Thanks for the quick reply. I get the same sort of error as before after running that command:

```
Failed to run synaptic as user root:
 No password was supplied and sudo needs it.
```

---

### Post by aysiu on 2006-01-21
What about this? ```
sudo apt-get update
```
And do you even get prompted for a password?

---

### Post by bloodborne on 2006-01-21
Ok, I ran the command and was prompted for my password, but got the following error after:

```
Sorry, user joe is not allowed to execute '/usr/bin/apt-get update' as root on localhost.localdomain.

```

joe is my user account I set up when I installed Ubuntu and is the only one on the computer currently, if that's important.

---

### Post by aysiu on 2006-01-21
[QUOTE=bloodborne]
joe is my user account I set up when I installed Ubuntu and is the only one on the computer currently, if that's important.[/QUOTE] That *is* important, actually. If you did a normal (i.e., not **expert** install), the first user you create should have sudo privileges.

---

### Post by bloodborne on 2006-01-21
Yep I just ran the normal install, nothing fancy. Have you or anyone else ever seen this happen before? I mean, to just lose sudo privliges on your own machine. I don't remember doing anything sudo-related before this happened, I think I was just tweaking sound options in Multimedia Systems Selector.

Well, any ideas?

---

### Post by aysiu on 2006-01-21
Try rebooting into recovery mode.
I believe this will boot you in as root.
Then open a root terminal and type ```
adduser bloodborne admin
``` Then reboot to normal Ubuntu.

---

### Post by bloodborne on 2006-01-21
Awesome it worked, thanks a lot. But I still wonder what would make this happen in the first place.  :)

---

### Post by Zalbor on 2006-01-21
I had something similar happen to me sometime ago, after I deleted the first user account (I did have another, with all privileges). Even after the "adduser user admin" thing, not everything worked fine until I reinstalled.

---

### Post by Tichondrius on 2006-01-21
Yeah this must have happened because you either edited some config files like /etc/groups or /etc/sudoers, or deleted and created users using gnome tools. Either way, you can boot into recovery mode and add this line to /etc/sudoers

joe ALL=(ALL) ALL

now reboot normally and user joe should be able to sudo, so you can fix any other issues like adding users to admin group etc using gnome interface *which requires sudo privilege to do these things).

---

