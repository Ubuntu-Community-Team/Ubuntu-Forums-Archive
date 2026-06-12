---
title: "Hide common files in different directories"
date: 2009-09-25
forum: General Help
---

### Post by AeroCross on 2009-09-25
Since I'm making the transition from Windows to Linux, while browsing my other NTFS hard drive I can see the desktop.ini and Thumbs.db files everywhere in Ubuntu, but I still use Windows and access the same files through it, so deleting them isn't the solution.

Is there a way to at least naming a file so it's hidden system wide, or a .hidden file that list ALL the files that I want to hide with absolute paths? Or something very massive?

I've been looking around all day and found nothing.

(Making a .hidden file in every folder is not an option)

---

### Post by Liolikas on 2009-09-25
Maybe do feature request bug for your file manager? 
Just hide not only .<file> but <file>.db and <file>.ini on it.
Without some codding I think impossible, but if you add bug everything possible.

---

### Post by AeroCross on 2009-09-25
I don't think you got it right:

I have for example C:\Files\My Music
In My Music\1, My Music\2, My Music\3, My Music\4, and My Music\5 I have a Thumbs.db and a desktop.ini file.

How can I hide them without having to create a .hidden file in EACH directory?
Like, recursively or something?

I'm on Ubuntu 9.04 - GNOME - you know the drill.

I thought I could just create a single .hidden file in the root filesystem accessed by anyone and listing the absolute path of each file I wanted to hide - no success.

---

### Post by CatKiller on 2009-09-25
> **AeroCross said:**
> (Making a .hidden file in every folder is not an option)

You wouldn't have to do it by hand; since it's the same files you want to hide in each directory, you could just make the one and use a *find* command to copy it to each directory that has the files you want to hide in.

---

### Post by AeroCross on 2009-09-25
It is still not quite an option - I'd still be creating a file in each directory, and when I go back to windows, I'd have to flag them all as hidden again - also, if I wanna hide one file named differently in diferent folders, I'd still have to create more hidden files - which is pointless.

Creating a file to hide another file then hiding it in the other OS per directory is inefficient.

Clever, but innefficient - if there are more files, it's OK, but... 1-2?

---

### Post by NoaHall on 2009-09-25
As far as I can remember, you can delete both desktop.ini and thumbs.db

---

### Post by sleepitoff on 2009-09-25
yes, just delete them... it's not a problem... Search directory, select all, delete...

---

### Post by AeroCross on 2009-09-25
The thing is that I still use Windows - so I'd be missing my preferences. I wouldn't be missing much but still.

If I wasn't using Windows it'd be a walk in the park xD
But I am, so they'll be recreating!

---

### Post by sleepitoff on 2009-09-25
This should be a feature in Nautilus, and therefor Dolphin as well for KDE users... An option to add certain file types to be hidden by default and I'm actually surprised there isn't an option for that right now. 

So looks like you're going to have to wait until this feature is implemented, delete all those files and deal with the lost preferences this may cause, or create the .hidden file in every directory containing Thumbs.db and desktop.ini

---

