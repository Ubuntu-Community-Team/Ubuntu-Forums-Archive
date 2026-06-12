---
title: "Uninstalling source package"
date: 2006-05-07
forum: General Help
---

### Post by october1917 on 2006-05-07
I've done something bad to my Ubuntu.

I had some problem with K3B (couldn't associate with cue files - only this), and after having search too much, i decided to uninstall it from Synaptic, and install the source package as it says at K3B site. Then i didn't knew how to install mp3 support, and it couldn't work even if i had already the mp3 plug-in installed from Synaptic.

Someone told me to go to /....../K3B/plugins and do "make" and "make install". That was all. Now, K3B doesn't react even if i just try to launch it, and i don't know if after the "make", "make install" in the plugin folder i can uninstall the program.

I'm new in Linux, and i have heared that connected as user, is impossible to do something cannot be un-done to your system. Is that true?

Sorry for the rather bad language. greek.

---

### Post by garner_nc on 2006-05-07
If you want to build and install from source I highly recommend checkinstall. It's replaces the  normal "make install"  when building from source. It keeps track of all the files installed. Checkinstall can later remove every component of an installed package.
   I know this doesn't help you now but in the future keep it in mind. Checkinstall is in the repositories.

All the Best,
Doug White

---

### Post by az on 2006-05-07
[QUOTE=october1917]
I'm new in Linux, and i have heared that connected as user, is impossible to do something cannot be un-done to your system. Is that true?
[/QUOTE]

Horse-hockey!  (Not true!)

Just go into synaptic and reinstall k3b.  See if that works.  The install libk3b2-mp3 to enable mp3.

It may be called k3b-mp3 in breezy...

---

### Post by october1917 on 2006-05-07
Do you think that if i install on the old installation again the same version using this time the checkinstall, it sould be removable after that?

---

### Post by october1917 on 2006-05-07
Thank you azz. The Synaptic installation indeed works. But i want also to remove all the useless after that files created. Is there a way?

Or exists there a program such as CheckLinks (win) to delete the useless files?

---

