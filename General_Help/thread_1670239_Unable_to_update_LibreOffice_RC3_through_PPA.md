---
title: "Unable to update LibreOffice RC3 through PPA"
date: 2011-01-18
forum: General Help
---

### Post by lbarnes on 2011-01-18
Hey guys, I had LibreOffice RC2 installed through the libreoffice ppa on my 10.10 64 Ubuntu system and was waiting for the ppa to update before installing RC3. Well, today RC3 was released and I am unable to update through Update Manager or Terminal:
```
lennon@lennon-HP-HDX-16-Notebook-PC~ $ sudo apt-get upgrade
[sudo] password for lennon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-core libreoffice-draw libreoffice-filter-binfilter libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-writer python-uno
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
lennon@lennon-HP-HDX-16-Notebook-PC~ $

```

```
lennon@lennon-HP-HDX-16-Notebook-PC~ $ sudo apt-get install libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-core (= 1:3.3.0~rc3-2maverick1) but 1:3.3.0~rc2-3maverick1 is to be installed
               Depends: libreoffice-java-common (>= 1:3.3.0~rc3~) but 1:3.3.0~rc2-3maverick1 is to be installed
E: Broken packages
lennon@lennon-HP-HDX-16-Notebook-PC~ $ 

```
I was wondering if anyone was waiting like I was and was able to update through the ppa today. I'm thinking that the likely reason is that RC2 should be completely removed for RC3 to be installed. If that's the case what is the ideal way to remove RC2 properly? Thanks for any suggestions.

---

### Post by TGBaker on 2011-01-18
I doubt that it should be removed. A Ubuntu package is not showing up for me. It could be that RC3 is out but not the Ubuntu packaging.

---

### Post by lbarnes on 2011-01-18
Are you already on RC3? That would explain it not showing up for you if you're using the libreoffice ppa. I attached a screenshot showing Update Manager listing the libreoffice packages. I don't want to remove RC2 if RC3 will still not install, so I'll hold off on that for now.

---

### Post by TGBaker on 2011-01-18
My LibreOffice shows RC2-3.  I wonder if we are using two different PPA's?

[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) maverick

But then I'm not showing the update???

---

