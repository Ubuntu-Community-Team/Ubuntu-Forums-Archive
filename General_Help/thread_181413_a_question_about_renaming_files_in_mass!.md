---
title: "a question about renaming files in mass!"
date: 2006-05-24
forum: General Help
---

### Post by zeltak on 2006-05-24
Hi

I have 1000 movies i would like to mass rename in a strange way.  I  have txt files with the movie name as file name for each movie i own . the mpeg movie files are unnamed.  does anyone know of a way to automate a filename transfer from a txt file to mpg file? for example i have satrwars.txt file and a 1.mpg file. i would like to transfer the filename so it would give me starwars.mpg. i would like to do it for all movies 

thx alot in advance

Zeltak

---

### Post by elamericano on 2006-05-24
How will you know that starwars.txt goes with 1.mpg and not 37.mpg?

---

### Post by zeltak on 2006-05-24
hi

thx for the answer. all my mpeg movie files are "dummy" files and are the same. they just act as an avatar for the real movies for mythtv. so if every txt file would just take the next mpg file avilable it would do fine

thx

Zeltak

---

### Post by seth0x2b on 2006-05-24
I put this together really quick:
Create a file called movies.txt in the .mpg file folder, and write the movie names in it:
```

film_1
film_2
film_3
film_4
film_5

```
Then create a new text file and paste this:
```

import os
file = open("movies.txt")
n = 1
ext = '.mpg'
while 1:
    line = file.readline()
    if not line:
        break
    os.system('mv '+str(n) + ext + ' ' + line.rstrip() + ext)
    n = n + 1
    pass

```
Save it in the .mpg's folder as mass.py or whatever, open a command prompt in that folder and run python mass.py
It will read the file movies.txt and substitute 1.mpg with the first line + the extension, 2.mpg with the second and so on. 

Cheers

---

### Post by zeltak on 2006-05-24
thx alot seth0x2b for the answer!

unfortunantly it gives me an erroe message (here is part of it):
mv: target `Contact.mpg' is not a directory
mv: target `Mind.mpg' is not a directory
mv: target `Wanda.mpg' is not a directory
mv: target `Violence.mpg' is not a directory
mv: target `Wind.mpg' is not a directory
mv: target `Sequel.mpg' is not a directory
mv: target `Spider.mpg' is not a directory
mv: target `Beauty.mpg' is not a directory
mv: target `X.mpg' is not a directory
mv: target `Psycho.mpg' is not a directory
mv: target `Sunday.mpg' is not a directory
mv: target `Now.mpg' is not a directory
mv: target `Future.mpg' is not a directory
mv: target `2.mpg' is not a directory
mv: target `3.mpg' is not a directory
mv: target `Begins.mpg' is not a directory
mv: target `America.mpg' is not a directory
mv: target `Malkovich.mpg' is not a directory
mv: target `Beckham.mpg' is not a directory
mv: target `Hill.mpg' is not a directory
mv: target `Fish.mpg' is not a directory
sh: Teds: command not found
mv: target `Columbine.mpg' is not a directory
mv: target `Bear.mpg' is not a directory
mv: target `Almighty.mpg' is not a directory
mv: target `Ho-tep.mpg' is not a directory
mv: target `Kid.mpg' is not a directory
mv: target `Away.mpg' is not a directory
sh: -c: line 0: syntax error near unexpected token `('
sh: -c: line 0: `mv 36.mpg Cat Stevens: Majikat (Earth Tour 1976).mpg'

i think its trying to create directories wheras im trying to create mpg files. hope this fantastic script can work

thx

Zeltak

---

### Post by seth0x2b on 2006-05-24
That's weird. It works for me.
I have the text file movies.txt, mass.py and 1,2,3,4,5.mpg in the same folder.
CD to the folder, python mass.py an puf!It works.
Make sure you have all the files in the same folder.

Make sure you have only one movie name  per line. Also..there might be problems when using complex characters in the name(like "()" 
and so on).You also CAN'T use spaces with that script because "mv" interprets "Cat Stevens" as 2 separate filenames.It is a veeeeeeeeeery basic script! I usually use a file_000.mpg convention. Linux(or command prompts/terminals in general) don't like spaces very much.

Cheers

---

### Post by elamericano on 2006-05-24
You could try a simple shell script if they are all in the same directory.
```

for file in *.mpg
do
    textfile=`ls *.txt | head -n 1`
    if test -n "$textfile"
    then
        newname=`echo "$textfile" | sed -e 's/txt$/mpg/'`
        mv "$file" "$newname"
        rm "$textfile"
    else
        exit
    fi
done

```

Maybe this could be more efficient, but it's easy to modify to your own purposes. The script will stop processing when it runs out of mpg or txt files. (it needs to remove text files after renaming to find the next one. be sure they're writable.) Spaces are allowed.

---

### Post by simonn on 2006-05-24
[QUOTE=seth0x2b]That's weird. It works for me.
[/QUOTE]

You need to have quotes around the file names

    os.system('mv '+str(n) + ext + ' ' + line.rstrip() + ext)
    
Should be something like:

    os.system('mv \"'+str(n) + ext + '\" \"' + line.rstrip() + ext + '\"')
   
I do not know Python, so I do not know how to put quotes into strings, but replace \" with whatever you need to.

---

