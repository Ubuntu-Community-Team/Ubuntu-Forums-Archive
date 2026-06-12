---
title: "recent questions posted on forum"
date: 2010-05-11
forum: General Help
---

### Post by colorlessprism on 2010-05-11
recently both here and on launchpad i have noticed a number of people experiencing GPG errors. i've looked around an decided to consolidate some information in hopes of helping people out.
   
_**PPA GPG ERROR FIXES:**_

[LIST]
[*]Dominic Evans script launchpad-update (see attached). save this script and run it if you find yourself needing GPG keys, this is the fastest way to update key information. it works for current ppas but add-apt-reposiroty may soon replace it.
[/LIST]
 
[LIST]
[*]to fix these errors in _lucid_ use "sudo add-apt-repository ppa:<repository name>" this registers the ppa with APT and an entry is created in /etc/apt/sources.list  and backs up to /etc/apt/sources.list.save. ff a key is required and available it is automatically downloaded and  registered. you must have "python-software-properties" installed before using this command
[/LIST]
 
[LIST]
[*] you can go to the ppa page click on the green link saying "technical  details about this PPA", select your version from  the drop down, click the "Signing Key" link and it should take you to a keyserver page. Copy and paste gpg public code to your favorite editor, and  save it.  open "software sources" and select "authentication" click the "Import Key File", and select the  file you just saved. now reload your sources
[/LIST]
 if anyone else has other methods please post them here.

---

### Post by blazemore on 2010-05-13
I'll bump this, I had to help someone with this just now

---

