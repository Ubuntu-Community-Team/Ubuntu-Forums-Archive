---
title: "How to remove all foldernames which contains spaces in Desktop with a single command?"
date: 2011-06-08
forum: General Help
---

### Post by karthick87 on 2011-06-08
How to remove all foldernames which contains spaces in Desktop with a single command?

---

### Post by ruffEdgz on 2011-06-08
I found this to work on my computer with test directories on my desktop:
```

find ~/Desktop/ -regex .*\ .* -type d -exec rm -Rf {} \;

```
Before deleting any directories, you can verify that it will delete the correct dirs by running this command:
```
find ~/Desktop/ -regex .*\ .* -type d
```
Hope this helps.

---

### Post by karthick87 on 2011-06-09
Thankyou i have checked it, it is scanning sub folder also. I just want to delete only the main folder..

For Example,

```
/home/karthick/Desktop/Images/"Hindi Films"
``````
[COLOR=Red]/home/karthick/Desktop/"Hindi Films"[/COLOR]
```In the above Example ie i want to delete the folder in the second line and not  the folder in the first line.  I just want to delete the folders which contains space in this path **[COLOR=Red]/home/operator1/Desktop/[/COLOR] **and not in the subfolders which contains space in ~/Desktop/**[COLOR=Red]Example[/COLOR]**/"[COLOR=Blue]Hindi Films[/COLOR]"

---

### Post by ruffEdgz on 2011-06-09
In that case, then we just need to add a max-depth to the find command:
```
find ~/Desktop/ -maxdepth 1 -regex .*\ .* -type d -exec rm -Rf {} \;
```

To verify, I did the following command on my Desktop with directories and subdirectories inside of them and it only found the top level directories:
```
find ~/Desktop/ -maxdepth 1 -regex .*\ .* -type d
```

Cheers!

---

### Post by karthick87 on 2011-06-09
Yeah thanks a lot :)

One more condition, if i want to exclude a particular directory from deletion which contains spaces, How will you modify the command?

---

### Post by ruffEdgz on 2011-06-09
I wish there was an easy 'one liner' for excluding a file/directory when using find but right now, there isn't :( if anyone knows of a way to complete his request in find or another way, I would be interested in that as well.

I have a script that you can use if you do wish to exclude one of those 'spaced' directories:
```

#!/bin/bash
IFS=$'\n'
exclude=$1
desktop_path="/home/user/name/here/Desktop"
echo $exclude
for i in $(find ~/Desktop/ -maxdepth 1 -regex .*\ .* -type d); do
   if [ $i != "$desktop_path/$exclude" ]; then
      rm -rf $i 2>&1
   fi
done

```
Make sure you change the variable **desktop_path** inside this script to your desktop full path. It is important to have ;)

When you execute it, just do the following:
```

/path/to/executable/script "untitled folder"

```

I can also make a script for multiple folders if you like but that will take me some time to get the logic in there. Hope this helps.

Cheers!

---

### Post by karthick87 on 2011-06-16
Thanks a lot :)

---

### Post by Vaphell on 2011-06-16
find can exclude stuff
```
find . -maxdepth 1 -name '* *' ! -name 'some name'
```

---

