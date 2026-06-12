---
title: "Creating back-up for installed programs in ubuntu."
date: 2012-09-21
forum: General Help
---

### Post by arroy_0209 on 2012-09-21
It is generally said that one need not create backup of installed programs since it is easy to reinstall these after restoring os. However, for safety I want to create backup for all the programs I installed in ubuntu 10.04LTS. These include programs like xfig, latex, gcc, gimp etc and all these were done using command "sudo apt-get install <program_name>". Now is it possible to create back-up for these? If possible, which files do I need to take back-up for?

---

### Post by drmrgd on 2012-09-21
That's going to be a bit tricky as the program may have components in a few locations (the executable binary in /usr/bin, necessary libraries in /lib, custom settings in your home directory, etc.).  If you do something like:

```
sudo dpkg -L <package name>
``` 

you can see where all of the components for a package are stored.  Quite a list for some packages!

So, if you're recovering your OS, you'd be better off reinstalling rather than trying to just copy programs over.  You can get lists of what packages you have installed on your system with something like:

```
sudo dpkg --get-selections
```

or 

```
sudo dpkg -l #note: that's a lower case L, not the number 1
```

You can then store that package list in a text file, which can later be used to re-install the packages that were on your system at the time you recovered your OS.  For example:

[http://savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/](http://savvyadmin.com/backup-and-restore-package-lists-in-ubuntu/)

As I was trying to find you an example, I also came across this, which I don't know too much about.  It certainly looks intriguing though!

[http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/](http://www.howtogeek.com/110034/how-to-back-up-restore-your-installed-ubuntu-packages-with-aptoncd/)

---

