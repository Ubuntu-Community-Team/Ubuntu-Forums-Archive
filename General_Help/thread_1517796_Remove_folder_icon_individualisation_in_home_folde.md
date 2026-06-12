---
title: "Remove folder icon individualisation in home folder"
date: 2010-06-25
forum: General Help
---

### Post by Japese on 2010-06-25
I have a personal way of sorting my files such as having an "Audio" folder which contains the folders "Music" and "Samples" instead of the "Music" folder in the home folder. I then gave all the folders emblems such as a documents emblem to the "Documents" folder and changed the locations in the file "user-dirs.dirs" in the ".config" folder such as:

XDG_MUSIC_DIR="$HOME/Music"
to
XDG_MUSIC_DIR="$HOME/Audio/Music"

I've also added a few extra folders in the home folder not in that file such as a "Projects" folder.

Now, because each of the folders shown in the "user-dirs.dirs" file have been given a different icon showing a picture relating to the contents of that folder in the home folder, some have these icons, some don't (The extra folders I added now having the simple folder icons) and those that do have the icons also have the emblems I added to them. It all looks a bit stupid.

It just feels like they're trying to standardise a home folder structure that I really don't like as there are files I have I just can't sort into any of those folders.

I've noticed that changing the icons by going into the properties of the folder won't work because when changing the theme, those icons won't change with it. So is there any other way of reverting all of the folders that have been given these icons back to simple folder icons in the home folder as they were before?

---

