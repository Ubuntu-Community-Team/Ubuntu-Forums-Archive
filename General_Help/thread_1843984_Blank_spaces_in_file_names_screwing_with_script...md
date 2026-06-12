---
title: "Blank spaces in file names screwing with script.."
date: 2011-09-14
forum: General Help
---

### Post by zero2xiii on 2011-09-14
Hay all,

I have a simple problem, and I hope there is a simple cure.

When I use variables in my scripts that contain file paths/names, spaces break the script. Lets say for example I want to exec this:

```
cp $file $file.bak
```

and $file=/home/user/some file.txt

It creates an error. How can the paths be made to be EXACT with the use of something like qoute marks? The code I need to get working looks like this:

```

        file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
	times="3"
					
	while [ $times -gt 0 ]
	do 
	sed -f algo_en.txt <$file > temp.enc
	mv temp.enc $file
		times=$(($times - 1))
	done

```

so when the $file is qouted in the sed line, no file changes are made to the original file, executing this in a terminal gives a file does not exist error, or to many arguments, if the name has more than one part (some part of a name.txt for example)


edit: Oh yea, when the file name has no space, the script works. So it is defenitly a space breaking it..

Thanks in advance
Cherz.

PS -- This bash thing is bashing my head (pun intended) :lolflag:

---

### Post by ofnuts on 2011-09-14
Using quotes is the right solution in most cases.

```

# this won't work because "<" is seen as part of the file name
cat "<$f"

# this will work
cat <"$f"
# or 
cat < "$f"

```There is a "[**Programming Talk**]("http://ubuntuforums.org/forumdisplay.php?f=39")" section on Ubuntuforums ( [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) ). Future bash questions are best addressed there.

---

### Post by nothingspecial on 2011-09-14
Hi, 

Read this guide to bash pitfalls

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Yours was number 2 :D

---

### Post by zero2xiii on 2011-09-14
> There is a "Programming Talk" section on Ubuntuforums ( [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39) ). Future bash questions are best addressed there.
Thanks, I was unaware of that. Will post future questions there.

> Hi, 

Read this guide to bash pitfalls

[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

Yours was number 2 

I have read that, but thanks for referencing it again. However, that doesn't work:

```
#!/bin/bash	
		
	##Set variables
	file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
	times="3"
					
	while [ $times -gt 0 ]
	do 

	sed -f algo_en.txt < "$file" > temp.enc
	mv temp.enc "$file"
		times=$(($times - 1))
	done
```

Does nothing to the file. However, if I run the same script in a terminal as:

```
#!/bin/bash	
		
	##Set variables
	read file
	##file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
	times="3"
					
	while [ $times -gt 0 ]
	do 

	sed -f algo_en.txt < "$file" > temp.enc
	mv temp.enc "$file"
		times=$(($times - 1))
	done

```

and copy and paste the path to the file (with and without white spaces) both of the files are changed correctly. It seems that there is something strange about the way the 

```
file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```

variable is set? I have notice this in the mean time:

> NAUTILUS_SCRIPT_SELECTED_FILE_PATHS: newline-delimited paths for selected files (only if local)

Could the "newline-delimited paths" cause this issue? the newline-delimitation???

Thanks for the help guys/gals (lolz... )

---

### Post by ofnuts on 2011-09-14
> **zero2xiii said:**
> Thanks, I was unaware of that. Will post future questions there.



I have read that, but thanks for referencing it again. However, that doesn't work:

```
#!/bin/bash    
        
    ##Set variables
    file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
    times="3"
                    
    while [ $times -gt 0 ]
    do 

    sed -f algo_en.txt < "$file" > temp.enc
    mv temp.enc "$file"
        times=$(($times - 1))
    done
```Does nothing to the file. However, if I run the same script in a terminal as:

```
#!/bin/bash    
        
    ##Set variables
    read file
    ##file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
    times="3"
                    
    while [ $times -gt 0 ]
    do 

    sed -f algo_en.txt < "$file" > temp.enc
    mv temp.enc "$file"
        times=$(($times - 1))
    done

```and copy and paste the path to the file (with and without white spaces) both of the files are changed correctly. It seems that there is something strange about the way the 

```
file="$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"
```variable is set? I have notice this in the mean time:



Could the "newline-delimited paths" cause this issue? the newline-delimitation???

Thanks for the help guys/gals (lolz... )
If $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS contains several files it won't work. If you want to process several files with on a single sed call, do not use input redirection but list the files as arguments to sed. 

Transforming file names from a string into sed parameters is a good job for xargs. xargs can be told to use \0 as a delimiter instead of space, so if you original string contains filenames with spaces separated by newlines characters you would use something like:

```

echo $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS | tr '\n' '\0' | xargs -0 sed -f algo_en.txt >temp.enc

```

(actual syntax to be checked...)

---

### Post by zero2xiii on 2011-09-15
> If $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS contains several files it won't work. If you want to process several files with on a single sed call, do not use input redirection but list the files as arguments to sed.

Yea true, but you are missing the problem. The script DOES NOT WORK, even for a single file when called from the nautilus script menu when the filename contains spaces.

The script is a simple file encryption routine. I wont ever use it one more than one file at a time. But not even that works, IF the filename contains white spaces... 

But thanks for the recommendation...

---

