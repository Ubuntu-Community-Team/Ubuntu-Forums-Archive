---
title: "Script help please"
date: 2010-05-05
forum: General Help
---

### Post by wnaBsd8d on 2010-05-05
Hi,

i am writing a script for my ubuntu server and basically i want it to download a file that i specifically type in then take that file put it in a certain folder (note file may or may not be archived so i'd have to check for that) then add the name of that file to a text file

i know sounds strange but this is what i got so far:

```

#!/bin/bash
echo "-----Star of Script-----"
echo "Please enter URL:"
read URL
cd testdir
wget $URL
//extraction here + delete original archive (rar,zip,anything :S)
echo name_of_file >> list.txt
echo "-----End of Script-----"


```


if anyone could point me in the right direction that would be much appreciated ..

cheers

---

### Post by ironic.demise on 2010-05-05
This really isn't helping... but I would appreciate if you told me the purpose of 

"#!/bin/bash"
"wget"

A bit new to terminal and was very very comfortable with windows CMD...

I can only suggest that you might use google to find the terminal equivalent of 
"IF EXIST GOTO"

Use terminal to search through the list text file for the string that matches the name_of_file?
Then if you do find an IF EXIST GOTO does exist, just use it on that particular string?

(There probably is a way to IF a string instead of a file... or if your checking for archive you could IF EXIST the file in that directory)

The only other way I could help would be if you wined CMD... and that's so simple I'm sure you could write your own windows batch file for that... :( 

Apologies, New to the game

:edit:
grep searches for strings of text
Though I can't seem to see an IF function?

---

### Post by wnaBsd8d on 2010-05-05
> "#!/bin/bash"
"wget"

the purpose of that is firstly (from my limited knowledge of scripts) to define the this is infact a script (bin/bash) and secondly the wget allows you to download files ie wget [http://somesite.com/somefile.rar](http://somesite.com/somefile.rar)

thankyou for your suggestions i shall look into them further

hope this helps

---

### Post by sbergman on 2010-05-05
should line #8 not be:

echo $URL > list.txt

??

---

### Post by wnaBsd8d on 2010-05-05
Well what i want to be included in the list.txt is the name of the file

ie: 
i download a rar or some archive 
extract it
the file will be somename.jpg for instance
then i want to include "somename" into the list.txt not the url of where it came from

---

### Post by ironic.demise on 2010-05-05
> **wnaBsd8d said:**
> the purpose of that is firstly (from my limited knowledge of scripts) to define the this is infact a script (bin/bash) and secondly the wget allows you to download files ie wget [http://somesite.com/somefile.rar](http://somesite.com/somefile.rar)

thankyou for your suggestions i shall look into them further

hope this helps

much appreciated :)
hmmm
depending on where you download it to couldn't you just ls the directory?
So if it downloaded to downloads couldn't you just 
```
cd ~\downloads
ls -l > list_of_files
```

---

### Post by pytheas22 on 2010-05-05
> i download a rar or some archive
extract it
the file will be somename.jpg for instance
then i want to include "somename" into the list.txt not the url of where it came from

Do you have code that determines what "somename" is?  In the script you posted above, you echo name_of_file into a file, but name_of_file is not set to anything.

Also, it should be:
```

echo $name_of_file >> list.txt
```

(note the $) right?

---

