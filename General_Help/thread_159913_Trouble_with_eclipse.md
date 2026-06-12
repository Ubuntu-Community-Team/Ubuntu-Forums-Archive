---
title: "Trouble with eclipse"
date: 2006-04-13
forum: General Help
---

### Post by Brok3n_Sword on 2006-04-13
I get this error when trying to edit Java files in eclipse.  Any ideas how to fix it?

[IMG]http://img49.imageshack.us/my.php?image=screenshot5hk.png[/IMG]

In case you can't see it:  [http://img49.imageshack.us/my.php?image=screenshot5hk.png](http://img49.imageshack.us/my.php?image=screenshot5hk.png)

---

### Post by Brok3n_Sword on 2006-04-13
Anyone?  I need to get this done for an assignment, and don't want to boot into Windows just to write some Java code.

---

### Post by testube_babies on 2006-04-14
The first thing you should try is to configure your default java packages.  You may need to repeat this step, replacing "java" with "jar", "javadoc", "javac", "javah", "javap", and "javaws"

```
sudo update-alternatives --config java
```

If that doesn't work, you may have to reinstall the Java JDK.  See the bottom portion of this page:

[http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)


If neither of these works, reinstall eclipse.  Just download the new version from eclipse.org and untar it.  You should be good to go.

---

### Post by testube_babies on 2006-04-14
I also just noticed that there are no files in your navigator panel.  Did you set up a default workspace?

---

