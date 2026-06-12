---
title: "Ubuntuzilla Script Question"
date: 2010-01-16
forum: General Help
---

### Post by sports fan Matt on 2010-01-16
Since I have installed the new Ubuntuzilla script from here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla), which folders for the ubuntu firefox & thunderbird can i delete in my home directory and keep everything intact? 

thanks for any help.

---

### Post by jamesisin on 2010-01-16
I'm hearing that this is now a better method for getting Tb3:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Go figure.

---

### Post by sports fan Matt on 2010-01-16
So far it is...I have the official versions of both programs.

---

### Post by jamesisin on 2010-01-16
There is some small mentions of things to be removed on that page I linked above, but I did remove Tb2 through Synaptic.

---

### Post by nanotube on 2010-01-16
> **sox fan Matt said:**
> Since I have installed the new Ubuntuzilla script from here: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Welcome_to_Ubuntuzilla), which folders for the ubuntu firefox & thunderbird can i delete in my home directory and keep everything intact? 

thanks for any help.

Hi
Well first, i hope by 'the new ubuntuzilla script' you mean 'the new ubuntuzilla repository' :)

Second, if you have a bunch of old directories of the type ".mozilla_backup_xxxxx", or ".thunderbird_backup_xxxxx" you can delete them since they are just backups made by the old ubuntuzilla script. (that is, if you don't need the backups, of course).

besides that, there's nothing else to be deleting.

---

### Post by sports fan Matt on 2010-01-16
That was it..it works like a charm :)

---

### Post by sports fan Matt on 2010-01-16
I do have a mozilla thunderbird and a seperate thunderbird folder.  If i deleted one, would it hurt and which one if I could delete one, should I choose?

---

### Post by mkvnmtr on 2010-01-16
I would not delete anything. I would back up like it says in the instructions. When I used the Ubuntuzill repository I uninstalled the app I wanted to install and then installed from the new update with the new repository. I did not fool with my home directory.

---

### Post by nanotube on 2010-01-16
> **sox fan Matt said:**
> I do have a mozilla thunderbird and a seperate thunderbird folder.  If i deleted one, would it hurt and which one if I could delete one, should I choose?

here is where to be careful. check both folders and see what the contents are. usually the mozilla build uses .thunderbird for mail storage, and the ubuntu-repos version uses .mozilla-thunderbird. 

before doing any deleting, check to see what's inside, and try renaming rather than removing, to make sure that everything still works.

and, as mentioned in the post above - having backups of your data is always a very good idea - so i hope you're not doing anything that can't be undone. :)

---

### Post by nanotube on 2010-01-16
> **mkvnmtr said:**
> I would not delete anything. I would back up like it says in the instructions. When I used the Ubuntuzill repository I uninstalled the app I wanted to install and then installed from the new update with the new repository. I did not fool with my home directory.

indeed, there's no real need to delete anything unless you're low on space or just want to "keep it clean". and indeed, having backups of data is important.

---

