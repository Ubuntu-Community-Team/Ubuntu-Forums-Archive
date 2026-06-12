---
title: "Uninstalling software from Ubuntu Software Centre breaks dependencies"
date: 2010-06-19
forum: General Help
---

### Post by mister.zee.man on 2010-06-19
I've just installed UNR 10.04 on a netbook with a very small harddrive. I've gone on to try and slim everything down but keep running into dependency issues. 
Removing gnome-games, openoffice.org (not required),  evolution (I use Thunderbird) and rhythmbox (Amarok all the way, baby) seems a no go, as does removing unneeded xorg drivers. I've tried using apt, synaptic and software centre. 
I've also tested this on my x86_64 install, and the same applies (although space is less of an issue, I'd still like to get rid of stuff I have no intention of using). As it is, there's little room on my netbook for files now, or indeed the software I was planning to put on it in the first place. :frown:
Is there any way I can get around this issue without switching to another eee variant?

---

### Post by mister.zee.man on 2010-06-20
Bump

---

### Post by XSAlliN on 2010-06-20
> Is there any way I can get around this issue without switching to another eee variant?

No. It's the way Ubuntu is build, some dependencies are not vital but others (like evoulution) can also remove the GUI. Which normally - it's not related (since is not a GUI dependency - like for Gnome), yet that's the way Ubuntu was built. For Ubuntu many tools come in Packs, you can't remove one without the rest. 

Yet, I do admit - even I hate this about ubuntu (forcing me to keep even what I don't need/use - ever). :frown:

---

### Post by arrange on 2010-06-20
Could you give us the output of the removal commands? For example```
apt-get --dry-run remove openoffice.org
```(This will actually not remove anything, see the *--dry-run* option.)

---

### Post by XSAlliN on 2010-06-20
I don't see any major dependency for OpenOffice.org:

[IMG]http://img820.imageshack.us/img820/5406/screenshovvxcvxt.png[/IMG]

-if you use synaptic to uninstall you can also see the dependencies and it's also cleaner.

---

### Post by mister.zee.man on 2010-06-24
Intriguing - Synaptic, Software Centre, apt and dpkg gave no errors when removing -  however when I ran apt-get install i got:

The following packages are BROKEN:
  rhythmbox-plugin-cdrecorder 
0 packages upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
Need to get 0B/13.9kB of archives. After unpacking 147kB will be used.
The following packages have unmet dependencies:
  rhythmbox-plugin-cdrecorder: Depends: rhythmbox (= 0.12.8-0ubuntu6) but it is not installable
The following actions will resolve these dependencies:

Install the following packages:
rhythmbox [0.12.8-0ubuntu3 (lucid)]
rhythmbox-plugin-cdrecorder [0.12.8-0ubuntu3 (lucid)]
rhythmbox-plugins [0.12.8-0ubuntu3 (lucid)]

Score is 22

Accept this solution? [Y/n/q/?] 

Of course, none of these are actually installed.
I uninstalled the openoffice.org meta-package and am getting no more complaints about that, although I suspect this is because I've left openoffice.org.core alone. Still have the apps in the menu too. :confused:
Btw, I have all of this scripted from previous installs - this is the first time I've had issues of this sort. My lucky day I guess...

---

### Post by mister.zee.man on 2010-06-24
Right, removed openoffice.org-core, and that got rid of the software. Now apt-get install gives me this:

The following packages are BROKEN:
  rhythmbox-plugin-cdrecorder 
The following NEW packages will be installed:
  openoffice.org-base-core openoffice.org-core openoffice.org-gnome 
  openoffice.org-gtk openoffice.org-l10n-common openoffice.org-l10n-en-gb 
  openoffice.org-l10n-en-za openoffice.org-thesaurus-en-us python-uno 
0 packages upgraded, 10 newly installed, 0 to remove and 0 not upgraded.
Need to get 46.4MB of archives. After unpacking 171MB will be used.
The following packages have unmet dependencies:
  rhythmbox-plugin-cdrecorder: Depends: rhythmbox (= 0.12.8-0ubuntu6) but it is not installable
The following actions will resolve these dependencies:

Keep the following packages at their current version:
rhythmbox-plugin-cdrecorder [Not Installed]

Score is 119

Humph... Still, Just got plymouth running in hi-res glory, so not all is bad :p.

---

