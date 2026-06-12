---
title: "Where's my Favorites Folder?"
date: 2011-03-19
forum: General Help
---

### Post by imaginashawn on 2011-03-19
I've been looking for a simple way to save my Firefox favourites/bookmarks so that next time my computer crashes, I don't have to start all over again collecting favourites. 
I'm willing to give Ubuntu One a try so I signed up and linked my computer to it but I can't find the favourites folder to upload. ](*,)
Does anybody know where it is on 10.10?
Thanks, Shawn

---

### Post by blueridgedog on 2011-03-19
From an earlier post by cariboo907:

Firefox bookmarks are located in ~/.mozilla/firefox/xxxxx.default where xxxxx is a random string of letters and numbers. The easiest way to find the directory is to open Nautilus (Place-->Home Folder) and press Alt-h this will reveal the hidden files and directories.

---

### Post by COMPUTIAC on 2011-03-19
Hello, you state using _ Alt-h_ to reveal hidden files.

  Is this the same as using  _Ctrl-h_  in 10.10 which I use ?

---

### Post by blueridgedog on 2011-03-19
Correct!  I just checked and it is ctrl.

---

### Post by Thund3rstruck on 2011-03-19
> **imaginashawn said:**
> I've been looking for a simple way to save my Firefox favourites/bookmarks so that next time my computer crashes, I don't have to start all over again collecting favourites. 
I'm willing to give Ubuntu One a try so I signed up and linked my computer to it but I can't find the favourites folder to upload. ](*,)
Does anybody know where it is on 10.10?
Thanks, Shawn

Favorites are not saved in the form of *.url files as they are on Win32. Firefox used sqlite (v3) to store everything. Favorites are in ~/.mozilla/firefox/<uid>.default/places.db3

```

select [url] from moz_places WHERE url LIKE 'http%'

```

^^
EDIT: corrected sqlite syntax

---

