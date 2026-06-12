---
title: "Nautilus fails to open Places in Gnome Classic"
date: 2011-10-31
forum: General Help
---

### Post by robbielink on 2011-10-31
Clicking anything in "places" tries to start Nautilus but then it gives up and never opens. Home, desktop, documents, computer - nothing opens. "Search for files" DOES work and also clicking a folder on the desktop will open the file manager just fine. I can also launch nautilus from the command line. It's only clicking the links in Places that doesn't work.

I've tried the various fixes I've found - removing nautilus open terminal, the ubuntuone integration, adding a line to mimetypes for nautilus - no change. Suggestions?

Fresh install of 11.10 but kept my "home" on a separate partition. Have to use Gnome Classic (regular or "no effects" both work) due to older hardware.

---

### Post by WasMeHere on 2011-10-31
> **robbielink said:**
> ... Fresh install of 11.10 but kept my "home" on a separate partition. Have to use Gnome Classic (regular or "no effects" both work) due to older hardware.

Hi robbielink,

I suggest that you download Xubuntu, Lubuntu or Linux Mint 11 and try them live from a CD or USB drive. Sometimes you have to try a few different flavors or versions before you find something that cooperates well with your hardware. Or simply revert back to your previous version (11.04?) and wait for some weeks, while the worst bugs are found and fixed in 11.10.

Have fun finding out :-)
Olle

---

### Post by robbielink on 2011-10-31
> **Olle Wiklund said:**
> 
I suggest that you download Xubuntu, Lubuntu or Linux Mint 11 and try them live from a CD or USB drive. 


Thanks, Olle. 
Actually, I'm quite happy with 11.10 and Gnome Classic except for this one little issue. I did try the XFCE desktop and didn't like it. I know Gnome Classic will probably go away in future versions but right now this old Presario laptop is running zippier than ever. I tried a live CD of 11.10 before installing and oddly enough even Unity worked and looked great. Tried updating and it totally trashed my system so did a new install (but kept my old Home) and now Unity doesn't work at all (even 2D) but no matter - I didn't like it anyway. (add me to the "I hate Unity" list). It's the Intel graphics chip problem.

At any rate - I suspect the problem I'm having with Nautilus is due to some residual configuration file or an incorrect path somewhere. Somewhere I read about deleting a .nautilus file of some kind in my home directory (can't remember exactly what it was called) but I didn't have that file. So - that's the route I'm looking for answers in - where to search/what to look for that might be a configuration issue.

Thanks for your suggestions, though.

---

### Post by WasMeHere on 2011-10-31
In that case, would you dare to uninstall nautilus and after that reinstall it again. Before you do it, please read ```
man apt-get
``` carefully! I think you could use the following commands to get rid of some garbage, that may cause problems.
```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

---

### Post by robbielink on 2011-10-31
> **Olle Wiklund said:**
> In that case, would you dare to uninstall nautilus and after that reinstall it again.
```
sudo apt-get purge nautilus
sudo apt-get install nautilus
```

Yep - tried that already. First time used sudo apt-get remove and reinstalled. Then remembered purge might be better so did that. No change but I've "purged" other programs and still found residual config files lying around.

Someone suggested deleting the .nautilus configuration file from my home directory but I didn't have one there. What I did find was this (minus all the translations):
~/.local/share/applications/nautilus.desktop

[Desktop Entry]
Categories=GNOME;GTK;Utility;Core;
Comment=Browse the file system with the file manager
Encoding=UTF-8
Exec=nautilus --no-desktop --browser %U
Icon=system-file-manager
Name=File Browser
NoDisplay=false
OnlyShowIn=GNOME;
StartupNotify=true
Terminal=false
TryExec=nautilus
Type=Application
X-GNOME-Autostart-Notify=true
X-GNOME-Autostart-Phase=Desktop
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Product=nautilus
X-GNOME-Bugzilla-Version=2.24.1
X-GNOME-Provides=filemanager
X-Ubuntu-Gettext-Domain=nautilus

Wondering if there's anything unusual there or if there's another place to look for any kind of config file. I just wonder if since I did a new install but kept my old home directory on a different partition (which the new install seemed to find) if maybe some files got put somewhere else or lost.

---

### Post by WasMeHere on 2011-10-31
I think you are right about the home directory, that the installation seemed to discover. That might be causing the problem. It might also be a bug of the operating system.

I don't have any more ideas right now. Maybe someone else reading this thread?

---

### Post by cbowman57 on 2011-10-31
You might want to delete the contents of this ~/.config/nautilus

Don't know if it will help but it's a start.

---

### Post by robbielink on 2011-11-01
> **cbowman57 said:**
> You might want to delete the contents of this ~/.config/nautilus

Don't know if it will help but it's a start.

Hey Chuck! That did it!
The file I had found apparently was from an old configuration and no longer used as removing that had no effect. I un-installed Nautilus and removed .config/nautilus as you suggested, re-installed and that fixed my problem after a restart.
Thanks!!!

---

### Post by cbowman57 on 2011-11-01
Outstanding, glad it worked. :)

---

### Post by cscj01 on 2012-02-13
I had a problem with Gimp described here:[//http://ubuntuforums.org/showthread.php?p=11678629]("http://http://ubuntuforums.org/showthread.php?p=11678629").  After adding the PPA's and going through the install steps, Gimp is fine, but I can no longer launch Nautilus from the Places Menu.  I can launch Nautilus from a Terminal or by opening a disk on my desktop.  But that is inconvienent.  I deleted the contents of ~/.config/nautilus, but that did not help.  I do not have any desktop files with the --browser issue.  I have not tried removing and reinstalling Nautilus as yet.  Anyone have any ideas?

---

