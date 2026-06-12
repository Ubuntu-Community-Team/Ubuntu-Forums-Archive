---
title: "useless packages?"
date: 2006-02-01
forum: General Help
---

### Post by slavik on 2006-02-01
is there a way to list packages which are not required by any other packages?

reason for asking is that I want (after installing lots of stuff) to get rid of unneeded package which I am not using ... but maybe it was required for something I used to use and such.

---

### Post by AmboyGuy on 2006-02-01
In Synaptic search for deborphan.

---

### Post by slavik on 2006-02-01
hey, thanks.

---

### Post by RAOF on 2006-02-01
There are (at least) two options here.  One is to use "aptitude" from the command line - when it installs a dependency automatically it marks it as such, so if you later remove the package all the (now unused) dependencies are removed automatically.

To just clean up unused packages, you can try installing "gtkorphan", which does exactly what you want - lists unused packages and allows you to remove them.

---

### Post by doclivingston on 2006-02-01
You can also view Orphaned packages in Synaptic, once you have installed deborphan.

1) Go to Settings->Filters
2) Create a new filter called "Orphaned packages"
3) Uncheck all the boxes on the "Status" tab, except "Orphaned"
4) Use the "Custom" button at the bottom of the sidebar, and go to "Orphaned packages"

You'll only need to do (4) after the first time.

---

### Post by astronerd on 2006-02-01
Just make sure that when you run the orphan filter through synapitc and uninstall packages for the first time to run it again cause it usually creates a new list of packages based on the ones that were just removed.

---

### Post by slavik on 2006-02-01
Thanks for the suggestions (VMware, here I come again). I installed orphaned and when I tried orphaner, I got a blank list ... I know there has to be a package that is installed but nothing else depends on it ... (I am sure nothing depends on ubuntu-desktop or build-essential since they are meta packages and such).

---

