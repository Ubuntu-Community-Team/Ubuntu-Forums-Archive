---
title: "unable to remove folders from places pane"
date: 2011-12-19
forum: General Help
---

### Post by senchan on 2011-12-19
Hi.
 
I've installed a dual boot win 7 and ubuntu, with a common storage partition and want to set up the document libraries in both systems to point to that storage partition. 
 
I had no problems doing so in windows, but in Ubuntu when I right click one of the folders (i.e. Pictures) in the "places pane" the "Delete" and "Rename" option seem
to be grayed out (I can't click on them). 
 
I presume it has something to do with root access, but from what I've realized (a newbie), root actions can be done only from the terminal (or are recommended
only to be done that way). 
 
What should I do? Is there a way to just redirect where these folders point, like
in the windows 7 libraries? Still, this would be only a partial solution for me, 'cause
I wouldn't use half of these (like Pictures, Music), and would like to add some others as well, so being able to delete these folders would be a must for me :/

---

### Post by seawolf167 on 2011-12-19
You can remove or edit them by opening Nautilus then from the menu select Bookmarks, then Edit Bookmarks, and edit the bookmarks.

---

### Post by grahammechanical on 2011-12-19
As a helpful hint it is possible to load both the file manager (Nautilus) and the standard editor (Gedit) with root or administrator privileges so that you can use a GUI to do things.


```
gksudo gedit
```

will open Gedit with root privileges.

```
gksudo gedit /path/filename
```

will open the file so named in Gedit with root privileges.

```
gksudo nautilus
```

will open the file manager with root privileges.

Regards.

---

### Post by senchan on 2011-12-19
I tried to open nautilus with gksudo and succeeded, but when I select "edit bookmarks" there is only the "Home" bookmark (none of the others which are present in the pane when I open my home folder regularly)..also, the "places" in the side pane are different in nautilus than in the "regular gui"

---

### Post by seawolf167 on 2011-12-19
> **senchan said:**
> I tried to open nautilus with gksudo and succeeded, but when I select "edit bookmarks" there is only the "Home" bookmark

This is because you are opening and editing *root's* bookmarks. Don't use *gksudo* then attempt to edit the bookmarks.

---

### Post by senchan on 2011-12-19
Thanks for the quick response seawolf.

I must be doing something wrong - I enter "nautilus" in the terminal and when it openes up, there is no menu from which I can choose "bookmarks"..it looks just like a regular gui which comes up when I click on the home icon in the app bar

---

### Post by seawolf167 on 2011-12-19
Try hitting the default shortcut keystroke to edit the bookmarks menu and see if it pops up

[CTRL][B]

Also - you can run GUI applications by hitting [ALT][F2] then typing in the application name rather than using the terminal.

From the file manager (Nautilus): Use the Places menu at the top and select "Edit Bookmarks" from the bottom.

---

### Post by mcduck on 2011-12-19
> **senchan said:**
> Hi.
 
I've installed a dual boot win 7 and ubuntu, with a common storage partition and want to set up the document libraries in both systems to point to that storage partition. 
 
I had no problems doing so in windows, but in Ubuntu when I right click one of the folders (i.e. Pictures) in the "places pane" the "Delete" and "Rename" option seem
to be grayed out (I can't click on them). 
 
I presume it has something to do with root access, but from what I've realized (a newbie), root actions can be done only from the terminal (or are recommended
only to be done that way). 
 
What should I do? Is there a way to just redirect where these folders point, like
in the windows 7 libraries? Still, this would be only a partial solution for me, 'cause
I wouldn't use half of these (like Pictures, Music), and would like to add some others as well, so being able to delete these folders would be a must for me :/
It's not a question of permissions or anything like that. Some entries of that panel show and hide automatically (devices, network locatons etc.), some of them are hard-coded into Nautilus (showing Desktop, user home, filesystem, Pictures, Videos etc. directories if they exist) and only some are actually editable (bookmarks).

In other words, you can only remove the bookmarks you have actually added to the side panel. The rest is built into the file manager. (if you really want to get rid of the "Pictures" entry, for example ,you'd have to remove the Pictures directory itself).

Anyway, if you just want your content to go to some other partition you just need to take a different approach. Depending on what filesystem you are using on that partition you can either create a simple symbolic link from a directory on that partition to your home. Or you can use the "bind" option in fstab to mount a certain directory into another place.

---

### Post by senchan on 2011-12-19
> **mcduck said:**
> It's not a question of permissions or anything like that. Some entries of that panel show and hide automatically (devices, network locatons etc.), some of them are hard-coded into Nautilus (showing Desktop, user home, filesystem, Pictures, Videos etc. directories if they exist) and only some are actually editable (bookmarks).

In other words, you can only remove the bookmarks you have actually added to the side panel. The rest is built into the file manager. (if you really want to get rid of the "Pictures" entry, for example ,you'd have to remove the Pictures directory itself).

Anyway, if you just want your content to go to some other partition you just need to take a different approach. Depending on what filesystem you are using on that partition you can either create a simple symbolic link from a directory on that partition to your home. Or you can use the "bind" option in fstab to mount a certain directory into another place.

Thanks.

When I remove the Pictures (i.e.) directory, the entry still remains in the pane and actually points to nothing (path not found error), so this does not solve the "problem" :)

But I can live with those entries being there and not being used :)

