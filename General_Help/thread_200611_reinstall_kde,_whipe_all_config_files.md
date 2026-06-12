---
title: "reinstall kde, whipe all config files?"
date: 2006-06-20
forum: General Help
---

### Post by scpike on 2006-06-20
Ok, I've beeen using ubuntu since hoary, and dist-upgraded each time.  I use gnome for most of my stuff. but i had kde installed to mess around with it.  Its gotten pretty messy, though, sound doesnt work (althought it works in gnome) and there are assorted other issues, so i want to reinstall kde, with all the kde config files overwritten.  what is the command for this.

is it something like apt-get reinstall -purge k* ?

thanks for the help

---

### Post by bruce89 on 2006-06-20
You'll have to completly remove KDE - [http://www.psychocats.net/ubuntu/puregnome.php](http://www.psychocats.net/ubuntu/puregnome.php), but remember to purge the config files, not sure how you do that.
Then reinstall KDE - ```
sudo aptitude install kubuntu-desktop
```

---

### Post by hvbakel on 2006-06-20
Another perhaps less drastic measure may be to logout from kde, enter console mode (ctrl+alt+F1) and delete (or move) the .kde folder from your home disk. When you login to kde after that, a brand new .kde folder will be generated with the default kubuntu settings. In case the default configuration files from kubuntu got messed up somehow this won't work and you may need to reinstall, but I would try the above first.

---

### Post by scpike on 2006-06-20
anyone know how to purge them/completely remove?

---

### Post by ajgreeny on 2006-06-20
I suppose one possibility is to:-

1.  Install or reinstall *kubuntu-desktop* using aptitude, (not apt-get or synaptic).  Aptitude remembers all the packages installed when you install a metapackage like *kubuntu-desktop*.

2.  Purge (ie completely uninstall) *kubuntu-desktop* with aptitude.  As you installed using aptitude this will now uninstall all the packages you have just installed

3.  Now reinstall kubuntu-desktop again.  Nothing should need to be downloaded this time as all the deb files will be in cache, so it should be much quicker.

As you did a purge of the kubuntu-desktop you should now have a totally clean start.  I must add that this is not something I have ever done but working from first principles I can't see why it shouldn't work.  If you try it let us all know how you get on.  Good luck!

---

### Post by 5-HT on 2006-06-20
If you want to remove all residual config files two easy options present themselves:

1. Just look for them in Synaptic. There is a listing of residual configs.
2. Search for them in Aptitude and remove them. If you are using Aptitude's text-based-GUI search for ~c.

To do it from the CLI:

```
 aptitude search ~c 
``` 
You can also purge all residual configs from Aptitude's CLI interface by using the same search flag.


[quote=ajgreeny]I suppose one possibility is to:

2.  Purge (ie completely uninstall) *kubuntu-desktop* with aptitude.  As you installed using aptitude this will now uninstall all the packages you have just installed

As you did a purge of the kubuntu-desktop you should now have a totally clean start.  I must add that this is not something I have ever done but working from first principles I can't see why it shouldn't work.  If you try it let us all know how you get on.  Good luck![/quote] 
AFAIK Aptitude's default setting is to remove, not purge, packages selected for automatic removal. 
While purging kubuntu-desktop will purge the metapackage, all dependencies will only be removed.

You can change this default to purge packages selected for automatic removal.

Hope that helps.

---

