---
title: "Removing packages via Synaptics"
date: 2010-08-02
forum: General Help
---

### Post by inearlygaveup on 2010-08-02
When removing packages via Synaptics it gives the option of 
[LIST=1]
[*]Mark for removal
[*]Mark for complete removal
[/LIST]
If I mark it for complete removal does it mean it will never be available from Synaptics again or does it mean that the whole package will be deleted from my system and have to be downloaded again if I want to install it again.
I am never sure which to pick

---

### Post by Smart Viking on 2010-08-02
> **inearlygaveup said:**
> When removing packages via Synaptics it gives the option of 
[LIST=1]
[*]Mark for removal
[*]Mark for complete removal
[/LIST]
If I mark it for complete removal does it mean it will never be available from Synaptics again or does it mean that the whole package will be deleted from my system and have to be downloaded again if I want to install it again.
I am never sure which to pick

mark for complete removal that means like it will delete the configuration files in the home folder and that stuff i think, it basically removes every trace of that the program have been installed. But you can STILL install it again anyways. :)

---

### Post by mcduck on 2010-08-02
"Mark for removal" uninstalls the program but leaves all configuration files around.

"Mark for complete removal" uninstalls the program and deletes it's configuration files from your computer. (only system-wide configuration files, though, each user's own configurations will still be left around as they belong to those users and should never be automatically removed by admins tasks like this). 

Neither one will remove anything from Synaptic, the package manager will always list all the packages that are available in all the software repositories you have configured.

Edit: Whatever you remove with Synaptic (or other package management tools) won't effect the cached packages on your computer. To remove them you'd have to run "sudo apt-get clean" (or just delete them manually from /var/cache/apt/archives).

---

### Post by WorMzy on 2010-08-02
[QUOTE="https://help.ubuntu.com/community/SynapticHowto#Remove%20or%20Uninstall%20Packages"]The Mark for Complete Removal option instructs Synaptic to remove any configuration files associated with the package as well.[/QUOTE]

The package will still be available for reinstallation, assuming that it hasn't been removed from the repos. :)

---

### Post by Cavsfan on 2010-08-02
Complete uninstall will delete it and if you want to re-install the program, it will have to be re-downloaded.
If you just uninstall it, it will not need to be re-downloaded to be re-installed.

---

### Post by mcduck on 2010-08-02
> **Cavsfan said:**
> Complete uninstall will delete it and if you want to re-install the program, it will have to be re-downloaded.
If you just uninstall it, it will not need to be re-downloaded to be re-installed.

Sorry, but this is not true.

Like I said, the only difference between the two options is how they handle system-wide configuration files that belong to the package.

If you install a program the package manager will always first check the apt's cache directory in case the package is there. If yes (and there isn't any new version available in any of your repositories), the cached package will be used instead of downloading it again.

Uninstalling a package has no effect on what's stored in cache, unless you have yourself configured Synaptic to only keep cache for packages that are currently installed on your system. By default it will keep every package you have installed until you remove them yourself.

So, in most cases, the package manager won't have to re-download the package if you remove it and then install it again at later time. It  only needs to do that if you have yourself removed the cached package, or if there's a later version of the same package available in the repositories.

---

### Post by inearlygaveup on 2010-08-02
Thanks for all your help - I have been meaning to ask for ages.):P

---

### Post by Cavsfan on 2010-08-02
> **Cavsfan said:**
> Complete uninstall will delete it and if you want to re-install the program, it will have to be re-downloaded.
If you just uninstall it, it will not need to be re-downloaded to be re-installed.

> **mcduck said:**
> Sorry, but this is not true.

Like I said, the only difference between the two options is how they handle system-wide configuration files that belong to the package.

If you install a program the package manager will always first check the apt's cache directory in case the package is there. If yes (and there isn't any new version available in any of your repositories), the cached package will be used instead of downloading it again.

Uninstalling a package has no effect on what's stored in cache, unless you have yourself configured Synaptic to only keep cache for packages that are currently installed on your system. By default it will keep every package you have installed until you remove them yourself.

So, in most cases, the package manager won't have to re-download the package if you remove it and then install it again at later time. It  only needs to do that if you have yourself removed the cached package, or if there's a later version of the same package available in the repositories.

Thanks for your correction! I wasn't absolutely sure, but know I know. Thanks! :)

---

