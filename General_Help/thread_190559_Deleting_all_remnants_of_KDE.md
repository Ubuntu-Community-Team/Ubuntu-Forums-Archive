---
title: "Deleting all remnants of KDE"
date: 2006-06-06
forum: General Help
---

### Post by greenbmw530i on 2006-06-06
Hello all!
With Breezy I had KDE to start with, but then got rid of it in favor of GNOME. However I still see things from KDE (programs with "K" in the beginning of the name :-k ). So, I recently upgraded to Dapper and I still see the random KDE things...is there something I can do to get rid of everything that KDE put on my computer (without harming GNOME)?

Thanks in advance!
Mike

---

### Post by adwait on 2006-06-06
KDE programs can still be used with gnome, eg amarok and hence aren't removed when KDE itself is remvoed. So if you donw want these programs at all...I guess you'll have to manualy remove them.

---

### Post by cleentrax on 2006-06-06
Next time, when you install a complex package like kde, use aptitude instead of apt-get. It will make it much easier to uninstall.

---

### Post by no1wantdthisname on 2006-06-06
Here's a fairly easy way:
First install debfoster.  This program keeps track of dependencies of packages and makes it easy to find unneeded library files/leftover stuff from metapackages like kubuntu-desktop.
```
sudo apt-get install debfoster
```
Then reinstall kde.  I'm not sure what you removed so it'll be easier if you just reinstall.
```
sudo apt-get install kubuntu-desktop
```
Now create a default list.
```
sudo debfoster -q
```
Edit the list:
```
sudo gedit /var/lib/debfoster/keepers
```
Remove the line that says kubuntu-desktop.


Finally just do
```
sudo debfoster
```
and when it asks whether you want to remove kubuntu-desktop just push "p" for "Prune" which removes the package and all its dependencies.  Debfoster only removes dependencies that are not needed by other packages, so this won't break anything.

---

### Post by .t. on 2006-06-06
LOL, you beat me to it. That method is one I use not quite every day, more like every week.

---

### Post by mlind on 2006-06-06
My two favourite toys are
[LIST]
[*]deborphan
[*]aptitude
[/LIST]

Both very nice for tracking 'unwanted' dependencies.

hmm, that debfoster looks nice too. Maybe I'll include it on my toybox.

---

