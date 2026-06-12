---
title: "Installing all locales in Karmic"
date: 2009-11-19
forum: General Help
---

### Post by lachild on 2009-11-19
Once upon a time there use to be a package in the repositories that allowed you to install all the locale files.  For some reason it looks like the package name has changed or is no longer available.

Unfortunately there isn't much documentation on how to go about installing multiple locales so I thought I'd make a quick note here so I can remember in case I have to do this again.  Plus maybe it'll help someone else that is having the same problem.


First I'd like to start out by saying if your only worried about a couple of different locales simply install them by using:

```
sudo locale-gen [some locale here]
```

For a list of avaliable locales to install:

```
cat /usr/share/i18n/SUPPORTED | less
```


Now if you looking to install quite a few and disk space is no concern then to install all locales use the following:

```
sudo cp /usr/share/i18n/SUPPORTED /var/lib/locales/supported.d/local
sudo locale-gen
```

Hope this helps,
LaChild

---

