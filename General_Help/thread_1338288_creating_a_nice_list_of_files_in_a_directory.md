---
title: "creating a nice list of files in a directory"
date: 2009-11-26
forum: General Help
---

### Post by markdavidoff on 2009-11-26
I have a rather large collection of movies and TV shows. Each is categorized under genre, and within that, other folders for sub-collections eg. 

Movies/Action/<list of movies>
Movies/Action/Matrix Triliogy/<list of movies>
Movies/Comedy/<list of movies>
Movies/Comedy/Austin Powers Trilogy/<list of movies>
etc.

And I would like it to be output into a list as follows (or similar):

Movies:
[INDENT]Action:
[INDENT]<list of movies>
<list of movies>
<list of movies>
<list of movies>
[INDENT]Matrix Triliogy:
[INDENT]<list of movies>
<list of movies>
<list of movies>[/INDENT][/INDENT][/INDENT][/INDENT]
[INDENT]Comedy:
[INDENT]<list of movies>
<list of movies>
<list of movies>
<list of movies>
[INDENT]Austin Powers Trilogy
[INDENT]<list of movies>
<list of movies>
<list of movies>[/INDENT][/INDENT][/INDENT][/INDENT]

etc...

There is probably a really easy way of doing this with ls, but I'm not 100% sure of the correct syntax

---

### Post by audiomick on 2009-11-26
you might be looking for the "find" command.

do
```
man find
```
to get the manual page for it. It is a bit of a monster, but around line 734 there are options to print to a file. That should give you a text file, which you then might want to format a bit in Open Office or similar.

There is also the command grep, ( manual man grep ) which looks for the occurrence of specified characters in files, and can be combined with find. 
I don't know if that is any use to you, but I hope so.

---

### Post by kaibob on 2009-11-26
Deleted by kaibob

---

### Post by akakingess on 2009-11-26
> **kaibob said:**
> It is easy to create a text document with a list of directories and files. The difficulty is getting it formatted as you want.

If no one has an easier suggestion, you can use the following. The only thing it does not do is indent subdirectories. You need to change /target/directory to whatever is appropropriate.

```
#!/bin/bash

olddir=none

find /target/directory -type f | sort -d | while read files ; do
   for file in "$files" ; do
      path="${file%/*}"
      dir="${path##*/}"
      name="${file##*/}"
      [ "$dir" != "$olddir" ] && echo -e "\n${dir}" >> media_list
      echo "   $name" >> media_list
      olddir="$dir"
   done
done
```

I would do this and then copy and paste into something like OpenOffice Word Processor to do the formatting if you were just looking at coming up with a "written" catalog to refer to for looking where a certain title is...

---

### Post by markdavidoff on 2009-11-26
That worked nearly perfectly, except that the files that weren't in subdirectories eg.

Movies/Action/<list of movies>

were scattered under several "Action:"
lines instead of one "Action" Directory

Good enough for now until a better solution is thought of. Thanks

---

### Post by kaibob on 2009-11-26
> **markdavidoff said:**
> That worked nearly perfectly, except that the files that weren't in subdirectories eg.


I checked and you are correct--none of my suggestions do what you want. Perhaps another forum member will be able to help.

---

### Post by Keith Hedger on 2009-11-26
try ```
ls -R --hide "*.jpg"  -1
``` as a start, my movie files have a similar hierarchy and gives this```
.:
Action
Comedy
Drama
Horror
Musicals
Mythology
Other
RomCom
Sci-Fi

./Action:
Casino Royale.avi
Collateral Damage.avi
Con Air.avi
Death Race.avi
Die Hard 4 0.avi
Dragon Wars.avi
Entrapment.avi
Face off.avi
Highlander.avi
Hostage.avi
Sin City.avi
Super Heroes

./Action/Super Heroes:
Batman Begins.avi
Blade 2.avi
Blade Trinity.avi
Daredevil.avi
Elektra.avi
Fantastic Four 2.avi
Fantastic Four.avi
Ghost Rider.avi
Wolverine.avi

./Comedy:
Bewitched.avi
Big Fish.avi
Calendar Girls.avi
Cats And Dogs.avi
Evolution.avi
Garfield 2.avi
Haunted Mansion.avi
Shrek 1.avi
Shrek 2.avi

./Drama:
Brotherhood Of The Wolf.avi
Children Of Men.avi
Coyote Ugly.avi
Defiance.avi
Enemy Of The State.avi
Far And Away.avi
Flight Of The Phoenix.avi
Gran Torino.avi
Knowing.avi

./Horror:
Other
Vampires
Werewolves

./Horror/Other:
Birth.avi
Boo.avi
Creep.avi
Hanibal Rising.avi
Hemoglobin.avi
Hostel 1.avi
Hostel 2.avi

./Horror/Vampires:

./Horror/Werewolves:
An American Werewolf In London.avi
An American Werewolf In London.JPG
Dog Soldiers.avi
Howling 3.avi

./Musicals:
Mamma Mia.avi
Moulin Rouge.avi

./Mythology:
10000 B.C..avi
300.avi
Beowulf.avi
Elizabeth The Golden Age.avi
King Arthur.avi

./Other:
A Knights Tale.avi
Corpse Bride.avi
Dungeons And Dragons.avi
Harry Potter And The Chamber Of Secrets.avi
Harry Potter And The Order Of The Phoenix.avi
Harry Potter And The Philosophers Stone.avi
Human Traffic.avi

./RomCom:
Australia.avi
Australia.JPG
Bridget Jones 2.avi
Bridget Jones Diary.avi
S.W.A.L.K.avi

./Sci-Fi:
1984.avi
A Clockwork Orange.avi
Aeon Flux.avi
Alien Vs Predator.avi
Armageddon.avi
Constantine.avi
Dark Star.avi
Doom.avi
Doomsday.avi
Final Fantasy VII.avi
Hitch Hikers Guide To The Galaxy.avi

```
I use the hide to hide the corresponding jpeg files for each movie see the man page for ls for more details

---

### Post by diesch on 2009-11-26
```

#!/bin/sh

dir="$1"
[ -z "$dir" ] && dir=$PWD

title=${dir##*/}

INDENT=${INDENT:-}

echo "$INDENT$title:"
INDENT="      $INDENT"
if ls "$dir"/* 2>1 >/dev/null; then
    for f in "$dir"/*; do
    if [ -d "$f" ]; then  
        INDENT="$INDENT" $0 "$f"
    else
        echo "$INDENT${f##*/}"
    fi
done
fi

```

---

### Post by diesch on 2009-11-26
There also *tree* (not installed by default)

---

### Post by markdavidoff on 2009-11-27
diesch, you are a legend!

---

