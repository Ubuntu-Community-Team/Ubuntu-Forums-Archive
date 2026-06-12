---
title: "gconf-sanity-check-2 exited with status 256"
date: 2012-03-11
forum: General Help
---

### Post by igor2000 on 2012-03-11
[SIZE=2]I'm running Ubuntu 10.04.4 LTS and had a disk glitch; filesystems were not mounting.
Booted from a CD with slax and ran:  e2fsck -f -y -v /dev/sda1
To make sure that there were no residual errors, I rebooted from a CD with slax and re-ran:  e2fsck -f -y -v /dev/sda1

Booted from the hard drive and the system came up, but no gnome (which had been working ok before the crash).  Just an error box with:

[B]There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)[/B]


alt-ctrl-F1 gets me to a log-in prompt, and I can get in to a command prompt.  Similarly, I can ssh to the box.

Looking at various threads, I tried the following, to no avail:
Removed gconf2, gnome-panel, and gconf2-common; deleted /etc/gconf; installed gconf2, gnome-panel, and gconf2-common; no change.

Running dpkg-reconfigure gdm  does not produce any output, just returns to a prompt.

Running /usr/lib/libgconf2-4/gconf-sanity-check-2 from a command prompt produces:
[B]The files that contain your preference settings are currently in use.

You might be logged in to a session from another computer, and the other login session is using your preference settings files.

You can continue to use the current session, but this might cause temporary problems with the preference settings in the other session.

Do you want to continue? Continue (y/n)?y
Failed to load addresses to delete locks
Please contact your system administrator to resolve the following problem:
No configuration sources in the configuration file "/etc/gconf/2/path"; this means that preferences and other settings can't be saved. Error reading the file: Failed: Couldn't open path file `/etc/gconf/2/path': No such file or directory
[/B]

Also:
gdm owns /var/lib/gdm
Everything in /etc/gconf is set to 755
/tmp is set to 1777
renamed /etc/gdm/custom.conf to custom.conf.old


I'm stumped! Any help or suggestions would be appreciated.
[/SIZE]

---

### Post by igor2000 on 2012-03-11
Solved!  Looks as if I was almost there. All that I had to do was copy the /etc/gconf/2/path from another system, and then reconfigure nvidia.

---

### Post by koolkev on 2012-06-03
> **igor2000 said:**
> All that I had to do was copy the /etc/gconf/2/path from another system, and then reconfigure nvidia.

How do I get that file if I don't have another system? 

Do I have to reconfigure my video too? How do I do that?

---

