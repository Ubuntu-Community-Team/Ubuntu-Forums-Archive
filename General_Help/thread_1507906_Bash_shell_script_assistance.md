---
title: "Bash shell script assistance"
date: 2010-06-12
forum: General Help
---

### Post by Haagimus on 2010-06-12
I have written a shell script that randomly selects a movie from my movie HDD (over 1100 movies) so that i dont have to troll through when I just want to watch something random. My question is, is there any way to set up this script to basically tag movies with a number of times played or last time played, so i can set it up to select movies that havent played as frequently before playing ones i have watched first. Im guessing i would have to output a file or something in the script with a reference table within but i dont know how to do it. another idea would be to incorporate the date accessed of all the files and ones with an older date accessed get moved to the top of the selection list. any help with this would be really appreciated. im still fairly new to BASH but im not a total beginner.

Here is the functional script now:
cd '/media/2TB Media/01. Movies'
set -- *
length=$#
m=$(( $RANDOM % ($length + 1) ))
vlc --one-instance --volume 1024 "${!m}"
exit 0

---

### Post by mike2357 on 2010-06-12
I think that before you continue programming, you should decide exactly what you want your selection criteria to be.  Do you want true randomness?  It sounds like you have what you want.  Do you want to select the movie that you haven't watched the longest?  Then you can use the "touch" command each time you watch a move, which would update the time stamp of the movie file, then you can use "ls -tr | head -1" to find one not watched in awhile.  Or, each time you watch a movie, you could write a record to either an output file or a database and use it to select your next one.  Over time, random selection should result in a large variety of movies watched, and would give you the benefit of not having them played in the same order.  But with 1,100 movies, it will take quite a while to see them all.  You could get the same result by going through your list of movies alphabetically, as long as you watched new movies as you acquired them.

---

### Post by prodigy_ on 2010-06-12
If you just want a counter, something like this will suffice:```
f_WatchCounter () {
        [ ! -f "$1" ] && return 1
        touch ../list_watched
        WATCHED=$(< "../list_watched" grep "$1")
        if      [ -z "$WATCHED" ]
                then
                        echo "${1} 1" >> ../list_watched
                else
                        COUNT=$(echo $WATCHED | awk -F' ' '{ print $NF }')
                        (( COUNT++ ))
                        sed -i -e "s/${WATCHED}/${1} ${COUNT}/" ../list_watched
        fi
}
```

To pass **${!m}** to this function you'll just need to insert ```
f_WatchCounter "${!m}"
``` line into your code.

---

