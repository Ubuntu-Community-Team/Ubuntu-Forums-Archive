---
title: "symlink samba or something?"
date: 2009-07-25
forum: General Help
---

### Post by norjms on 2009-07-25
Hello and thanks for reading.
I have a question about how to accomplish a task on my server. I have several drives full of my archived movies. I want them to all appear in one directory.

Example
Drive A
      Folder Starwars 1 - Starwars1.avi
      Folder Starwars 2 - Starwars2.avi
Drive B
      Folder Starwars 3 - Starwars3.avi
      Folder Starwars 4 - Starwars4.avi
Drive C
      Folder Starwars 5 - Starwars5.avi
      Folder Starwars 6 - Starwars6.avi

How would I make a directory and symlink so it looks like this
Drive A
      Folder Master Movies 
             Folder Starwars 1 - Starwars1.avi
             Folder Starwars 2 - Starwars2.avi
             Folder Starwars 3 - Starwars3.avi
             Folder Starwars 4 - Starwars4.avi
             Folder Starwars 5 - Starwars5.avi
             Folder Starwars 6 - Starwars6.avi

I know I could link each directory but, I have 1600 folders and that might take a very long time. I also know I could soft raid them but, I don't want to lose everything is a drive fails. Make sure you speak slow as I'm a novice.

The reason I need to do this is my media center breaks up different drives into different views and I would have to check them all to find a certain movie.

If you can't symlink them or something into one folder view. Can Samba make the contents multiple drives appear ubder one share?

and Not like this
Folder or Share Master Movies 
     Drive A
      Folder Starwars 1 - Starwars1.avi
      Folder Starwars 2 - Starwars2.avi
     Drive B
      Folder Starwars 3 - Starwars3.avi
      Folder Starwars 4 - Starwars4.avi
     Drive C
      Folder Starwars 5 - Starwars5.avi
      Folder Starwars 6 - Starwars6.avi

It can't show that the drives are sepperate or in different folders just one master folder or share with just the contents of the different drives inside.

---

