---
title: "File management by script (movies)"
date: 2011-03-24
forum: General Help
---

### Post by schopo on 2011-03-24
Heya gurus,

The title may not be as descriptive as I want it to be, but I couldn't think of a better one so let me explain:

I am bussy reorganising loads of scattered movies on my NAS drive and for the sake of learning I want to do as little as possible by hand. More precisely I want to put hardlinks to all movies on the drive in a seperate folder, keeping the originals in place as well.  I.e. find . -iname "*.avi" -exec ln ./AllMovies/ \{\} \;

Now that just does the job for *all* .avi files but there are several additions to the challenge:
 - It should apply on all files that are movies, not just .avi
 - Files smaller than a certain threshold (music videos instead of movies) should be omitted
 - I wish to exclude certain folders that contain home made camera videos
 - Some movies are DVD rips that consist of a few files in a folder. Therefore all .vob files should have their parent directory soft linked instead.

I'd much apreciate anyone who can teach me the tricks of the trade to accomplish this. And please remember I am not asking anyone to "do my work for me", I just want to learn from this.

Tnx all!

Ps: I have root on my buffalo linkstation live, via telnet. If it helps.

---

### Post by DaithiF on 2011-03-25
this won't be complete, but may give you a start:
Now that just does the job for *all* .avi files but there are several additions to the challenge:
 - It should apply on all files that are movies, not just .avi
use the -iregex feature of find to specify a list of movie extensions 
 - Files smaller than a certain threshold (music videos instead of movies) should be omitted
 use the -size +10M feature of find to only pick files above a threshold
- I wish to exclude certain folders that contain home made camera videos
use the -path xxx -prune feature of find to exclude certain dirs.  you can chain these together with -o to exclude several dirs
- Some movies are DVD rips that consist of a few files in a folder. Therefore all .vob files should have their parent directory soft linked instead.
that'll need extra logic within the find loop

```
find /path/to/nas \( -path ./homemovies1 -o -path ./homemoveies2 \) -prune -o -size +10M -iregex '.*\.\(avi\|mov\|mpg\|mpeg\|mp4\) -print | while read file
do
    # figure out file extension
    ext=${file##*.}
    if [[ "$ext" == "vob" ]]; then
        dir=${file%/*}
        # do something with dir here, (unless we've already done it!)
        if [[ ! -e "/somewhere/$dir" ]]; then
            # create soft link here
        fi 
    else
        # its a regular file -- do the hardlink stuff here
    fi 
done
```

---

### Post by schopo on 2011-03-25
It seems rather complete, don't really have time to test it now but I will certainly report how well it works by the end of sunday. 
Luckily I roughly understand what is going on in the script and up next is tweaking it to my taste!

Now all I need to do is give my movies some sensible names, that's pretty impossible to automate ;)

Thanks, and you'll hear how it goes.

---

### Post by J_Wales on 2011-03-25
This is neither here nor there but, one of the things that imo sucks about having movies in multiple file formats is getting them to sort easily. I always rename all my movies with the released year in front and sort alphabetically. Like this 1979_The_Road_Warrior.whatever. then they always line up by year no matter what the extension. Not that it matters, its just my preference. You could name begin their names with how ever you wish them to be sorted by default and sort alphabetically then.

---

### Post by schopo on 2011-03-25
Nice one, but unfortunately I don't have the luxury of having all info about all my movies and I don't feel like searching and typing from all the covers...

Often I just know which movie I'll watch and hit the first letter of it's name to jump to it.

---

