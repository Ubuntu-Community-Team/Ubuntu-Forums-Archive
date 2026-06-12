---
title: "change folder icon and apply to all subfolders"
date: 2011-05-11
forum: General Help
---

### Post by ububeginner on 2011-05-11
I have a music folder that contains alot of folders for different artist, each of those folders contain various folders for different albums.
The Music folder itself has got a music folder icon, but all of the subfolders have the regular folder icon, I would like all of the subfolders to have the music folder icon but I don't want to go through each folder to change the icons one at the time.

Is it possible to change the folder icon and apply the change to all the subfolders and sub-subfolders?

I'm on 10.10 btw

---

### Post by ububeginner on 2011-05-11
I think I've found the right path to take here. 
I created a test folder with sub- and subsubfolders to experiment with

This command changes the test folders icon

```
gvfs-set-attribute test metadata::custom-icon file:///home/borkur/.icons/OSDark/128x128/places/folder-music.png 
 
```however, when trying to apply the command to subfolders with a *wildcard

```
borkur@ubuntu:~$ gvfs-set-attribute test/* metadata::custom-icon file:///home/borkur/.icons/OSDark/128x128/places/folder-music.png 
Error setting attribute: Setting attribute test/art2 not supported
 
```So the question is
How do I get the *wildcard to work, and limit it to just folders and not actual music files?

---

