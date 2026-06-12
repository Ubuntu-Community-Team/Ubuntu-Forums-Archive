---
title: "Scripting Help"
date: 2011-04-14
forum: General Help
---

### Post by TheFuzz4 on 2011-04-14
I am not sure if this is the right area for this or not and if not I apologize.  So this is what I want to do.  I am currently in the process of converting all of my DVD's to m4v files.  Now while this process goes quite quickly, the process of moving them from my desktop to my NAS is quite tedious due to the fact that I have to manually create all of the folders and then manually move all of the files.  So I've written a few bash scripts for work related items but this will be my first script of this nature.  Now in theory this sounds like a very straight forward script.  
1. Get the contents out of a directory
2. Create a directory in the destination matching the name of the file from the source.  
Problem is that the sources have spaces in them.  
When I do a for loop such as  for i in `ls`; do echo $i ; done it prints out all of the movies but with every space it treats it as a new line.  now I know I'll also have to use some sed magic in here as well in order to ignore the file extension.  What is the best method to escape the spaces with a command like this while I'm attempting to load up the variable.  In theory once all of this is done I'll setup some cron jobs that will handle all of the grunt work for me :).  Thank you in advance for your help with this.

---

### Post by sisco311 on 2011-04-14
```
for file in *
do
  echo "$file"
  echo "file without extension: ${file%.*}"
done
```

See:
[http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29](http://mywiki.wooledge.org/BashPitfalls#for_i_in_.24.28ls_.2A.mp3.29)
and
[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

---

### Post by TheFuzz4 on 2011-04-14
Thank you very very much for your help with that.  I cannot believe that it is that easy.

---

### Post by idoitprone on 2011-04-14
nvm, i am too slow

---

### Post by TheFuzz4 on 2011-04-16
So I thought that for the greater good I would post my script examples in here in case someone can use them.

Of course they can be used for moving anything that you want in my case it was just for movies. 

```
#!/bin/bash

#This script will move the movies from the completed movies dir to the share

MOVIE_DIR="Your/Destination/Path"

cd ~/Source/Of/Movies

for i in *; do
  if [ ! -d  "${MOVIE_DIR}"/"${i%.*}" ]; then
    #echo "Make the directory"
    mkdir "${MOVIE_DIR}"/"${i%.*}";
  fi
  mv "$i" "${MOVIE_DIR}"/"${i%.*}";
done
```

Then this one if for handbrake to take an iso file and convert it to a m4v file.

```
#!/bin/bash

COMPLETED_VIDEO=~/Path/Where/You/Want/Your/Completed/Movie/To/Go
UNENCODED_MOVIES=~/Path/Of/ISO



cd "$UNENCODED_MOVIES"

for i in * `| grep iso`; do
  HandBrakeCLI -i "${i}" -o "${i%.*}".m4v ${COMPLETED_VIDEO}
  rm "${i}"
done
```

I think in my next rendition I will combine these into one script but for now I have 2 cron jobs for these.

---

