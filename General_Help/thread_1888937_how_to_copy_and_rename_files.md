---
title: "how to copy and rename files?"
date: 2011-11-30
forum: General Help
---

### Post by sohlinux on 2011-11-30
Hi,

I have 300 directories which all have sub directories with images inside them, 

001.jpg  upto 120.jpg 

I need to copy all the images named 001.jpg from each of the 300 directories/subdirectories, copying them all into a new folder.

so the end product will have a new folder with 300 images all having new names.

I tried it with konqueror search and copy but each time it asks me to manually rename the files.

How can this be done in ssh or is there some other software capable of this?

thanks

---

### Post by Lampi on 2011-11-30
what new name do you want to give them?

---

### Post by sohlinux on 2011-11-30
> **Lampi said:**
> what new name do you want to give them?

any name, it doesnt really matter.

thanks

---

### Post by sohlinux on 2011-11-30
any name would be great but if possible to rename the images the same name of the folder where they came from for example tom001.jpg if it was copied from the folder named tom. bearing in mind all the images are in separate sub-folders.

but just a simple rename will do the trick

thx

---

### Post by Lampi on 2011-11-30
wow... first things first :)

Can you confirm this does print all the files you need and list them in this pattern:

parentdirectory/some more path/001.jpg
parentdirectory/some other path/002.jpg

and so on ...

you'll have to replace parentdirectory="/home/my images/" with your actual path to your files

```

#!/bin/bash

loopcounter=1
parentdirectory="/home/my images/"

for file in `find $parentdirectory -type f -name "001.jpg"`
do
echo "${file/1.jpg/}"$loopcounter.jpg
loopcounter=$[loopcounter+1]
done
```

if this works you can try what else is possible with naming the target file after it's previous path and stuff...

---

### Post by vangop on 2011-11-30
So if you don't care about the final names, use the following:
```
% find <find dir path> -iname '*.jpg' -print0| xargs -0 -i cp "{}" <destination_dir_path>$(date +%s).jpg
```

<find dir path> - the root folder under which you have all your other folders with images
<destination_dir_path> - where you want all the copies stored

---

### Post by Lampi on 2011-11-30
Maybe this works?
```

#!/bin/bash

parentdirectory="/home/my images/"
targetdirectory="/home/my new images/"

for file in `find $parentdirectory -type f -name "001.jpg"`
do
newfilename=`echo $file | tr / _`
echo "path 2 newfile=[$targetdirectory$newfilename]"
#cp -vi "$file" "$targetdirectory$newfilename"
done

```

if the path 2 newfile echo makes sense you can uncomment the cp line additionally, I'm not sure it's a 100% right, that's why you get cp -vi which will ask before overwrite anything...

---

### Post by sohlinux on 2011-11-30
> **Lampi said:**
> wow... first things first :)

Can you confirm this does print all the files you need and list them in this pattern:

parentdirectory/some more path/001.jpg
parentdirectory/some other path/002.jpg

and so on ...

you'll have to replace parentdirectory="/home/my images/" with your actual path to your files

```

#!/bin/bash

loopcounter=1
parentdirectory="/home/u9/Pictures/all"

for file in `find $parentdirectory -type f -name "001.jpg"`
do
echo "${file/1.jpg/}"$loopcounter.jpg
loopcounter=$[loopcounter+1]
done
```

if this works you can try what else is possible with naming the target file after it's previous path and stuff...


thanks for the info

all I got was the following output but it did not create any new files

/home/u9/Pictures/all/003a/003/001.jpg
/home/u9/Pictures/all/002a/002/002.jpg
/home/u9/Pictures/all/001a/001/003.jpg


my images are located in /home/u9/Pictures/all/

inside all directory is the following

/home/u9/Pictures/all/tom/jannahouse/001.jpg
/home/u9/Pictures/all/****/minnie/001.jpg
/home/u9/Pictures/all/harry/london/001.jpg
/home/u9/Pictures/all/mary/birthday/001.jpg
/home/u9/Pictures/all/jane/holiday/001.jpg

300 directories in all


I cannot see in your code where is the output directory?
thanks

---

### Post by Lampi on 2011-11-30
yeah, try the next example - this will truncate your path, and replace it with underlines.

Bear in mind this is difficult to run tests without your specific path structure at hand, som I'm taking baby steps here to not mess up your files ;)

---

### Post by sohlinux on 2011-11-30
> **Lampi said:**
> yeah, try the next example - this will truncate your path, and replace it with underlines.

Bear in mind this is difficult to run tests without your specific path structure at hand, som I'm taking baby steps here to not mess up your files ;)


thanks for the info, but it just asks if I want to rename the files now

path 2 newfile=[/home/u9/Pictures/all/new_home_u9_Pictures_all_003a_003_001.jpg]
cp: overwrite `/home/u9/Pictures/all/new_home_u9_Pictures_all_003a_003_001.jpg'? 
path 2 newfile=[/home/u9/Pictures/all/new_home_u9_Pictures_all_002a_002_001.jpg]
cp: overwrite `/home/u9/Pictures/all/new_home_u9_Pictures_all_002a_002_001.jpg'? 
path 2 newfile=[/home/u9/Pictures/all/new_home_u9_Pictures_all_001a_001_001.jpg]
cp: overwrite `/home/u9/Pictures/all/new_home_u9_Pictures_all_001a_001_001.jpg'? 
u9@u9:~/Pictures$

---

### Post by sohlinux on 2011-11-30
it works!! I missed out a slash on the ouput path and didnt notice the new files!!


thanks
guys

---

### Post by Lampi on 2011-11-30
okay then, glad to help :)

---

### Post by sohlinux on 2011-11-30
> **vangop said:**
> So if you don't care about the final names, use the following:
```
% find <find dir path> -iname '*.jpg' -print0| xargs -0 -i cp "{}" <destination_dir_path>$(date +%s).jpg
```

<find dir path> - the root folder under which you have all your other folders with images
<destination_dir_path> - where you want all the copies stored

thanks for that too!!

---

