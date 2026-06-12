---
title: "Minimum gnome?"
date: 2011-04-30
forum: General Help
---

### Post by bartos on 2011-04-30
What are the minimum gnome files I need to run gnome software on Kubuntu?
I am trying to run Lottanzb and can't get preferences to show. So I think some gnome files are missing that are not in dependencies.

Thanks

---

### Post by ankspo71 on 2011-04-30
Hi,
Do you see any errors when running the application from the terminal (konsole) while trying to view the preferences?

Installing the gnome-core package should probably cover all of the basic gnome components. Technically it will install a Gnome desktop environment, but it is a very stripped down version of Gnome.

```
sudo apt-get install gnome-core
```
or search for the package in kpackagekit or synaptic etc.

If you are currently using Kubuntu 11.04, and do not want to install Ubuntu One in Kubuntu, then I recommend using the --no-install-recommends option. For some reason Ubuntu One is now  included as a recommended package. 

```
sudo apt-get install gnome-core --no-install-recommends
```

Hope this helps.

---

### Post by oldos2er on 2011-04-30
If you installed it with a package manager it should've pulled in all its dependencies.

---

### Post by bartos on 2011-04-30
sudo apt-get install gnome-core --no-install-recommends

Was probably still much for me but worked.

Thanks

---

