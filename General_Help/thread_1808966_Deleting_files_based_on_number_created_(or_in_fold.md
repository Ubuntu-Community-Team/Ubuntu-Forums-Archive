---
title: "Deleting files based on number created (or in folder?)"
date: 2011-07-21
forum: General Help
---

### Post by Rikeshar on 2011-07-21
Hello everyone. I'm dipping my toes into some bash scripting and was wondering if there was a way to delete a file not based on how old it is, but rather how many other files are currently in the folder... or something to that effect....

What I'm doing is creating a script to back up a folder nightly. I'd like to keep a maximum of 3 backups. However in case the script for some reason fails to run one night (computer turned off possibly) I don't want to set the condition for deletion to be the date.

I know that if I run:

```
find /path/to/files* -mtime +3 -exec rm {} \;
```that it will delete everything older than three days. -atime and -ctime don't seem to be what I"m looking for... is there another command I can use to achieve what I"m trying to?

---

### Post by nothingspecial on 2011-07-21
You want to test how many files are in the folder. Something like


```
#count how many files/folders are in the folder
files=$(ls /path/to/folder | wc -l)
 
#find the oldest file/folder   
oldest=$(ls -lt /path/to/folder | tail -n 1)

#See if there are more than 2
if [[ "$files" -gt 2 ]]

#if there are then delete the oldest
then rm -r "${oldest##*:[0-9][0-9] }"

#If not say so
else echo "Less than 3 backups"
fi
```

Please bear in mind that I just wrote this while having a cigarette break. It's off the top of my head and will fail in many situations.

For example, if there are 25 backups it will still only remove one and leave you with 24.

Or it will fail if your oldest backup has a : in it's name.

And in other ways to.

You'll need to improve it, but it should get you going.

---

### Post by Rikeshar on 2011-07-21
Thanks! I'll give it a go and see what I can do with it. 


And I love your signature by the way :P

---

### Post by sisco311 on 2011-07-21
If you read the files in an array, then the number of elements is the number of files:
```

files=(/path/to/dir/*)
echo "${#files[@]}"

```

Finding the oldest is trickier...

The array will contain the filenames in lexicographical order. If you name your backups as backup-YYYYMMDD (where YYYY is the year, MM is the month and DD is the day), then the first element in the array will be the oldest.

So you have to delete the first n files. Where n is the number of files minus the number of max allowed files.

```

max=3

files=(/path/to/dir/*)
echo "number of files: ${#files[@]}"

nr=$((${#files[@]} - max))
for ((i=0; i<nr; i++))
do
    echo rm -i -- "${files[i]}"
done

```

Otherwise you can try something like:
```

#!/bin/bash

max=3

files=(/path/to/dir/*)
nr=$((${#files[@]} - max))

for ((i=0; i<nr; i++))
do
    files=(/path/to/dir/*)
    oldest="${files[0]}"
    for file in "${files[@]}"
    do
        if [[ "$file" -ot "$oldest" ]]
        then
            oldest="$file"
        fi
    done
    rm -- "$oldest"
done

```

---

### Post by Rikeshar on 2011-07-21
Alright! It worked! Thank you very much :) Took me a while to step  through and try to find out exactly what it was doing, but I -think- I  understand it now.

---

### Post by sisco311 on 2011-07-21
You are welcome!

If you have any questions, please feel free to ask.

---

