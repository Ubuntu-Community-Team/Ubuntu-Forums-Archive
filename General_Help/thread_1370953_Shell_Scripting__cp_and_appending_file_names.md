---
title: "Shell Scripting : cp and appending file names"
date: 2010-01-02
forum: General Help
---

### Post by twjolson on 2010-01-02
I am quite a novice to shell scripting, so I am in need of some help, as this script is above my head.

I have a bunch of files in a folder structure that I need to copy out from the folders and placed in one bulk, folderless folder.  However, some of the files have the same name.

Can anyone write a script, or know better commands than I know, that will traverse the folders, grab the files and write them to a bulk folder, adding a "_1" or "_2" and such as needed to prevent overwriting and allowing all files to be copied?

I have very little programming experience, and much less shell scripting experience, so any help would be great.

---

### Post by twjolson on 2010-01-02
Or is there another Forum that is more suited to shell scripting, either on Ubuntu or around the web?

---

### Post by CharlesA on 2010-01-03
Check here: [http://www.unix-manuals.com/forum/viewtopic.php?t=93](http://www.unix-manuals.com/forum/viewtopic.php?t=93)

You could probably make a script to check if a file already exists and if it does, run x command.

```
#!/bin/bash

FILE=somefile
DATETIME=`date +%Y%m%d` 

if [ -f $FILE ];
then
  echo "$FILE already exists"
  cp $FILE $FILE$DATETIME
else
  cp $FILE
fi

```

I don't know if it would work, but it might be what you are looking for.

---

### Post by kaibob on 2010-01-03
The following will do what you want. You need to change the source and target directory. Some people object to hard-encoding a source directory into a shell script. You can change the script if that is a concern. I tested the script with nested directories containing multiple, identically-named files, and it worked fine.

```
#!/bin/bash

source="/source/directory"
destination="/target/directory"
counter=1

find "$source" -type f | while read found ; do
   file="${found##*/}"
   if [ -f "${destination}/${file}" ] ; then
      while [ -f "${destination}/${file}_${counter}" ] ; do
         counter=$((counter+1))
      done
      cp "${found}" "${destination}/${file}_${counter}"
      counter=1
   else
      cp "$found" "${destination}"
   fi
done
```

BTW, if you want to limit the files copied to those with a particular extension, change the script as follows:

```
find "$source" -type f -iname "*.txt" | while read found ; do
```

---

