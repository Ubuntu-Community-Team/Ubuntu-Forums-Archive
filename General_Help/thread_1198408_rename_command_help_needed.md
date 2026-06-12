---
title: "rename command help needed"
date: 2009-06-27
forum: General Help
---

### Post by bowens44 on 2009-06-27
Hello all,
I have been trying to use the rename command to auotmate the renaming of a couple of dozen files I have downloaded every evening. I have had no luck.

The file names are quite long, usually about 20+ characters. What I need to do is rename the file to the first 12 characters plus the extension.

Example:

original file name: aug090101-10_adsrecgrthyds.csv

new file name:      aug090101-10.csv



I need to put this in a script that I can schedule to run every morning.

Thanks!!

---

### Post by saj0577 on 2009-06-27
> **bowens44 said:**
> Hello all,
I have been trying to use the rename command to auotmate the renaming of a couple of dozen files I have downloaded every evening. I have had no luck.

The file names are quite long, usually about 20+ characters. What I need to do is rename the file to the first 12 characters plus the extension.

Example:

original file name: aug090101-10_adsrecgrthyds.csv

new file name:      aug090101-10.csv



I need to put this in a script that I can schedule to run every morning.

Thanks!!

Hey,

I have just been learning python and I believe this is possible through python, if no one else gives you a solution first I will post the code when I finished it.

Saj

---

### Post by colau on 2009-06-27
> **bowens44 said:**
> Hello all,
I have been trying to use the rename command to auotmate the renaming of a couple of dozen files I have downloaded every evening. I have had no luck.

The file names are quite long, usually about 20+ characters. What I need to do is rename the file to the first 12 characters plus the extension.

Example:

original file name: aug090101-10_adsrecgrthyds.csv

new file name:      aug090101-10.csv



I need to put this in a script that I can schedule to run every morning.

Thanks!!

Does [this]("http://www.filetransit.com/files.php?name=Batch_Rename_Linux") help?

---

### Post by saj0577 on 2009-06-27
> **saj0577 said:**
> Hey,

I have just been learning python and I believe this is possible through python, if no one else gives you a solution first I will post the code when I finished it.

Saj


I have got it using the files first 12 and the extension just need to make it rename them to it now.

Saj

---

### Post by bowens44 on 2009-06-27
> **colau said:**
> Does [this]("http://www.filetransit.com/files.php?name=Batch_Rename_Linux") help?

Thanks but no. I really want to do this with either the linux/debian rename command or a script. I am trying to automate some activities on a server that will be be for the most part unattended. I don't want to have to interact with the server to accomplish my tasks.

---

### Post by saj0577 on 2009-06-27
Almost done it just a few problems. Not the best at python.

Saj

---

### Post by saj0577 on 2009-06-27
Got it all working I think goign to test it tonight will publish it in next few hours when I am home again.

Saj

---

### Post by kaibob on 2009-06-27
The following will do what you want:

```
rename -n 's/(.{12}).*/$1.csv/' *.csv
```

The -n option directs rename to do a dry run and show proposed changes. Substitute -v for -n to actually rename the files.

You can do the same thing with a for loop:

```
#!/bin/bash

for FILE in *.csv ; do
   NEWFILE=${FILE:0:12}
   cp "$FILE" "$NEWFILE.csv"
done
```

I used cp rather than mv in the above as a precaution.

---

### Post by ghostdog74 on 2009-06-28
> **bowens44 said:**
> Hello all,
Example:

original file name: aug090101-10_adsrecgrthyds.csv

new file name:      aug090101-10.csv


you can try my Python script called file renamer (see my sig last link). eg usage
```

# filerenamer.py -c 11:-4  -l "*.csv"
==>>>>  [ /home/aug090101-10_adsrecgrthyds.csv ]==>[ /home/aug090101-1.csv ]


```

remove "-l" option to commit changes.

---

### Post by bowens44 on 2009-06-28
Thanks for all the reponses! I got exactly what I needed!! kaibob , your reponse was key.

---

