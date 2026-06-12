---
title: "CREATE-&gt;COPY script"
date: 2010-02-22
forum: General Help
---

### Post by chiques on 2010-02-22
Hi Everyone, 

Are there any tutorials that anyone recommends that guides me on how to create a directory with a corresponding file name and copy that file into that newley created directory?

e.g.

File1.txt
File2.txt
File3.txt

File1.txt->File1/File1.txt

File2.txt->File2/File2.txt

File3.txt->File3/File3.txt

---

### Post by Kruptein on 2010-02-22
like with a bash script?
```
#!/bin/bash
read filename   #Now I use user input, but you can also use other inputs
mkdir ./$filename
cp ./$filename.txt ./$filename/
#if the original file should be deleted remove the # from the next line:
#rm ./$filename.txt
```

---

### Post by chiques on 2010-02-23
> **Kruptein said:**
> like with a bash script?
```
#!/bin/bash
read filename   #Now I use user input, but you can also use other inputs
mkdir ./$filename
cp ./$filename.txt ./$filename/
#if the original file should be deleted remove the # from the next line:
#rm ./$filename.txt
```




Yes, a bash script will do.


I tried to run the script you recommended in the same directory where my 3 files are kept but I received the following error. I apologize for my ignorance.

```

user@user-desktop:~/Desktop/scripts_test$ ./run.sh

mkdir: cannot create directory `./': File exists
cp: cannot stat `./.txt': No such file or directory
user@user-desktop:~/Desktop/scripts_test$ 

```


Here's what it looks like in Nautilus.

---

### Post by chiques on 2010-02-23
I get it now. I have to manually input each file name after I run the script. How can I have it automatically create a folder with the same name of each file without inputting the file name?

---

### Post by Lekensteyn on 2010-02-23
You mean by looping through the folders contents?

---

### Post by kaibob on 2010-02-23
The following should do what you want:

```
#!/bin/bash

cd /home/username/Desktop

for file in *.txt ; do
   mkdir "${file%.txt}"
   cp "$file" "${file%.txt}"
done
```

A few comments:

* You have to change username in the above shell script.

* Some people object to specifying a specific directory in a shell script. You can change that if it bothers you.

* Since you have not indicated otherwise, the new directories are created in the directory that contains the source files. Also, all files with a *.txt extension in the source directory are copied to newly created directories.

---

### Post by chiques on 2010-02-23
> **kaibob said:**
> The following should do what you want:

```
#!/bin/bash

cd /home/username/Desktop

for file in *.txt ; do
   mkdir "${file%.txt}"
   cp "$file" "${file%.txt}"
done
```

A few comments:

* You have to change username in the above shell script.

* Some people object to specifying a specific directory in a shell script. You can change that if it bothers you.

* Since you have not indicated otherwise, the new directories are created in the directory that contains the source files. Also, all files with a *.txt extension in the source directory are copied to newly created directories.



Excellent! This worked for what I asked. Thank you guys!

---

### Post by Kruptein on 2010-02-23
That's what I meant with the other kinds of input ^^

---

### Post by chiques on 2010-02-24
Out of curiosity, how would I append the name of the newly created folder?

e.g.

The name of my file is 

```
file1.txt

```

I would like to create a folder named:

```
file1_txt

```

I'm not sure what syntax I should reference to (C++, perl, etc...).

---

### Post by Kruptein on 2010-02-24
You can use the same script, you only have to change:
```
mkdir "${file%.txt}"
```
with
```
mkdir "${file%.txt}_txt"
```

---

### Post by chiques on 2010-02-24
Oh I see.

I was using 

```
mkdir "${file%.txt}"_txt"
```

Thanks!

---

