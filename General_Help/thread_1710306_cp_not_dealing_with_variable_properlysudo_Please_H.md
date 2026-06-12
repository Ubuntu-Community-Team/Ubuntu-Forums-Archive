---
title: "cp not dealing with variable properly?sudo Please Help"
date: 2011-03-19
forum: General Help
---

### Post by solidium on 2011-03-19
I am having trouble with a script that is supposed to :

a)take all the jpg pictures in a given directory/parameter and create thumbnails of it in a directory on the desktop. 

e.g 
from /here/are/the/files.jpg to ~/Desktop/parser-the/files.png

this is my script: all the individual parts work but it falls apart when i put them together :sad: any help would be appreciated ](*,)

```
  for picturesource in $(ls ${1}/*.[jJ][pP][gG])
                do
                        echo this is the picturesource $picturesource;
                        destination=~/Desktop/parser-"${picturesource}";
                        echo this is the destination $destination;
                        /bin/cp -Rf ${picturesource} ${destination}  && echo cp done ;
                        basenames=`basename ${destination}`;
                        echo this is basename $basenames;
                        echo eval="convert -thumbnail 137 $picturesource ${destination}.png" && echo eval and it goes here $destination;
                        ls ~/Desktop/parser* && echo now listing files in the folder
                        sleep 1
                done


```

Heres the output:

```
this is the picturesource test/hdgef.jpg
this is the destination /home/arbutt1/Desktop/parser-test/hdgef.jpg
/bin/cp: cannot create regular file `/home/arbutt1/Desktop/parser-test/hdgef.jpg': No such file or directory
this is basename hdgef.jpg
eval=convert -thumbnail 137 test/hdgef.jpg /home/arbutt1/Desktop/parser-test/hdgef.jpg.png
eval and it goes here /home/arbutt1/Desktop/parser-test/hdgef.jpg
/home/arbutt1/Desktop/parser-
now listing files in the folder


```

any help would be extremely appreciated :)

---

### Post by Rinzwind on 2011-03-19
Looking at it I (not being an expert) am thinking this is weird:

`/home/arbutt1/Desktop/parser-test/hdgef.jpg'

that ` looks wrong there. Looks like it is part of the filename

---

### Post by solidium on 2011-03-19
> **Rinzwind said:**
> Looking at it I (not being an expert) am thinking this is weird:

`/home/arbutt1/Desktop/parser-test/hdgef.jpg'

that ` looks wrong there.

True but I cant see how that got in there. Theres nothing like it in my original script. : \

---

