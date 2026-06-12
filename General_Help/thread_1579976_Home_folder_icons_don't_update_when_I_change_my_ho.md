---
title: "Home folder icons don't update when I change my home directory"
date: 2010-09-22
forum: General Help
---

### Post by knexfreak111 on 2010-09-22
Hey everyone,

I have a minor problem, but its really annoying to my OCD side.

I have a dual-boot macbook with an OS X partition and an ubuntu partition. When I first installed ubuntu, I changed my home folder to my OS X home directory to synchronize all my files from both. My home directory is now /media/sda2/Users/username/. In a regular home folder, the icons for Documents, Music, Pictures, Movies, etc. are different (not just with emblems, but actually different icons). But when I changed my home folder, these subfolders' icons stayed the same as regular folder icons and I can't figure out a way to change that default setting.


I know how to change the icons for each folder manually, but these changes don't appear everywhere (i.e. nautilus, places, etc). Furthermore, every time I change my icon theme, I would have to manually reassign icons for these folders. Is there a way to globally change the folder icons for these folders??

---

### Post by N00b-un-2 on 2011-03-31
I've been wondering the same exact thing for quite some time now.  At one point I got as far as figuring out how to reassign which folder gets which icon but only on the default icon set (Humanity).  I use Hydroxygen and want to have separate icons for each folder type (Music, Videos, Pictures, Docs, etc...) which hydroxygen AND Humanity both have the icons for, but for the life of me I can't figure out what determines this.  I've dug into the icon sets themselves and there is no way to configure it from there.  My guess is that it has something to do with some of the hidden configuration files in your home, hence the reason why changes that you make to your home folder icons are not visible when you do something like sudo nautilus.

---

### Post by N00b-un-2 on 2011-03-31
W007! I've been looking for a solution to this problem for a REALLY long time and I finally found it.  SO here's the deal.  The issue has to do with XDG.  XDG looks for some very specifically named icons which are located in the /whatever size/places folder in your respective icon theme.  If your icon theme has .svg icons you're in luck because the process is much faster.  Otherwise you're going to be making a crap ton of symbolic links.
I have only managed to change the 'Documents' folder icon, but the theory is sound.  Just make a symbolic link to the icon you want to use but name the icon the proper name, in the case of documents, the proper name is 'folder-documents.png'.  I'm using Hydroxygen which uses png files so I will have to make sym links for each size icon; 128, 72, 48, 32,24, etc....

eg;
```
sudo ln -s /usr/share/icons/hydroxygen/128x128/places/skyblue-folder-documents.png /usr/share/icons/hydroxygen/128x128/places/folder-documents.png
```

repeat the process for each of the sizes, and each of the XDG folders (Documents, Downloads, Pictures, Music, Videos, etc...)

---

