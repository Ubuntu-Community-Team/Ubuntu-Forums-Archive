---
title: "undoing a recent application update"
date: 2010-12-14
forum: General Help
---

### Post by pgagy on 2010-12-14
I recently added a repository to my package manager to allow me an installation of firefox 4.0.  This worked, and when I ran a recent update, my package manager also updated my firefox 3.6 to a nightly build, as well as my thunderbird email application.  What's worse is, it changed around all my icons and names, so now it uses the code name of the version (Namaroka, instead of firefox...)  I'm sure this is great for developers, but I just want it to be normal.  Any idea if/how I can step back with the update I did?

Thanks!

---

### Post by 3rdalbum on 2010-12-14
Remove the repository from your package manager and then use the "Force Version" menu item for each of your FireFox and Thunderbird packages in Synaptic Package Manager.

The development versions of FireFox and Thunderbird are always known by the code names, so what happened was pretty much par for the course.

---

### Post by lovinglinux on 2010-12-15
Remove Firefox 4

```
sudo apt-get remove firefox-4.0
```

Go to "Software Center >> Edit >> Software Sources >> Other Software", disable ubuntu-mozilla-daily ppa, update and reinstall Firefox and Thunderbird.

```
sudo apt-get update
sudo apt-get install --reinstall firefox
sudo apt-get install --reinstall thunderbird
```

If you want to install Firefox 4 without updating your default version, see my tutorial at [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

---

### Post by pgagy on 2010-12-18
I used a combination of your suggestions, but the --reinstall option did not work. I had to completely uninstall firefox and thunderbird, and then reinstall.  I did remove the daily repository as well. 

Thanks for your helps!

---

