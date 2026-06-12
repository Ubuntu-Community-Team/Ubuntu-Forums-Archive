---
title: "apt-get Problem"
date: 2006-01-28
forum: General Help
---

### Post by gunderwood on 2006-01-28
I'm having an issue with a bad package, libssl. The package will not install, whenever it does it breaks apt and I need to run dpkg --configure -a to fix it. But the real kicker is that now every time I try and install anything apt-get wants to upgrade libssl. (actually install because it never actually installed)  I've tried to remove the package, apt-get clean, but no matter what the package is still sitting there wanting to be installed. 

Greg

---

### Post by o_fortuna on 2006-01-28
[QUOTE=gunderwood]I'm having an issue with a bad package, libssl. The package will not install, whenever it does it breaks apt and I need to run dpkg --configure -a to fix it. But the real kicker is that now every time I try and install anything apt-get wants to upgrade libssl. (actually install because it never actually installed)  I've tried to remove the package, apt-get clean, but no matter what the package is still sitting there wanting to be installed. 

Greg[/QUOTE]
I had a similar problem with a different package. The only solution I could find was to download off the internet a copy of the package as the one in the repositories was somehow messed up.

Frankly, though, I just did a google search and came up nil. You could try a google search to see if you can find a .deb for libssl.

If you can find one (yay!) then download it to the desktop and do this at the command line:
```
cd Desktop
sudo dpkg Name_of_Package.deb
```
This should replace your old version, meaning you can uninstall it so that it'll stop causing problems.

---

### Post by gunderwood on 2006-01-29
Thank you for your suggestion o_fortuna, unfortunately any package I was able to locate also broke during the installaion. Something about a broken pipe. Anyway for anyone interested I was able to resolve the issue. I found that the package was in a half installed state. So every time I was running apt-get it was trying to install the package all the way. Apparently when youy have a half installed package before removing it apt attempts to install it all the way then uninstall the package.

dpkg --remove --force-remove-reinstreq libssl-dev

That cleaned up the package and I was back in business.

Greg

---

