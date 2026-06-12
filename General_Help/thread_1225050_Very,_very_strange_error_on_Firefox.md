---
title: "Very, very strange error on Firefox"
date: 2009-07-28
forum: General Help
---

### Post by argos3016 on 2009-07-28
The problems are:
-The bookmarks doesn't exist!!
-The direction bar don't fresh; when I go to google it continue on blank
-And most strange, when I click home page (Google) , the Firefox goes to Mozilla.org
Posible reasons are:
-Yesterday I was silly and start Firefox as root
Sorry for my english, but you know about that?!:confused:

---

### Post by nikhilk on 2009-07-28
> **argos3016 said:**
> The problems are:
-The bookmarks doesn't exist!!
-The direction bar don't fresh; when I go to google it continue on blank
-And most strange, when I click home page (Google) , the Firefox goes to Mozilla.org
Posible reasons are:
-Yesterday I was silly and start Firefox as root
Sorry for my english, but you know about that?!:confused:

First off, check the permissions on your firefox profile directory.
```
ls -l ~/.mozilla
```

Probably also check permissions of .mozilla directory itself.
```
ls -la ~/ | grep mozilla
```

---

### Post by Nisstyre56 on 2009-07-28
Try creating a new firefox profile

Not entirely sure on the process of this, I think it depends on what version of Ubuntu and FF you're using.

---

### Post by argos3016 on 2009-07-28
Terminal prints this:
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 extensions
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 firefox
macrum@macrum:~$ 
macrum@macrum:~$ 
macrum@macrum:~$ clear
macrum@macrum:~$ ls -l ~/.mozilla
total 8
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 extensions
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 firefox
macrum@macrum:~$ ls -la ~/ | grep mozilla
drwx------  4 macrum macrum     4096 2009-06-13 21:46 .mozilla
macrum@macrum:~$ 
And I don't know what is a Firefox profile. My version of is Firefox 3.0.12 running on Jackalope.
Please help meee!

---

### Post by Nisstyre56 on 2009-07-28
Completely close down Firefox

run this
```
firefox -ProfileManager
```

Delete the current profile (WARNING: this will get rid of all of your settings and bookmarks in Firefox)

Now create a new one. Restart, see if the problem persists.

---

### Post by argos3016 on 2009-07-28
The problems gone!!! In future I will create security copies of bookmarks, (I had about 302):( But thanks!!:D

---

### Post by nikhilk on 2009-07-28
> **argos3016 said:**
> Terminal prints this:
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 extensions
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 firefox
macrum@macrum:~$ 
macrum@macrum:~$ 
macrum@macrum:~$ clear
macrum@macrum:~$ ls -l ~/.mozilla
total 8
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 extensions
drwx------ 3 macrum macrum 4096 2009-06-13 21:46 firefox
macrum@macrum:~$ ls -la ~/ | grep mozilla
drwx------  4 macrum macrum     4096 2009-06-13 21:46 .mozilla
macrum@macrum:~$ 
And I don't know what is a Firefox profile. My version of is Firefox 3.0.12 running on Jackalope.
Please help meee!

The permissions look OK.

First quit from Firefox, use File->Quit. Then you can create a new profile as follows
```
mv ~/.mozilla/firefox ~/.mozilla/firefox_bak
```

Now launch Firefox and see if it works correctly.

---

