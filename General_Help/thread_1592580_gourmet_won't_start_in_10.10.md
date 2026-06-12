---
title: "gourmet won't start in 10.10"
date: 2010-10-10
forum: General Help
---

### Post by brashley46 on 2010-10-10
Just upgraded to 10.10 and now gourmet won't start. Running in terminal gives: 
```
brashley46@ross-desktop:~$ gourmet
/usr/share/gourmet/gourmet/backends/db.py:294: SADeprecationWarning: The Binary type has been renamed to LargeBinary.
  Column('image',Binary(),**{}),
/usr/share/gourmet/gourmet/backends/db.py:295: SADeprecationWarning: The Binary type has been renamed to LargeBinary.
  Column('thumb',Binary(),**{}),
Traceback (most recent call last):
  File "/usr/bin/gourmet", line 35, in <module>
    gourmet.GourmetRecipeManager.startGUI()
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 715, in startGUI
    r=RecGui(splash_label=splash.label)
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 917, in __init__
    GourmetApplication.__init__(self, splash_label=splash_label)
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 114, in __init__
    self.setup_recipes() # Setup recipe database
  File "/usr/share/gourmet/gourmet/GourmetRecipeManager.py", line 204, in setup_recipes
    self.rd = recipeManager.default_rec_manager()
  File "/usr/share/gourmet/gourmet/recipeManager.py", line 131, in default_rec_manager
    return get_recipe_manager(**dbargs)
  File "/usr/share/gourmet/gourmet/recipeManager.py", line 126, in get_recipe_manager
    return RecipeManager(**args)
  File "/usr/share/gourmet/gourmet/backends/db.py", line 1742, in __init__
    self.km = keymanager.get_keymanager(rm=self)
  File "/usr/share/gourmet/gourmet/keymanager.py", line 531, in get_keymanager
    return KeyManager(*args,**kwargs)
  File "/usr/share/gourmet/gourmet/keymanager.py", line 40, in __init__
    self.initialize_categories()
  File "/usr/share/gourmet/gourmet/keymanager.py", line 81, in initialize_categories
    for k in self.rm.get_unique_values('ingkey',self.rm.ingredients_table,deleted=False):
  File "/usr/share/gourmet/gourmet/backends/db.py", line 797, in get_unique_values
    if not table: table=self.recipe_table
  File "/usr/lib/python2.6/dist-packages/sqlalchemy/sql/expression.py", line 1296, in __nonzero__
    raise TypeError("Boolean value of this clause is not defined")
TypeError: Boolean value of this clause is not defined
brashley46@ross-desktop:~$
```

What can be done about this?

---

### Post by brashley46 on 2010-10-11
I uninstalled it, went to Sourceforge and downloaded and installed the gourmet_0.15.6-2_all.deb package - it works.

---

### Post by Mr. Picklesworth on 2010-10-14
Looks like a critical bug nobody noticed. I filed a bug report here:
[https://bugs.edge.launchpad.net/ubuntu/+source/gourmet/+bug/660748](https://bugs.edge.launchpad.net/ubuntu/+source/gourmet/+bug/660748)

---

### Post by brashley46 on 2010-10-14
> **Mr. Picklesworth said:**
> Looks like a critical bug nobody noticed. I filed a bug report here:
[https://bugs.edge.launchpad.net/ubuntu/+source/gourmet/+bug/660748](https://bugs.edge.launchpad.net/ubuntu/+source/gourmet/+bug/660748)
Thanks! I did not know enough about the code to do that. I'll stick with my downloaded version until the repositories catch up.

---

### Post by gregorydillon on 2010-10-28
Yeah, this is happening to me too.    Frustration combined with some relief that it was not me who did something wrong.

---

### Post by brashley46 on 2010-10-28
> **gregorydillon said:**
> Yeah, this is happening to me too.    Frustration combined with some relief that it was not me who did something wrong.

As I said, though, the Sourceforge download version works just fine. So go thou and get unfrustrated. (Wanna recipe for blueberry clafouti?)

:)

---

### Post by Killerkaninchen on 2010-10-31
It's the same TypeError when using griffith for searching my movie database. So I think it has something to do with sqlalchemy. I found some threads on the internet:

[http://www.linuxquestions.org/questions/linux-software-2/gourmet-recipe-manager-not-starting-in-ubuntu-10-10-a-841196/](http://www.linuxquestions.org/questions/linux-software-2/gourmet-recipe-manager-not-starting-in-ubuntu-10-10-a-841196/)
[http://forum.griffith.cc/index.php?topic=1099.0](http://forum.griffith.cc/index.php?topic=1099.0)
[http://forum.ubuntuusers.de/topic/durchsuchen-der-film-datenbank-bei-griffith-ni/#post-2667070](http://forum.ubuntuusers.de/topic/durchsuchen-der-film-datenbank-bei-griffith-ni/#post-2667070) (my german griffith-thread)

But they have no other solutions...

---

### Post by labatts on 2010-11-25
Not for me =(. would definitely like a solution here.  I am regretting not using 'cookbooks' right now...

---

### Post by brashley46 on 2010-11-26
> **labatts said:**
> Not for me =(. would definitely like a solution here.  I am regretting not using 'cookbooks' right now...

Go to [http://sourceforge.net/projects/grecipe-manager/files/0.15.6/gourmet_0.15.6-2_all.deb/download]("http://sourceforge.net/projects/grecipe-manager/files/0.15.6/gourmet_0.15.6-2_all.deb/download") and download the latest version, works for me; or wait for the Ubuntu repository to be updated per this thread: [bugs.edge.launchpad.net/ubuntu/+source/gourmet/+bug/618643]("http://bugs.edge.launchpad.net/ubuntu/+source/gourmet/+bug/618643")

---

### Post by Trapper on 2011-01-02
Fedora had the same difficulty with the release of Fedora 14. It's a compatibility problem with the gourmet software itself. U-10.10 has libraries the current version of gourmet was not designed for. It doesn't mean gourmet is a bad app. It just means Ubuntu is only offering an older version that doesn't work with the new libraries. The way to fix it is to get a more recent release. Use the version at sourceforge. The repositories will eventually catch up.

Here's a direct link:

[http://sourceforge.net/projects/grecipe-manager/files/0.15.6/](http://sourceforge.net/projects/grecipe-manager/files/0.15.6/)

---

