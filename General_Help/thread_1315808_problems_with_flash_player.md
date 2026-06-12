---
title: "problems with flash player"
date: 2009-11-05
forum: General Help
---

### Post by ephrems on 2009-11-05
hi!!! Im a newbie in linux.I just upgraded frm ubuntu 9.04 to 9.10 and these are the problems i am facing my kernelis 32bit.

1.there are errors with my flash player

"The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?"

when i go thru with this............................

"The package 'adobe-flashplugin' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system."

I am unable to remove it from the synaptics packge manager I am gettin the following error while trying to open synaptics.......................


"E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."


I am unbale to install or upgrade any softwares or patches because of the same error
I have gone through a couple of threads in the forum and tried to do it manually but iam gettin the same error messages........................

It would be very helpful if u guys could gimme a solution

                                                            Thank You.

---

### Post by mac9416 on 2009-11-05
Hi, ephrems!

You can uninstall adobe-flashplugin, and install the flashplugin-nonfree with these commands:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # Deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # Force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # Force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # Installs flashplayer the easy way
```

Good luck!

---

### Post by ephrems on 2009-11-05
Thanks mannn wrks great............................

---

### Post by mac9416 on 2009-11-05
I can't really tell if it worked or not. Could you try running the last two commands again?

---

