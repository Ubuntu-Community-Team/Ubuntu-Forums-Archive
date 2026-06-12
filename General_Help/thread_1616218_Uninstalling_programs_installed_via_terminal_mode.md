---
title: "Uninstalling programs installed via terminal mode?"
date: 2010-11-07
forum: General Help
---

### Post by daldude on 2010-11-07
How do you uninstall programs that were installed via terminal mode that don't appear in Ubuntu Software Center under Installed programs but do appear under the applications menu to be run and are properly installed and launch ok?
Programs with a deb extension in the file package that was used to install them.

The Program is Mobile Media Converter and this is what is under  properties when I check of it in the main menu setting under System  Preferences
/opt/MIKSOFT/MobileMediaConverter/MobileMediaConverter %F

To install it I typed sudo dpkg --force-architecture -i mmc_1.7.0_i386.deb

The program launches ok but will fail when it tries to convert any media files.

Sorry about the duplicate message below, I tried to delete it but I guess you can't do that or I don't know how to do it.

---

### Post by Barriehie on 2010-11-07
> **daldude said:**
> How do you uninstall programs that were installed via terminal mode that don't appear in Ubuntu Software Center under Installed programs but do appear under the applications menu to be run and are properly installed and launch ok?
Programs with a deb extension in the file package that was used to install them.

So you installed a package that you retrieved from somewhere other than the repos?  If not retrieved from the repos did you use gdebi to install it?

---

### Post by goinglinux on 2010-11-07
> **daldude said:**
> How do you uninstall programs that were installed via terminal mode that don't appear in Ubuntu Software Center under Installed programs but do appear under the applications menu to be run and are properly installed and launch ok?
Programs with a deb extension in the file package that was used to install them.

Assuming you used apt-get install <package> to do the installation, you can use the following to uninstall:
```
sudo apt-get remove <package>
```

---

### Post by bioterror on 2010-11-07
Commands are:

```
dpkg -r
dpkg -P
```

And more about this from "man dpkg"

> 
dpkg -r | --remove | -P | --purge package ... | -a | --pending
Remove an installed package. -r or --remove remove everything except configuration files. This may avoid having to reconfigure the package if it is reinstalled later. (Configuration files are the files listed in the debian/conffiles control file). -P or --purge removes everything, including configuration files. If -a or --pending is given instead of a package name, then all packages unpacked, but marked to be removed or purged in file /var/lib/dpkg/status, are removed or purged, respectively


---

### Post by goinglinux on 2010-11-07
Something else you might try:

I have noticed that with the Software Center, not every installed .deb package appears in the list if you click on "Installed Software". On the other hand, if you use the search box to search for the package by name, you will find it and be able to install it from the main window.

---

### Post by uRock on 2010-11-07
Installed debs should be visible and easily removed in Synaptic Package Manager.

---

### Post by daldude on 2010-11-08
I figured it out. I extracted the [COLOR=Red]** libfaac**[/COLOR] files from the deb package using archive manager and now it works.

---

