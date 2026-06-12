---
title: "I messed up my Gimp installation. Help"
date: 2011-01-08
forum: General Help
---

### Post by jruh64 on 2011-01-08
I wish I could remember everything that I just did as I am sure that will help.
I originally had the Gimp 2.6 (?) installed from the default Ubuntu repository in software center.
I then upgraded to 2.7.2 from the ppa:matthaeus123/mrw-gimp-svn repository following instructions from [here]("http://ubuntumanual.org/posts/255/gimp-2-7-released-for-testing-and-we-are-impressed-with-the-outcome") .

I then decided I wanted to go back to the older version and tried uninstalling and re-installing from the software center but it still always installed the newer version.

I wish I could remember all the stuff i tried after that, uninstalling from software center and symantic, removing the 3 or 4 'ppa:matthaeus....' repositories from software sources (they were already causing errors when update manager did a 'check' or synaptic did a 'reload').

Now it seems it is uninstalled except for some of the add-ons. When I now try to re-install from Software center (provided by ubuntu) I get the following errors: "Package dependencies cannot be resolved:  This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."
I also get a pop-up saying: "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now? Once Update Manager has finished the repairs, you can close it and return to the store."  Clicking on 'Repair' doesn't work, the window just pops up again.

Not sure what to try next.  Hope someone can give me some advice.

Thanks, John

---

### Post by alphacrucis2 on 2011-01-08
> **jruh64 said:**
> I wish I could remember everything that I just did as I am sure that will help.
I originally had the Gimp 2.6 (?) installed from the default Ubuntu repository in software center.
I then upgraded to 2.7.2 from the ppa:matthaeus123/mrw-gimp-svn repository following instructions from [here]("http://ubuntumanual.org/posts/255/gimp-2-7-released-for-testing-and-we-are-impressed-with-the-outcome") .

I then decided I wanted to go back to the older version and tried uninstalling and re-installing from the software center but it still always installed the newer version.

I wish I could remember all the stuff i tried after that, uninstalling from software center and symantic, removing the 3 or 4 'ppa:matthaeus....' repositories from software sources (they were already causing errors when update manager did a 'check' or synaptic did a 'reload').

Now it seems it is uninstalled except for some of the add-ons. When I now try to re-install from Software center (provided by ubuntu) I get the following errors: "Package dependencies cannot be resolved:  This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."
I also get a pop-up saying: "Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now? Once Update Manager has finished the repairs, you can close it and return to the store."  Clicking on 'Repair' doesn't work, the window just pops up again.

Not sure what to try next.  Hope someone can give me some advice.

Thanks, John

first try to fix your repo catalogue:

```
sudo dpkg --configure -a
```

One option is to use ppapurge. It will remove anything installed from a specified ppa and install the version from the standard repos. Other option is to remove the app then disable the ppa.  If you want to use ppapurge, you need to install that first.

---

### Post by jruh64 on 2011-01-08
Thanks for your reply.

I ran **sudo dpkg --configure -a** and it did not return anything so i assume it worked?

I also just installed ppa-purge but seems i have no idea how to run it.  I had already removed the ppa and uninstalled the package but i must have done it wrong. actually sure i did that wrong.

Thanks, John

---

### Post by JOHNNYG713 on 2011-01-08
First completly remove Gimp via synaptic, and close synaptic, open your home folder press "cntl+h" this will show hidden files, remove .gimp 2.7, now open software sources and remove the ppa:matthaeus123/mrw-gimp-svn repository close and click "reload"  now reinstall Gimp via synaptic, now you should have  Gimp 2.6. Good luck !

---

### Post by jruh64 on 2011-01-08
Hey thanks both of you for the help.

I figured out how to use ppa-purge.  I had to add the ppa again and update, then i ran ppa-purge and it worked like a charm.  I now have the stable,documented version of gimp again.

Thanks, John

---

