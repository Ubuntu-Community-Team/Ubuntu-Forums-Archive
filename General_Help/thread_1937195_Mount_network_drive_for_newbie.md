---
title: "Mount network drive for newbie"
date: 2012-03-07
forum: General Help
---

### Post by poumtatalia on 2012-03-07
Hi there, 
I recently left the ms world so apologies in advance if my question is very basic.

I need to mount a network drive.

In window I basically added it as a drive, or eneterd the IP adress in the file explorer bar and that worked.

In Ubuntu, is there a GUI tool to do this?
If not, anybody has a command line to do so  or a tutorial? 

Thanks in advance for your help

---

### Post by Morbius1 on 2012-03-07
> In window I basically added it as a drive ... Same here. When you open Nautilus and go to "Browse Network" and finally select the shared folder it mounts it automatically. You can add a bookmark if you wish at that point: Bookmarks > Add Bookmark.

> ... or eneterd the IP adress in the file explorer bar and that worked.Same here but you need to prefix the ip address by smb://. So the line would be:
```
smb://192.168.0.100/shared-folder
```Or if you want to start it from a terminal:
```
nautilus smb://192.168.0.100/shared-folder
```In either case your shared folder is mounted to:
> /home/user-name/.gvfs/shared-folder on 192.168.0.100If you are using the 12.04 beta the mount point has moved to:
> /home/user-name/.cache/gvfs/shared-folder on 192.168.0.100If you want to mount this folder automatically every time you boot I would suggest Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by poumtatalia on 2012-03-07
Hi Morbius1, 

Thanks a lot for your complete and clear reply. I did manage to mount the drive, the only bit I couldn't manage is to make it persistent.
It just won't create the bookmark. I tried as SSH, Windows Share, no luck.

Any hint welcome ;-)

---

### Post by Morbius1 on 2012-03-07
You couldn't create the bookmark? There is nothing in /home/username/.gtk-bookmarks ?

[COLOR=Blue]**EDIT**[/COLOR]: Or are you talking about Gigolo?

---

