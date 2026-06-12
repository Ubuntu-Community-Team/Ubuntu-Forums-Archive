---
title: "maintenance"
date: 2010-04-01
forum: General Help
---

### Post by UncleMonty on 2010-04-01
Are there any commands or software that can do any of the following:

cache cleaner
orphan removal

---

### Post by oldos2er on 2010-04-01
If you're referring to the package (apt) cache, you can clear it with ```
sudo apt-get clean
```

```
sudo apt-get autoremove
``` will uninstall any "leftover" dependencies of packages that are no longer installed. Also look up the commands deborphan and debfoster.

---

### Post by waj1122 on 2010-04-01
Try this:

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

Very similar to ccleaner for windows.

---

### Post by SnickerSnack on 2010-04-01
> **UncleMonty said:**
> Are there any commands or software that can do any of the following:

cache cleaner
orphan removal

System > Administration > Computer Janitor

---

### Post by ajgreeny on 2010-04-01
> **SnickerSnack said:**
> System > Administration > Computer Janitor
But be careful to check what this shows as removable first before you simply let it do its job.

It will very often suggest removal of third party apps you have installed, such as in my case, **compiz-switch**, **easymp3gain-gtk**, and worst of all, **songbird**, all applications I installed and not from the ubuntu repos or a ppa.  That doesn't mean I want them to be removed, however, so just watch out.

---

### Post by ssulaco on 2010-04-01
> **waj1122 said:**
> Try this:

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

Very similar to ccleaner for windows.
Make sure "Places" is Unchecked,or you will wipe your bookmarks.
> Q: How can I delete Firefox URL history without deleting bookmarks?
A: Uncheck Places and check URL history. Firefox version 3 stores bookmarks, favicons, and URL history in a single file called the Places database.

---

