---
title: "How to rebuild apt index?"
date: 2010-01-01
forum: General Help
---

### Post by cyprys on 2010-01-01
I recently did a very stupid thing:
```
sudo rm -f /var/log
```
Now I cannot update or upgrade any package (I know there are updates waiting but Update Manager doesn't show any packages to download). How can I rebuild the index of packages and its versions in **/var/log/apt** ?

Someone suggested to reinstall all installed packages - is there any other solution?

---

### Post by dhillonv10 on 2010-01-01
Well, one thing we learned is never to do rm without knowing what it does, now try this and see if it helps: 

```
 
sudo apt-get -f install
 
```

And then do 

```
 
sudo apt-get update
sudo apt-get upgrade
 
```

---

### Post by cyprys on 2010-01-02
It didn't work. The output just said "building dependency tree" and then everything is "done" and "ok" and 0 packages to install, remove or update. Pretty much the standard apt output when done nothing. And upgrade doesn't download any new packages.

What happens currently on my desktop is:
```
for pkg in `dpkg --get-selections | awk '$2=="install"{print $1}'`;
do sudo apt-get install -y --reinstall $pkg;
done
```
I hope it helps because it takes long (and by that I mean: LONG!) time to reinstall everything.

Cheers!

edited:
It just occurred to me I could simply use awk script instead of employing bash "for ... in ... do" statement. It would look something like this:
```
dpkg --get-selections | awk '$2=="install" {
    system ("sudo apt-get install -y --reinstall " $1)
}'
```

edited:
It took long but re-installation helped and I can confirm (after today's upgrade) packages upgraded properly with Update Manager.

---

