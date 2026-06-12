---
title: "Jaunty refuses to update for anyone else?"
date: 2009-09-10
forum: General Help
---

### Post by JerecDrak2 on 2009-09-10
Hi Guys,

After trying to update Jaunty using the trustee old update-manager today I was confronted with the following error:

"An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, Eroblem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_jaunty_restrict ed_binary-i386_Packages, E :The package lists or status file could not be parsed or opened.'"

Using apt-get/aptitude doesn't work either, does anyone know how I can solve this?

Thanks!

---

### Post by earthpigg on 2009-09-10
verify your internet is working: you are on ubuntuforums.org, right? good, verified :D

system -> administration -> software sources -> ubuntu software -> download from -> other -> select best server -> let it test all the ubuntu mirrors in your country to find the fastest

no server has 100% uptime, so it is important to know how to pick a different one :D

and, if **everyone** uses the main *.archive.ubuntu.com server for their country, it will contribute to that server going slow for **everyone** in that country.

use mirrors!

---

### Post by JerecDrak2 on 2009-09-10
Well it seems that disabling all third party updates, doing a sudo apt-get update and then switching them all back on fixed this...strange!

---

### Post by drs305 on 2009-09-10
> **JerecDrak2 said:**
> Well it seems that disabling all third party updates, doing a sudo apt-get update and then switching them all back on fixed this...strange!

When you deselected the updates, those lists were removed from /var/lib/apt/lists . One of them had an error in it. When you reselected them again, the lists were downloaded again, and this time the files contained no errors.

---

### Post by JerecDrak2 on 2009-09-10
> **drs305 said:**
> When you deselected the updates, those lists were removed from /var/lib/apt/lists . One of them had an error in it. When you reselected them again, the lists were downloaded again, and this time the files contained no errors.

Ah, thanks for explaining that, will remember that in the future :)

---

### Post by misfitpierce on 2009-09-10
Mine are still giving me errors since yesterday because security repo is down or something... Someone else hit the same thing in recent thread I started... Trying what was said though to see if that helps.

---

### Post by jrweiss on 2009-11-02
I'm a noob with a similar problem in 9.04.  After adding ppa.launchpad.net_tsunetomo_ppa_ubuntu_dists_jaunty_main_binary-amd64_Packages to the repositories list in Synaptic package manager, I get the following error when I try to open SPM or use sudo apt-get update:

> Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_jaunty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

Is there a way to fix this via command line?  I do not have a Software Sources menu item under System | Administration.

---

### Post by drs305 on 2009-11-03
> **jrweiss said:**
> 
Is there a way to fix this via command line?  I do not have a Software Sources menu item under System | Administration.
Do you have Synaptic? (System, Administration, Synaptic Package Manager). It would be much safer to accomplish this via GUI than using root to delete system files. It can be done, and I will give you the commands, but I would prefer to do it via Synaptic. If you have Synaptic, do the steps as in Post # 3. (Settings, Repositories: Untick all Repositories in the Ubuntu Software and Third Party/Other tabs and then reselect them).

The other GUI way is to open a file browser as root and delete the package lists. Be careful in what you delete:
```
gksu nautilus /var/lib/apt/lists 
```
Do **not** delete the *partial* folder or any "lock" file. Delete all the other *files*. 

Then run:
```

sudo apt-get update

```

Once everything is working again, open up a root nautilus browser again to permanently delete the "root" trash:
```
gksu nautilus /root/.local/share
```
Use SHIFT-DEL to delete the "Trash" folder.

---

### Post by jrweiss on 2009-11-04
I have the Synaptic Package Manager, but I get the same error when I open it, and the entire app closes when I close the error message box.

I'll see if I can get it fixed by your command line method.  Thanks!

---

