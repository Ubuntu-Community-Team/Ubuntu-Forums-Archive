---
title: "Get 404 not found from repository"
date: 2011-06-27
forum: General Help
---

### Post by fatteralbert on 2011-06-27
I'm trying to install an old version of spotify since the new one keeps crashing, but I get 404 not found from the repository. This is my repository definition: 

```
deb http://dl.dropbox.com/u/1691381/spotify-client-gnome-support_1 253a0.4.9.302.g604b4fb-1 all.deb 
deb http://dl.dropbox.com/u/1691381/spotify-client-qt_1 253a0.4.9.302.g604b4fb-1 i386.deb
```Is there something wrong with my definition (I'm knew to linux)? 

Or is the repository removed?

---

### Post by dcstar on 2011-06-28
> **fatteralbert said:**
> I'm trying to install an old version of spotify since the new one keeps crashing, but I get 404 not found from the repository. This is my repository definition: 

```
deb http://dl.dropbox.com/u/1691381/spotify-client-gnome-support_1 253a0.4.9.302.g604b4fb-1 all.deb 
deb http://dl.dropbox.com/u/1691381/spotify-client-qt_1 253a0.4.9.302.g604b4fb-1 i386.deb
```Is there something wrong with my definition (I'm knew to linux)? 

Or is the repository removed?

A file URL is **not** a repository.

---

### Post by varunendra on 2011-06-29
> **dcstar said:**
> A file URL is **not** a repository.
^ and the files (that the URLs point to) seem to have been removed (or maybe replaced by new ones) from the repository to which they earlier belonged. This is normal for old versions of a software.

---

