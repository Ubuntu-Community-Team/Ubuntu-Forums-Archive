---
title: "Music Filenames"
date: 2010-11-03
forum: General Help
---

### Post by personjerry on 2010-11-03
hey guys I have many music files named in this format: Artist - Song Name.mp3
Is there some way to get rid of the "Artist - " part? Probably through the usage of sed I'm guessing.
I've never used sed though (and heard it takes a while to learn) so if anyone could provide such a command to execute in my music folder it would be greatly appreciated. In the meantime I guess I'll try to read up on it a little.

Thanks!

---

### Post by Enigmapond on 2010-11-03
I don't know of a command but you can install easytag and change them one by one...also I know the Guayadeque player and possibly Banshee can also do this but easytag is...well easy:) Hope this helps

---

### Post by Jose Catre-Vandis on 2010-11-03
Here you go a little script that might do what you want:

Assumes you have a "- " before the song name, as script will strip everything to the left (including the "- ")

Copy the script to a file, and ensure it is executable
```
#!/bin/bash


for FILE in *mp3 ; do
   NEWNAME="${FILE##*- }"  # Strips everything to the left of the first '- '

   echo mv "$FILE" "$NEWNAME"    # 'echo' is our safety feature
done
```
You might want to try this in a test directory with a few files first

Run a terminal and cd to the directory with files you want to rename
Copy the script into this directory

Now run the script

You should see output showing the old filename and then the new filename. This should show you it works.

Now edit the script and remove the "echo", save and run the script again. Your files should now be renamed correctly. (You can also replace mv with cp if you want to keep the original files/filenames as well)

---

### Post by personjerry on 2010-11-03
Hey thanks for the fast responses, I tried EasyTAG first and it actually had a Scan function which did exactly what I wanted and also put the Artist into the mp3 artist section! Thanks guys.

---

