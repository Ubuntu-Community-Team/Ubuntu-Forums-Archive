---
title: "what  happened to my firefox?"
date: 2012-01-27
forum: General Help
---

### Post by bpb101 on 2012-01-27
something is seriously wrong with my firefox.
list: 
ALL my bookmarks are gone(synced tho)
The back buttons aren't highlighted ,to go back(but right clicking drops down past pages)
  When i search for something the links are in Black
  when Firefox does ANY work it goes slightly black.(this use to happen in rare cases under high pressure but it constantly now )

what has happened ...

backround: i had nytimes.com as homepage and i simple changed it back to google.

Running firefox 9.0.1 , ubuntu 11.10 

screen shot included 
half crashed a few times during the search

IVE TRYED UNISTALL . INSTALL AND NOPE.

Thanks
*Barry*

---

### Post by wolfen69 on 2012-01-27
Uninstall firefox again, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
then open your home folder and do Ctrl+H. Delete the .mozilla folder. Reinstall firefox.

---

### Post by bpb101 on 2012-01-27
seams to be working again thanks

---

