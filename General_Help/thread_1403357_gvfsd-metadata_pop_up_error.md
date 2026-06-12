---
title: "gvfsd-metadata pop up error"
date: 2010-02-10
forum: General Help
---

### Post by giammy on 2010-02-10
Hi all,

I have a problem with gvfsd-metadata.

I installed a Ubuntu 9.10, and, using remastersys (backup mode) and unetbootin 
I built a bootable USB stick with my system, in persistent mode (i.e. the modification
or data I put in the usb stick will remain for the next reboot).

The problem is  than when I first boot the key I get the following error:
'Sorry, the program "gvfsd-metadata" closed unexpectedly'

The pop up comes out after some minutes of usage and if I press OK
everything  works but the pop up will compare again.

If I reboot, everything is OK.

My supposition is that at the first boot, the system has to build the persistent
filesystem, and gvfsd is unable to write something. The next boot he can write
all he want - so no errors.

But this is just a supposition: I do not know how to eliminate such an error!

thanks
giammy

---

### Post by giammy on 2010-02-11
Hi all,

Just an update: I was trying to disable gvfsd-metadata: I found that
it is started at the user login, so I imagine it is present in some
configuration files in the home of the user, but I'm unable to find
it. How can I avoid that gvfsd-metadata starts at login?

thanks
giammy

---

### Post by steev_666 on 2010-03-12
The thing that works for me whas


rm -rf ~/.local/share/gvfs-metadata

Looks Like when you get your disk full those archives get corrupt, just remove the folder and it will be created again and the isue must be repaired.

It works for me, when gvfs-metadata goes 100% my cpu

---

