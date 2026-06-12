---
title: "script to make symlinks regularly?"
date: 2006-05-10
forum: General Help
---

### Post by jms830 on 2006-05-10
I'm looking for a script (or some commands to get me started) that can make symlinks in one folder from a large amount of folders in other locations. To better explain:

I have music in a folder called electronic.  In this folder are more folders broken down like this "/electronic/artist/album/".  I have a folder on my desktop that I want to have a symlink to each artist in the electronic folder, and I want to be able to quickly update the desktop folder with new links when I move/add artists around in the electronic folder (and hopefully would avoid link doubles).

I also have folders for rock, rap, underground rap, and underground rock, which are set up like my electronic folder.  I would like symlinks for all the artists in these as well.

I'm guessing this can be done using "ln -s" with asterixes, I just don't know the syntax.  In the end I would hope to have a script that I could run to update my folder of symlinks easily, any suggestions? I hope I was clear, thank you!

---

### Post by kabus on 2006-05-10
[QUOTE=jms830]

I have music in a folder called electronic.  In this folder are more folders broken down like this "/electronic/artist/album/".  I have a folder on my desktop that I want to have a symlink to each artist in the electronic folder[/QUOTE]

My attempt, not tested though:
```

for dir in electronic/*; do ln -s "$dir" "~/Desktop/music/${dir##*/}"; done
```

---

### Post by jms830 on 2006-05-11
I've been trying to do what you wrote but maybe I'm not understanding something. I get this output:

```
**~/Desktop/music/electronic$** ln -s "$dir" "~/Desktop/music/${dir##* /}"
ln: creating symbolic link `~/Desktop/music/' to `': No such file or directory
```

---

### Post by Ramses de Norre on 2006-05-11
mkdir ~/Desktop/music

---

### Post by kabus on 2006-05-11
First you'll have to adjust the paths :
```

for dir in SOURCE/*; do ln -s "$dir" "TARGET/${dir##*/}"; done

```

Replace 'SOURCE' with the full path to your electronic folder.
Replace 'TARGET' with the path to the folder where you want the symlinks created (and make sure the folder exists).

You'll have to run the whole line, including the 'for' and 'done'. 

Any reason why you don't just create a link to the 'electronic' folder ?

---

### Post by jms830 on 2006-05-11
Ok, I get some results with

```
for dir in /home/jordan/Desktop/music/electronic/*; do ln -s "$dir" "~/Desktop/music_shortcuts/${dir##*/}"; done
```

but then it spits out a list of all my artist folders but doesn't make links b/c there isn't a directory there or something already.  Example output:
```
ln: creating symbolic link `~/Desktop/music_shortcuts/2 Many DJ\'s' to `/home/jordan/Desktop/music/electronic/2 Many DJ\'s': No such file or directory
ln: creating symbolic link `~/Desktop/music_shortcuts/Alan Braxe' to `/home/jordan/Desktop/music/electronic/Alan Braxe': No such file or directory
ln: creating symbolic link `~/Desktop/music_shortcuts/Annie' to `/home/jordan/Desktop/music/electronic/Annie': No such file or directory
ln: creating symbolic link `~/Desktop/music_shortcuts/Basement Jaxx' to `/home/jordan/Desktop/music/electronic/Basement Jaxx': No such file or directory
ln: creating symbolic link `~/Desktop/music_shortcuts/Books, The' to `/home/jordan/Desktop/music/electronic/Books, The': No such file or directory
ln: creating symbolic link `~/Desktop/music_shortcuts/Boom Bip' to `/home/jordan/Desktop/music/electronic/Boom Bip': No such file or directory

```

I should also note that ~/Desktop/music/electronic is the REAL location
and I want the symlinks to be in ~/Desktop/music_shortcuts

The reason I don't just put a link to my electronic folder is because I also have rock, rap, underground rap, underground rock folders, and while I want my music to be organized in these folders, I want a quick folder full of shortcuts that I can open and just start typing an artist's name and get to the folder.

---

### Post by kabus on 2006-05-11
See my post above, I think I've made it a bit clearer. Make sure the folder where the symlinks are supposed to be created already exists.

---

### Post by jms830 on 2006-05-11
excellent, it worked, I had to put /home/ instead of ~, cool.

If I wanted to exclude several folders, could I add something to the end of the script like

rm ln -s /home/jordan/Desktop/music/electronic/folder_i_dont_want

---

### Post by ZylGadis on 2006-05-11
rm and ln are separate commands. ln creates a link, i.e. a file which points to another file, while rm removes a file (any file, including one that points to another one, i.e. a symbolic link). So simply do
rm path_to/file_i_dont_want
:)

---

### Post by jms830 on 2006-05-11
EDIT: I simply typed the wrong path, ignore what I had here before

---

### Post by jms830 on 2006-05-11
Is there a command I can add so that broken links are automatically cleaned up in ~/Desktop/music_shortcuts

Thanks very much to everyone, you have all been extremely helpful.

EDIT: I installed the package symlinks and add this command to the script

```
symlinks -dr "/home/jordan/Desktop/.music_shortcuts"
```

works great! I now keep all my shortcuts in "~/Desktop/.music_shortcuts" (which is hidden) and have a link on my panel to the folder. Then I just start typing an artist name and there it is, while I can still keep my physical organization of them as well!

**Here is the script in case anyone wants to learn from this post:**
```
#!/bin/bash

for dir in /home/jordan/Desktop/music/electronic/*; do ln -s "$dir" "/home/jordan/Desktop/.music_shortcuts/${dir##*/}"; done

for dir in /home/jordan/Desktop/music/rock/*; do ln -s "$dir" "/home/jordan/Desktop/.music_shortcuts/${dir##*/}"; done

for dir in /home/jordan/Desktop/music/rock/Underground, Emo, Indie/*; do ln -s "$dir" "/home/jordan/Desktop/.music_shortcuts/${dir##*/}"; done

for dir in /home/jordan/Desktop/music/rap/*; do ln -s "$dir" "/home/jordan/Desktop/.music_shortcuts/${dir##*/}"; done

for dir in /home/jordan/Desktop/music/rap/Underground Rap/*; do ln -s "$dir" "/home/jordan/Desktop/.music_shortcuts/${dir##*/}"; done

rm -d "/home/jordan/Desktop/.music_shortcuts/Underground, Emo, Indie Rock"
rm -d "/home/jordan/Desktop/.music_shortcuts/Underground Rap"
rm -d /home/jordan/Desktop/.music_shortcuts/*.mp3

symlinks -dr "/home/jordan/Desktop/.music_shortcuts"

echo "Music Library Shortcuts Collected"

exit
```

---

### Post by jms830 on 2006-05-11
UMMMM.... so I THOUGHT it was working great, but somehow I made a symlink in every artist's folder to itself... that just keeps linking and linking to itself... HELP??

I mean I can just delete them manually if I have to from each artist folder, but I'd like the script to work and not do it. Thanks again

EDIT: I added this to the end of the script to take care of it... it renames the music folder to music1, deletes the symlinks, and then renames it back to music.

```
mv /home/jordan/Desktop/music /home/jordan/Desktop/music1
symlinks -dr "/home/jordan/Desktop/music1"
mv /home/jordan/Desktop/music1 /home/jordan/Desktop/music
```

---

