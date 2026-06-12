---
title: "How to get list of directorys in a directory  as a list in a file"
date: 2009-07-11
forum: General Help
---

### Post by mrakesh85 on 2009-07-11
I have a directory that contains so many directories in it and each directory contains a number of files.

it is  
          directory1>directory11>files
                        >directory12>files
                        >directory12>files
                         .
                         .
                         . 
I want the list of directorys in directory1 in a text file is it possible to get in fedora

---

### Post by jerome1232 on 2009-07-11
Yup, this would create a text file called 'directory1-listing' containing the output of ls in your current working directory

```
ls directory1 > directory1-listing
```

---

### Post by mrakesh85 on 2009-07-11
Thank you very much I got it

---

### Post by naklinaam on 2009-07-11
> **jerome1232 said:**
> Yup, this would create a text file called 'directory1-listing' containing the output of ls in your current working directory

```
ls directory1 > directory1-listing
```

Wont this list all files and directories within directory1, with no indication which entry is a file and which a directory

Alternatively, you could also try:
```
ls -l directory1 | grep '^d' |cut -c52- > directory1-listing
```
here is what it does:
**ls -l **        lists the contents of the directory in the long form

**grep '^d'**     looks for rows starting with a d... '^' indicates begining of line. This command filters out anything that is not a directory

**cut -c52-**      'cuts' out the first 52 characters of the output since this has all the file size and date etc... not sure if you might have to play with the number 52 to get the exact starting point of the file names. Note that the hyphen at the end of the command after 52 is required otherwise you will get only the 1st letter of the directory name

lastly,
**>direcotry1-listing**      creates (or overwrites) a file directory-listing with the output of the previous commands. ofcourse you can replace'directory1-listing' with any file name you choose

---

### Post by The Cog on 2009-07-11
or 
> find directory1 -type d -maxdepth 1

---

### Post by naklinaam on 2009-07-11
> **The Cog said:**
> or

@The Cog:
Thanks... That is really cool and efficient. How can I remove the leading 'directory1\' (I could use cut, but I am sure you have a better way of doing it).
Basically I am extrapolating the current question to find an efficient way of parsing text listing out without using regular expressions. Dont want to usurp this thread though so its OK if this question is not answered on this thread. I will research that separately, unless it helps the original requester with his task.

---

### Post by mrakesh85 on 2009-07-11
Thank you very much for giving more information and elaborate explanation

---

### Post by The Cog on 2009-07-11
Hmm  - tricky. Perhaps:
```
find directory1 -type d -maxdepth 1 -exec basename '{}' \;
```
or 
```
for f in $(find directory1 -type d -maxdepth 1) ; do echo basename $f ; done 
```
or 
```
find directory1 -type d -maxdepth 1 | sed 's:.*/::g'
```
None of these have I actually tried.

---

### Post by unutbu on 2009-07-11
Perhaps

```

find directory1 -maxdepth 1 -mindepth 1 -type d -printf "%f\n"
```

---

### Post by The Cog on 2009-07-11
> **unutbu said:**
> Perhaps
```

find directory1 -maxdepth 1 -mindepth 1 -type d -printf "%f\n"
```

Sweet! I must remember that capability.

---

### Post by dsmithnc on 2009-08-12
I'd like to give this a try with directories on a DVD.  How do you identify the source in your example:

ls -l directory1 | grep '^d' |cut -c52- > directory1-listing

Thanks,

Dick

---