---

### Post by senchan on 2011-12-19
> **mcduck said:**
> It's not a question of permissions or anything like that. Some entries of that panel show and hide automatically (devices, network locatons etc.), some of them are hard-coded into Nautilus (showing Desktop, user home, filesystem, Pictures, Videos etc. directories if they exist) and only some are actually editable (bookmarks).

In other words, you can only remove the bookmarks you have actually added to the side panel. The rest is built into the file manager. (if you really want to get rid of the "Pictures" entry, for example ,you'd have to remove the Pictures directory itself).

Anyway, if you just want your content to go to some other partition you just need to take a different approach. Depending on what filesystem you are using on that partition you can either create a simple symbolic link from a directory on that partition to your home. Or you can use the "bind" option in fstab to mount a certain directory into another place.

Thanks.

When I remove the Pictures (i.e.) directory, the entry still remains in the pane and actually points to nothing (path not found error), so this does not solve the "problem" :)

But I can live with those entries being there and not being used :)

@seawolf - I managed to bring up the bookmarks window, but removing them wouldn't remove them from the pane..so yea, I guess it can't be done. But at least I've found this way easier for the "redirection" part, so thanks for your help!

---

### Post by Mat11 on 2011-12-19
> **mcduck said:**
> It's not a question of permissions or anything like that. Some entries of that panel show and hide automatically (devices, network locatons etc.), some of them are hard-coded into Nautilus (showing Desktop, user home, filesystem, Pictures, Videos etc. directories if they exist) and only some are actually editable (bookmarks).
 
In other words, you can only remove the bookmarks you have actually added to the side panel. The rest is built into the file manager. (if you really want to get rid of the "Pictures" entry, for example ,you'd have to remove the Pictures directory itself).
 
Anyway, if you just want your content to go to some other partition you just need to take a different approach. Depending on what filesystem you are using on that partition you can either create a simple symbolic link from a directory on that partition to your home. Or you can use the "bind" option in fstab to mount a certain directory into another place.
 
Hi i'm not a newbie but the same thing happened to me a folder ended up in places which never should have been there in the first place and was never authorised by myself for a move. I'm wondering if it is a security issue as well.
Think i went too far and deleted nautilus and then reinstalled it to find my log-in square blanked out for some reason-- i'm writing from a windows backward machine.
I'm wondering if many other people are having this problem? -- i'm using Maverick 10.10 on a 86-64 laptop.
 
Someone recommended to me resetting using commands concerning 'config' in the terminal but you may have to ask someone else for the exact commands good luck.

---

### Post by senchan on 2011-12-19
Just to report in: 

I've made symbolic links instead of the folders, so now the places pane points to these symbolic links which point to my storage partition, I'm not frustrated by the fact that some of the places will never be clicked, but it sure would be cool to be able to ultimately customize this :)

Thanks mcduck for the symlink suggestion

---

### Post by mcduck on 2011-12-19
> **Mat11 said:**
> Hi i'm not a newbie but the same thing happened to me a folder ended up in places which never should have been there in the first place and was never authorised by myself for a move. I'm wondering if it is a security issue as well.
Think i went too far and deleted nautilus and then reinstalled it to find my log-in square blanked out for some reason-- i'm writing from a windows backward machine.
I'm wondering if many other people are having this problem? -- i'm using Maverick 10.10 on a 86-64 laptop.
 
Someone recommended to me resetting using commands concerning 'config' in the terminal but you may have to ask someone else for the exact commands good luck.
Sounds like you just accidentally bookmarked something (as it's pretty much the only way you possibly *can* add anything to the Nautilus sidepanel). Uninstalling Nautilus wouldn't have helped anything, as unistalling applciations doesn't touch any of the user's own configuration files. On the othe rhand Nautilus is pretty important component of the Gnome desktop, responsible of much more than just the file amanger window. Uninstalling it most likely removed quite many other packages as well. Try reinstaling the "ubuntu-desktop" package, that should make sure everything important is installed.

---

### Post by bodhi.zazen on 2011-12-19
You can edit them with ubuntu-tweak

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

[img]http://i.stack.imgur.com/LFaWM.jpg[/img]

See [http://askubuntu.com/questions/87232/removed-folder-re-appears-again](http://askubuntu.com/questions/87232/removed-folder-re-appears-again) for details.

---

### Post by senchan on 2011-12-19
Thank you.

---

### Post by bodhi.zazen on 2011-12-19
you are most welcome =)

---

