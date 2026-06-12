---
title: "Same Folder"
date: 2010-03-01
forum: General Help
---

### Post by CatchItBaby on 2010-03-01
How to move folder which have same name in subfolder

Path : /root/Documents/untitled_folder/**untitled_folder**/abc.txt

I want to move files from that folder how to do that

Output : /root/Documents/untitled_folder/abc.txt

through terminal any idea ? and plz suggest a way to do in all folder present in directory recursevely

how to check recursively in all folder's present in directory

./folder1/abc.txt
./folder1/[COLOR="Red"]folder1[/COLOR]/abc.txt
./folder2/[COLOR="red"]folder2[/COLOR]/folder2/bbc.txt
./folder3/[COLOR="red"]folder3[/COLOR]/folder3/folder3/my.txt
./folder4/[COLOR="red"]folder4[/COLOR]/folder4/folder4/folder4/bcz.txt
./folder5/[COLOR="red"]folder5[/COLOR]/ca.txt
./folder6/za.txt
**./folder7/folder8/ca.txr**

output should like this

./folder1/abc.txt
./folder1/abc.txt
./folder2/folder2/bbc.txt
./folder3/folder3/folder3/my.txt
./folder4/folder4/folder4/folder4/bcz.txt
./folder5/ca.txt
./folder6/za.txt
**./folder7/folder8/ca.txt** --> note in this case

i want that it will check only in folder and into int'z next folder only 

how to do recursevely ?

---

### Post by Arkitekt on 2010-03-01
Does it HAVE to be done in terminal? if not then I suggest using 'gksudo nautilus' and doing it via GUI

---

### Post by CatchItBaby on 2010-03-01
Yes , i need to do with terminal

---

### Post by lidex on 2010-03-01
```
mv -i * /root/Documents/untitled_folder/untitled_folder/ /root/Documents/untitled_folder/
```

Try that one.

---

### Post by CatchItBaby on 2010-03-01
how to check recursively in all folder's present in directory

./folder1/[COLOR="Red"]folder1[/COLOR]/abc.txt
./folder2/[COLOR="red"]folder2[/COLOR]/folder2/bbc.txt
./folder3/my.txt
./folder4/[COLOR="red"]folder4[/COLOR]/folder4/bcz.txt

output should like this

./folder1/abc.txt
**./folder2/folder2/bbc.txt** : note that in this case 
./folder3/my.txt
./folder4/folder4/bcz.txt

i want that it will check only in folder and into int'z next folder only 

how to do recursevely ?

---

### Post by guren on 2010-03-01
Just to get you started, save this script on **/root/Documents/untitled_folder/** as fix_duplicates.sh then **chmod 755 fix_duplicates.sh** then run it **./fix_duplicates.sh**.
It should copy **/root/Documents/untitled_folder/untitled_folder/abc.txt**
to **/root/Documents/untitled_folder/abc.txt**

```

#!/bin/bash

PWDIR=$(pwd);
PWDIR_LENGTH=${#PWDIR}

SLASH_COUNT=0
for ((x=0; x<=$PWDIR_LENGTH; x++))
do
	if [[ ${PWDIR:x:1} = "/" ]]
	then
		let SLASH_COUNT=SLASH_COUNT+1
	fi
done

SLASH_COUNT2=0
for ((x=0; x<=$PWDIR_LENGTH; x++))
do
	if [[ ${PWDIR:x:1} = "/" ]]
	then
		let SLASH_COUNT2=SLASH_COUNT2+1
		
		if [[ $SLASH_COUNT -eq $SLASH_COUNT2 ]]
		then
			let PWFOLDER_POS=x+1;
		fi
	fi
done

PWFOLDER=${PWDIR:PWFOLDER_POS}
FILE_LIST=$(ls);

for next_file in $FILE_LIST; do
	if [[ $next_file = $PWFOLDER ]]
	then
		mv $next_file/* $PWDIR
	fi
done

```

For the recursion part, hmm.. lemme try to modify this part
```

PWFOLDER=${PWDIR:PWFOLDER_POS}
FILE_LIST=$(ls);

for next_file in $FILE_LIST; do
	if [[ $next_file = $PWFOLDER ]]
	then
		mv $next_file/* $PWDIR
	fi
done

```

You might want to try it as well.. something like
cd $next_file until there's no more $next_file to cd to
then mv * .. for each count that it cd $next_file :popcorn:

---

### Post by guren on 2010-03-02
Okay, here it is.
For the recursion part, you just need to **find . -name untitled_folder -type d**
This will find all folders with the same name then move all file contents from that folder to the first untitled_folder

```

#!/bin/bash

PWDIR=$(pwd);
PWDIR_LENGTH=${#PWDIR}

SLASH_COUNT=0
for ((x=0; x<=$PWDIR_LENGTH; x++))
do
	if [[ ${PWDIR:x:1} = "/" ]]
	then
		let SLASH_COUNT=SLASH_COUNT+1
	fi
done

SLASH_COUNT2=0
for ((x=0; x<=$PWDIR_LENGTH; x++))
do
	if [[ ${PWDIR:x:1} = "/" ]]
	then
		let SLASH_COUNT2=SLASH_COUNT2+1
		
		if [[ $SLASH_COUNT -eq $SLASH_COUNT2 ]]
		then
			let PWFOLDER_POS=x+1
		fi
	fi
done

PWFOLDER=${PWDIR:PWFOLDER_POS}

FILE_LIST=$(ls)
for next_file in $FILE_LIST; do
	if [[ $next_file = $PWFOLDER ]]
	then
		FOLDERS=$(find . -name $next_file -type d)
		for next_folder in $FOLDERS; do
			mv $next_folder/* . 2>/dev/null
		done
	fi
done

```

If you want to use this for each folder1 to folder 7, you have to **cd folder_name** then execute the script. Reason is my script needs to know that "current working folder" is the duplicated folder.

---

### Post by geirha on 2010-03-02
Maybe something like this:
```

find . -type f -exec prename -n 's,/([^/]+)/\1/,/$1/,' {} +

```

Note that the -n means dry-run, so replace it with -v to have it actually rename.

It'll leave the inner dirs empty though. You can find all empty dirs and remove them with
```
find . -type d -empty -delete
```

---

### Post by guren on 2010-03-02
> **geirha said:**
> Maybe something like this:
```

find . -type f -exec prename -n 's,/([^/]+)/\1/,/$1/,' {} +

```

Note that the -n means dry-run, so replace it with -v to have it actually rename.

It'll leave the inner dirs empty though. You can find all empty dirs and remove them with
```
find . -type d -empty -delete
```

He transformed my 34 lines into 1 line. cool! i tried it and it works

---

### Post by CatchItBaby on 2010-03-02
Thankx :) :popcorn:

---

