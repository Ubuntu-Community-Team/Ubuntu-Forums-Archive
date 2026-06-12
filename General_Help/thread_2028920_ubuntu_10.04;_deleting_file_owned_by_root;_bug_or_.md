---
title: "ubuntu 10.04; deleting file owned by root; bug or feature"
date: 2012-07-19
forum: General Help
---

### Post by Wim Sturkenboom on 2012-07-19
As root, I have created a file on my (the user's) Desktop.

```

sudo su -
cd /home/wim/Desktop
touch abc.txt
exit

```

If I try to delete it (as normal user) using a terminal, it will warn me with a message (*remove write-protected regular file*) and allow me to bail out. If I however delete it from the GUI, it does not prompt me and the file is immediately deleted.

Is this a bug or is this a feature? Is there a work around to get this message as well in the GUI?

Thanks in advance.

---

### Post by hal8000 on 2012-07-19
I cant duplicate this as I'm running 11.10 and 12.04, but that doesn't sound right.
Any file on the desktop (Gnome or Unity) if created by root should not be deleteable.
How are you deleting, dragging with mouse, or by highlighting and pressing delete?

---

### Post by Wim Sturkenboom on 2012-07-19
highlight and press <delete>

---

### Post by ajgreeny on 2012-07-19
Just as a test of this I have just made a new file in my home with ```
gksudo gedit /home/<user>/txt.txt
``` on my 10.04 box.

I then checked the file's permissions, and not surprisingly it was owned by root, with read/write permissions, and had read-only permissions for group and others.  However, I could also delete that txt.txt file simply as user, without any problems at all using the delete button.

Very odd!  Anybody have any idea why that is possible.

EDIT:
Just an update.  I can delete the file, but I can not edit it at all as user.

This is getting very weird.  How come it is possible to delete but not edit a root owned file with read only permissions for my user?

---

### Post by 3rdalbum on 2012-07-19
> **ajgreeny said:**
> Just as a test of this I have just made a new file in my home with ```
gksudo gedit /home/<user>/txt.txt
``` on my 10.04 box.

I then checked the file's permissions, and not surprisingly it was owned by root, with read/write permissions, and had read-only permissions for group and others.  However, I could also delete that txt.txt file simply as user, without any problems at all using the delete button.

Very odd!  Anybody have any idea why that is possible.

EDIT:
Just an update.  I can delete the file, but I can not edit it at all as user.

This is getting very weird.  How come it is possible to delete but not edit a root owned file with read only permissions for my user?

Deleting a file doesn't actually modify the file, it modifies the parent directory. As long as you have read/write permission in the parent directory, you can delete any file in that directory no matter who the owner is or whether your user has write access.

As for not prompting, the Delete function in Gnome does not prompt. Never has, probably never will. That's why it's hidden by default in favour of the "Move to Trash" function, which is a little more reversible!

What is more odd is that all the Ubuntu 10.04 users are coming out tonight; this is the third thread I've read tonight where they're using the old LTS! :-)

---

### Post by Wim Sturkenboom on 2012-07-19
> **3rdalbum said:**
> 
As for not prompting, the Delete function in Gnome does not prompt. Never has, probably never will. That's why it's hidden by default in favour of the "Move to Trash" function, which is a little more reversible!

<delete> from the GUI moves it to the trash as well :)

> **3rdalbum said:**
> 
...
**they're using the old LTS!** :-)We (or at least I) don't want bleeding edge and I don't want to upgrade every year or so :) I usually upgrade my LTS in December when most of the issues that are there in the next release are hopefully solved. Till such time, any issue is valid game for me :lol:

---

### Post by Wim Sturkenboom on 2012-07-19
And threads like [http://ubuntuforums.org/showthread.php?t=2028502](http://ubuntuforums.org/showthread.php?t=2028502) (describing issues with nvidia driver / card) make that I actually don't want to upgrade at all to 12.04 ;)

---

### Post by ajgreeny on 2012-07-20
> **Wim Sturkenboom said:**
> And threads like [http://ubuntuforums.org/showthread.php?t=2028502](http://ubuntuforums.org/showthread.php?t=2028502) (describing issues with nvidia driver / card) make that I actually don't want to upgrade at all to 12.04 ;)
I don't have an nvidia card with the problems that gives some users, but an old ATI 9200SE, which with 10.04 is brilliant, running a full compiz desktop, if I want it.  In 12.04 however, that card will not run unity 3D, but reverts to unity2D with all the configuration limitations that gives, therefore even when I use 12.04, which is seldom, I take advantage of the gnome panel/fallback desktop, which works pretty well.

Compiz in 12.04 seems broken and when I try to use the compiz profile from 10.04 in 12.04, it completely messes up the desktop, hence my use not only of the fallback desktop, but also the "no effects" desktop, without compiz, using good old metacity.

However, like you I also am not in need of a bleeding edge system with all the problems that can give.  If I need updated applications I search for a ppa and give it a try, which so far has given me the best of all worlds, ie a tried and trusted, stable system, but with some top end applications, eg Libreoffice 3.5.4-2, thunderbird 14, tesseract 3.02, and several others I can't think of at the moment.

I still think 10.04 is the best ubuntu to date.

---

### Post by Wim Sturkenboom on 2012-09-25
Oops, posted by accident. Will mark as solved as there is no solution here.

---

