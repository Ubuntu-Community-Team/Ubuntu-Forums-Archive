---
title: "Produce a list of programmes I have installed"
date: 2011-10-28
forum: General Help
---

### Post by inearlygaveup on 2011-10-28
Is their an easy way to produce a printable list of programmes _that I have installed_ before I upgrade.
The Software Centre gives everything but also includes Ubuntu pre installed stuff.

---

### Post by zvacet on 2011-10-30
You can look in synaptic>history and see if that help.

---

### Post by Wayne_V on 2011-10-30
dpkg --list | grep "^i"

---

### Post by oldfred on 2011-10-30
If you use the synaptic or dpkg list, it will not reinstall those.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

You also need to check sources:
But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup

Top level applications:
aptitude --disable-columns -F 'no_dependents %p' search '~i!~M!~R(~i)'

List with explanations of programs, not for reinstall
dpkg -l > ~/installed_programs.txt

I do not think this is just the manually installed list:
A tabular list of all manually installed packages can be obtained using:
aptitude search '~i!~M'

I find using dpkg, I get a lot of older packages & have to houseclean list before reinstalling. For example I found I was still installing python2.5 and now my list still have OpenOffice which has been replaced by LibreOffice.

If you create a list from a new install you can use this to compare, or use diff or meld, etc:
HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

### Post by Wayne_V on 2011-10-30
or, if you want to see a list of packages that are installed but are NOT in the apt repos try this:

dpkg --list | grep "^i" | awk '{print $2}' | while read P ; do apt-cache search $P >/dev/null || echo "$P not in repo" ; done

---

### Post by inearlygaveup on 2011-10-30
Thanks everyone I manually listed them from the Software Centre, fortunately there were not to many.

---

### Post by zvacet on 2011-10-30
> I find using dpkg, I get a lot of older packages & have to houseclean list before reinstalling. For example I found I was still installing python2.5 and now my list still have OpenOffice which has been replaced by LibreOffice.

With that method ( using dpkg) you get list of installed and packages you uninstalled.That is why you see  OpenOffice on the list.With 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages
```

and if you want to install them on other comp 

```
sudo xargs aptitude --schedule-only install < my-packages
sudo aptitude install
```

---

