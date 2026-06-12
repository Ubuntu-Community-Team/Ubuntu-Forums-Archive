---
title: "syntax  ls command question for generating links."
date: 2010-08-06
forum: General Help
---

### Post by titanicmusic14 on 2010-08-06
I am trying to find out can I use the ls command to list my wav files in such a way that it follows this format: <OPTION value="/home/filepath.wav">My first file </OPTION>
I would like to know if there is a way I could simplify this because I have about 100 wav files. They all have names and if I could get them listed then a space then the name again with something behind it I could use the find replace feature to generate a bunch of links . If not is there a script out there that could use this format to generate links under this format?
BTW this is for a pull down menu that would control windows media player

---

### Post by worksofcraft on 2010-08-06
you could start with something like:

```

for f in *.wav
do
	echo '<OPTION value="'$f'">'$f'</OPTION>'
done

```

---

### Post by titanicmusic14 on 2010-08-06
thanks but could you explain why just so us guys who are somewhat new to this could study it and tweak it possibly in the future... Also where do I enter this, the command line?




> **worksofcraft said:**
> you could start with something like:

```

for f in *.wav
do
    echo '<OPTION value="'$f'">'$f'</OPTION>'
done

```

---

### Post by worksofcraft on 2010-08-06
for f in *.wav repeats the commands between do and done
assigns the value of each .wav file name to a variable named $f on successive iterations

The echo command simply writes out the string you give it substituting the $f.

I think you can just type that lot at a command prompt in the folder where all the .wav files are but it may be handier if you put it in a shell script file so you can redirect the output into a text file to copy into your html.

soz about that got interrupted...
so yes make a file called something like lswavs.sh and put those commands in it. Then make the file executable and run it using commands:
```

chmod +x lswavs.sh
./lswavs.sh>mywavs.txt

```

---

### Post by surfer on 2010-08-06
try to write this in a file:

```

#!/bin/bash

for f in *.wav
do
    echo '<OPTION value="'$f'">'$f'</OPTION>'
done

```

name the file something like list_wav.sh, make this file executable and run it in the shell with
```

./list_wav.sh

```

(ups, the last edit of the post right above just stated about the same)

---

### Post by darolu on 2010-08-06
Complementing the previous answers, you may want to print it to a text file or whatever type of file your player needs:
```
./list_wav.sh > myoptions.txt
```

---

### Post by titanicmusic14 on 2010-08-06
ooops... thx
But this list is in a file called wav.txt how do i get it to do that stuff to the file?

> **surfer said:**
> try to write this in a file:

```

#!/bin/bash

for f in *.wav
do
    echo '<OPTION value="'$f'">'$f'</OPTION>'
done

```name the file something like list_wav.sh, make this file executable and run it in the shell with
```

./list_wav.sh

```(ups, the last edit of the post right above just stated about the same)

---

### Post by titanicmusic14 on 2010-08-06
You guys are geniuses

---

### Post by titanicmusic14 on 2010-11-11
I still use this script thanks a bunch!!
> **darolu said:**
> Complementing the previous answers, you may want to print it to a text file or whatever type of file your player needs:
```
./list_wav.sh > myoptions.txt
```

---

