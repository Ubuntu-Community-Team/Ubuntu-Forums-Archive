---
title: "Help with Shred shell script"
date: 2010-09-29
forum: General Help
---

### Post by twzg on 2010-09-29
Hi. I have made a shell script to shred files and folders. 

If the user points the filepath to a folder and within the folder there are subfolders, the user is given a choice to shred the immediate files in the folders leaving the subfolders intact or to shred everything including the contents of the subfolders.

Please help me to debug the script.

```

#! /bin/sh

echo "Enter file path:\c"
read filepath

echo "Enter number of overwrites: [recommended >= 10] \c"
read overwriteAmt

echo "Selected file/folder: $filepath"
echo "Num. of overwrites: $overwriteAmt"

if [ -f $filepath ]
	then
		"Selected is a file"
		status = "file"
elif [ -d $filepath ]
	then
		"Selected is a folder"
		status = "folder"

	## Ask if user wants to delete a child files and folders in the folder
	 echo "Do you want all the child files/folders be deleted ? [Y/N]: \c"
	 read deleteChildren
fi

if [ status == 'folder' && $deleteChildren == 'Y' ]
	then
		## delete all childrens in a loop
		for childfile in `dir -d *` ; do
			shred -u -z -n $overwriteAmt $childfile

elif [ status == 'folder' && deleteChildren == 'N' ]
	then
		## delete the immediate files in the folder
		for childfile in `dir -d *` ; do
			if [ -f childfile ]
				then
					shred -u -z -n $overwriteAmt $childfile
		
elif [ status == 'file']	
	then
		delete individual file
		shred -u -z -n $overwriteAmt $filepath
fi

done



```

Here's the error I got from the terminal when it is running...

```

Enter file path:/home/linux/Desktop/dummy
Enter number of overwrites: [recommended >= 10] 10
Selected file/folder: /home/linux/Desktop/dummy
Num. of overwrites: 10
Shredder.sh: 24: Selected is a folder: not found
status: Unknown job: =
Do you want all the child files/folders be deleted ? [Y/N]: Y
Shredder.sh: 32: Syntax error: "elif" unexpected (expecting "done")

```

Why is it getting this error ?

Thanks and regards,
twzg.

---

### Post by DaithiF on 2010-09-29
each for ... do ...  loop needs to be terminated with done.
```
for a in b
do
  # do stuff here
done

```

---

