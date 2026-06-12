---
title: "moving and rename files help...."
date: 2009-12-16
forum: General Help
---

### Post by pentat0nicc on 2009-12-16
Hi
I would like some help/advice on and problem i have with moving video files from my camcorder. 
The camcorder does not store the files in tidy way....

I have a direcotory for each day, PRG001 PRG0002 PRG00A etc, and in there are the vidoes files called MOV001.MOD MOV002.MOD etc etc.

I have a command that moves the .MOD files from all the directories to one directory..
find . -iname "*.mod" -exec cp {} ../mpg/ \;

then i run a rename command to change the file extension from .MOD to .mpg, which allows me the play the files on my PS3 etc...which is
rename -v 's/\.MOD$/\.mpg/' *.MOD

The problem is that because etc day (or folder PRG00X) contains a MOV001 or MOV002, the find and copy command overwrites the files.

So i need a command/script to go into the PRG00X directories and rename the files with a unique name, ideally appending the date to the files, then i can move them one directory, rename the file extension and i am done.

I would like to have a nice script to do this, and not a application if that possible

Any thoughts.....

---

### Post by ghostdog74 on 2009-12-16
you can use a date variable plus a random variable
```

var=$(date +"%Y%m%d%H%M%s-$RANDOM")

```

---

