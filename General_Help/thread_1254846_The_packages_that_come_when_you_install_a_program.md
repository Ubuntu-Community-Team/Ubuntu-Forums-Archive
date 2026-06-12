---
title: "The packages that come when you install a program"
date: 2009-08-31
forum: General Help
---

### Post by fuzzman54 on 2009-08-31
When you uninstall that program, how do you get rid of all of the packages that came bundled with it that aren't removed when you uninstall the program that was dependant on those? Do you have to just remember what all came and do it one by one?

---

### Post by SoftwareExplorer on 2009-08-31
I think it will uninstall them if you go to Applications->Accessories->Terminal and paste this in:
```
sudo apt-get autoremove
```
When it finishes, all those extra things should be removed.

---

### Post by CatKiller on 2009-09-01
If you're a graphical person, they'll show in Synaptic as auto-removable, too.

---

### Post by theozzlives on 2009-09-01
If you're talking dependencies, autoremove will work. To get rid of cached packages:
```
sudo apt-get clean
```

---

### Post by fuzzman54 on 2009-09-01
Why doesn't it get rid of the folders from the programs too?

---

### Post by P4man on 2009-09-01
the folders probably contain settings, and those aren't removed unless you use the -purge option.

---

### Post by dave r on 2009-09-01
You could use Computer Janitor to clean up your system, or use 
Not Installed (Residual Config) in Synaptic Package Manager

---

### Post by SoftwareExplorer on 2009-09-01
> **CatKiller said:**
> If you're a graphical person, they'll show in Synaptic as auto-removable, too.
I know I saw that somewhere in synaptic, but I couldn't find it.

---

### Post by S29K on 2009-09-01
In Synaptic, click on the 'Status' button in the lower left-hand side. This will change the options in the left-side pane to show some or all of the following:
 
All
Installed
Installed (Auto Removable)
Installed (Local Or Obsolete)
New In Repository
Upgradeable
Not Installed (Residual Config)
Not Installed

Click on one of the statuses and the package list will change in the right-side pane.  Right-click on the package(s) you want to remove and select 'Mark for Complete Removal' to uninstall and purge the config files for them.

---

### Post by fuzzman54 on 2009-09-01
> **P4man said:**
> the folders probably contain settings, and those aren't removed unless you use the -purge option.
Any way to do the purge option after the programs are already gone?

---

### Post by oldos2er on 2009-09-01
> **fuzzman54 said:**
> Any way to do the purge option after the programs are already gone?

 sudo apt-get purge <package name>

---

### Post by fuzzman54 on 2009-09-02
The package that came with the dependencies, or the dependencies themselves?

---

### Post by SoftwareExplorer on 2009-09-02
> **fuzzman54 said:**
> The package that came with the dependencies, or the dependencies themselves?
I'm pretty sure it just removes the configuration files for the packages you specify, not all its dependencies.

---

### Post by S29K on 2009-09-02
If you use Synaptic simply click on the 'Not Installed (Residual Config)' status and it will show your which 'uninstalled' packages still have config files left.

---

### Post by fuzzman54 on 2009-09-03
Just posting this for the next guy that comes asking.

Although all of your answers were helpful, they didn't do what I was actually wanting. The utility GtkOrphan does everything that I was asking for. So yeah.

---

### Post by S29K on 2009-09-03
Thanks for the info fuzzman.  I wonder why apt doesn't remove these non-essential libraries when it uninstalls the package that requires them.  

I assumed that any unnecessary packages were automagically removed if you no longer had any installed applications that required them.

---

