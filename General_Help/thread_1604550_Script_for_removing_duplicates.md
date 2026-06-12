---
title: "Script for removing duplicates"
date: 2010-10-24
forum: General Help
---

### Post by anemon on 2010-10-24
Although having used Ubuntu for a good couple of years, I'm still a total beginner when it comes to scripting. However, what I need to do should be fairly straightforward:

Importing images from my digital camera, both RAW "originals" and JPG "copies" end up in the same folder. I typically flip through the JPG:s in Image Viewer and remove those that I'm not interested in. Now, this leaves me with the tedious job of going though all the RAW files in the folder manually to get rid of those too! It sure would be wonderful to get Ubuntu to do the work for me...

The script would simply need to go though all the RAW files in a folder one by one, check for a corresponding JPG file - and if there isn't one, remove the RAW file. How could I accomplish that?

Thankful for all help!

---

### Post by TeoBigusGeekus on 2010-10-24
```
for i in $(ls *.raw)
do
	fn=$(basename $i)
	n=${fn%.*}
	if [ ! -e $n.jpg ]
	then rm $n.raw
	fi
done
```

It won't work if the filenames have spaces though. In that case, use something like thunar's bulk rename to remove them.

---

### Post by anemon on 2010-10-25
Seems to work like a charm... Thanks a lot!

Just two additional questions: Where do I put the script to make it accessible from any folder? And is there a way to make it "case-insensitive", i.e. to make it find files named ".RAW" as well as ".raw"? (Well, except for the obvious solution to duplicate the entire loop and make it look for both... Not very elegant, though.)

---

### Post by TeoBigusGeekus on 2010-10-25
```
#!/bin/bash
for i in $(ls *.raw *.RAW)
do
	fn=$(basename $i)
	n=${fn%.*}
	if [ ! -e $n.jpg ]
	then rm $n.raw $n.RAW
	fi
done
```

Save it as check_dupl (for example)
Then 
```
chmod +x check_dupl
```
to make it executable and finally
```
sudo cp check_dupl /bin/
```
to have system wide access to it.

---

