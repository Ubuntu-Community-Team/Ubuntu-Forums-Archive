---
title: "reverting from gnome 3 to 11.04"
date: 2011-04-30
forum: General Help
---

### Post by slgtheindividual on 2011-04-30
Ok so I basically accidentally installed gnome3 on ubuntu tweak (I didn't notice the box was checked) and next time I started up I could only use the gnome 3 environment which is massively buggy. I wish to revert back to 11.04 (without a clean install, since I have a lot of files I need to keep). I have tried purging the gnome3 team ppa but I get the following error: 

"sudo ppa-purge ppa:gnome3-team/gnome3/
Updating packages lists
PPA to be removed: gnome3-team/gnome3 ppa
Warning:  Could not find package list for PPA: gnome3-team/gnome3 ppa"

---

### Post by iamcowdrunk on 2011-04-30
Just curious, did you unselect the gnome3 ppa in ubuntu tweak before running ppa-purge? If so try re-enabling the ppa and then 'ppa-purge gnome3-team/gnome3'

---

