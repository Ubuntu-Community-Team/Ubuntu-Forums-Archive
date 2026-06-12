---
title: "Help with a simple script"
date: 2011-10-07
forum: General Help
---

### Post by Nostigex on 2011-10-07
I'm not too familiar with console commands or scripting, but I need a script or program of some sort in order to make playlists in my large music collection.

I would like each playlist to be named after the parent folder (which is the name of the album, as I have it arranged). 

I found this script by a google search:

[FONT=courier new]**find** **-name** **'*.mp3'** **>playlistName.m3u**[/FONT]

I tried this for a few albums and it seemed to work fine; it ordered the music correctly. So it just seems I would need to change "playlistName.m3u" to a variable which stores the parent folder name, am I correct? What would this look like?

---

### Post by TeoBigusGeekus on 2011-10-07
```
#!/bin/bash
find -maxdepth 1 -type d ! -name . | while read folder;
do
    folder_name=$(basename "$folder")
    cd "$folder_name"
    ls *.mp3>"$folder".m3u
    cd - 
done
find -name "*.m3u" -exec mv "{}" ./ \;
```
Name it as script, put it in your music folder, make it executable
```
chmod +x script
```
and run it with
```
. ./script
```
(you have to source it for the cd commands to work)

---

### Post by papibe on 2011-10-07
Or this:
```
find ./MusicDir/ -type d -exec bash -c 'ls -1 *.mp3 > "${1##*/}.m3u" 2> /dev/null' _ '{}' \;
```
Regards.

---

### Post by Nostigex on 2011-10-08
Teo,

Maybe I should give more detail as to the structure and location of the  music. I have it on /media/Storage/Player Music/ with this structure:  /Player Music/(Artist Name)/(Album Name)

I assume your script is meant to take care of the entire music folder in one easy step, which is great! But when I use your script from Player Music, it makes playlists with the name of each artist, instead of each album, and places them all in Player Music, instead of within the individual album folders. If I copy the script to an artist folder and run it there, it creates playlists with the name of that artist's albums, but places them in the artist folder instead of within the corresponding album folders. I could manually repeat these steps for each artist, but before I do that, are there changes to the script that could fix this?

---

### Post by papibe on 2011-10-08
Knowing the tree structure simplify things a lot. Assuming that all Album directories have mp3 files on them:
 
```
#!/bin/bash

cd "/media/Storage/Player Music/"

for f in */*; do
    ls -1 "$f"/*.mp3 > "$f"/"${f##*/}".m3u
done
```
Hope it helps,
Regards.

---

### Post by TeoBigusGeekus on 2011-10-09
> **Nostigex said:**
> Teo,

Maybe I should give more detail as to the structure and location of the  music. I have it on /media/Storage/Player Music/ with this structure:  /Player Music/(Artist Name)/(Album Name)

I assume your script is meant to take care of the entire music folder in one easy step, which is great! But when I use your script from Player Music, it makes playlists with the name of each artist, instead of each album, and places them all in Player Music, instead of within the individual album folders. If I copy the script to an artist folder and run it there, it creates playlists with the name of that artist's albums, but places them in the artist folder instead of within the corresponding album folders. I could manually repeat these steps for each artist, but before I do that, are there changes to the script that could fix this?

Ah... now I see.
Try with this:
```
#!/bin/bash
find -maxdepth 1 -type d ! -name . | while read artist;
do
    cd "$artist"
    find -maxdepth 1 -type d ! -name . | while read folder;
    do
        folder_name=$(basename "$folder")
        cd "$folder_name"
        ls *.mp3>"$folder".m3u
        cd - 
    done
    cd -
done
```
Put it in your Player Music folder and run it as
```
. ./script
```

---

### Post by TeoBigusGeekus on 2011-10-09
> **papibe said:**
> Knowing the tree structure simplify things a lot. Assuming that all Album directories have mp3 files on them:
 
```
#!/bin/bash

cd "/media/Storage/Player Music/"

for f in */*; do
    ls -1 "$f"/*.mp3 > "$f"/"${f##*/}".m3u
done
```
Hope it helps,
Regards.

Your script puts the whole path of the songs (after the Player Music folder) inside the m3u file, making the playlist unplayable, at least on SMPlayer.

---

### Post by papibe on 2011-10-09
Thanks TeoBigusGeekus, you are absolute right . Sorry if I created some confusion.

Still with the spirit of helping the OP, I tested this, and it is working for me:
```
find -type d -links 2 -exec bash -c 'cd "$1"; ls -1 *.mp3 > "${1##*/}".m3u' _ '{}' \; 
```
What is does:
When run on "/media/Storage/Player Music/", it will find subdirectories (-type d), but only 2 levels depth (-links 2), that is, just Albums. For every subdirectory found, cd to it, and create a local playlist.

Regards.

---

### Post by Nostigex on 2011-10-09
OK, I've got what I need.

Thanks for the help guys. :)

---

