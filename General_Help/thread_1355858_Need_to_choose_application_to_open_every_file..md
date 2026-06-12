---
title: "Need to choose application to open every file."
date: 2009-12-15
forum: General Help
---

### Post by gregbzh on 2009-12-15
Hi.  I'm having problems opening files in Karmic.  I'm asked to choose an application to open every single file, whether it be an image, mp3, pdf etc (see image).  My right click menu is now also missing 'extract here' so I can't extract tar or zip files.  I've never seen this before.  Does anyone know how I can fix it?
[IMG][IMG]http://img265.imageshack.us/img265/8339/probsc.png[/IMG] By [les_friwis](http://profile.imageshack.us/user/les_friwis) at 2009-12-15[/IMG]

Cheers.

---

### Post by Physical Hook on 2009-12-15
Had the same issue and since I didn't found a solution ( including *no thumbnails* problem ), I installed Thunar. Way better than pcmanfm :)

---

### Post by doas777 on 2009-12-15
what do you get from:
```

ls -l ~/.local/share/applications/mimeapps.list

```

this file should store most of your "file type associations". does it exist, with read/write permissions?

---

### Post by gregbzh on 2009-12-15
> **doas777 said:**
> what do you get from:
```

ls -l ~/.local/share/applications/mimeapps.list

```

this file should store most of your "file type associations". does it exist, with read/write permissions?


This is what I get.  

-rw-r--r-- 1 greg greg 150 2009-12-15 08:18 /home/greg/.local/share/applications/mimeapps.list

Make sense?

---

### Post by doas777 on 2009-12-15
> **gregbzh said:**
> This is what I get.  

-rw-r--r-- 1 greg greg 150 2009-12-15 08:18 /home/greg/.local/share/applications/mimeapps.list

Make sense?

try renaming it to mimeapps.list.old, and rebooting. just a hunch, so no gaurenties.

---

### Post by Physical Hook on 2009-12-15
> **gregbzh said:**
> This is what I get.  

-rw-r--r-- 1 greg greg 150 2009-12-15 08:18 /home/greg/.local/share/applications/mimeapps.list

Make sense?

Would make a little bit more sense if you would show the contents of this file.

---

### Post by gregbzh on 2009-12-15
Oops, sorry.


[Added Associations]
x-content/audio-cdda=rhythmbox.desktop;vlc.desktop;brasero-copy-medium.desktop;exaile.desktop;
application/x-deb=gdebi.desktop;

---

### Post by gregbzh on 2009-12-15
I think I'll just do a fresh install.  I have 9.10 running elsewhere with no worries so I'm not sure how I've managed to stuff this up.  Thanks for your help though.  :D

---

### Post by Wardje on 2009-12-15
Why not just use nautilus?
And if you're eager on using pcmanfm, wouldnt the location where it makes its file associations be mentioned in their documentation?
For example, if it's only mimeapps.list in your local folder, you could copy contents from the file in /etc/gnome/, ...

---

### Post by doas777 on 2009-12-15
> **Physical Hook said:**
> Would make a little bit more sense if you would show the contents of this file.


well the file size was too small to hold much, but the reason I recommended renaming it, is because that file is no longer present on my karmic system here. It has been in prior versions of ubuntu (see my battles with it here: [http://ubuntuforums.org/showthread.php?t=1151325](http://ubuntuforums.org/showthread.php?t=1151325)). if it is supposed to be there, it shoudl be regened at next login, and if not, then it may be overriding the expected behavior. xorg.conf is like that now adays. you don't need it, but if you have it, it is used.

```

user@box-karmic:~$ ls -l ./.local/share/applications
total 4
-rw-r--r-- 1 user user 437 2009-09-18 10:55 gnomecc.desktop
user@box-karmic:~$ 

```

---

### Post by Physical Hook on 2009-12-15
> **doas777 said:**
> well the file size was too small to hold much, but the reason I recommended renaming it, is because that file is no longer present on my karmic system here. It has been in prior versions of ubuntu (see my battles with it here: [http://ubuntuforums.org/showthread.php?t=1151325](http://ubuntuforums.org/showthread.php?t=1151325)). if it is supposed to be there, it shoudl be regened at next login, and if not, then it may be overriding the expected behavior. xorg.conf is like that now adays. you don't need it, but if you have it, it is used.

```

user@box-karmic:~$ ls -l ./.local/share/applications
total 4
-rw-r--r-- 1 user user 437 2009-09-18 10:55 gnomecc.desktop
user@box-karmic:~$ 

```

From what I've read, the Karmic repository version is broken ( no thumbnails + it doesn't remember file associations ). Most of the people I found complaining about issues with pcmanfm fixed it by installing the latest version, so before you reinstall Ubuntu, this might be worth a try.

---

