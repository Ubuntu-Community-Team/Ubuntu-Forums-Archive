---
title: "Search for a string in millions of files"
date: 2012-09-03
forum: General Help
---

### Post by ELMIT on 2012-09-03
I lost a harddisk a while back and recovered it. However, millions of files are "randomely" placed into thousands of directories.

I am looking for some files, and I do know what string is in it. 

A simple grep string */* does not work, since the list of arguments will be too long.

How can I find the file containg the string? There is only one level directories and within are all files. Or is there a program available that I can use.

---

### Post by MG&amp;TL on 2012-09-03
*find* and bash's for-loop are your friend. Assuming /lost is the directory with the files in it:

```
for files in $(find /lost); do grep "string" $files /dev/null*; *done
```

*for files in $(find /lost)* - go over every file in /lost

*do grep "string" $files /dev/null* - normally, grep will only show a hit, not which file it came from. Giving it two file arguments allows it to say which one. Since /dev/null is blank, you'll only get results from $files.

---

### Post by ELMIT on 2012-09-03
The script is now running for a while, but I wonder if it really works this time:

> ronald@ronald-Desktop:~$ for files in $(find 1T5recovery/*); do grep "BATCH_SIZE" $files /dev/null; done

Just to make sure what this does:
It uses all directories (1 level) under the ~/1T5recovery 
It seaches for the string, and if not founded it goes to the next.

What does it do when it found it? I need to know the file name ;-)
It seems to me it will only stop, letting me still guess which file it is ;-(

---

### Post by MG&amp;TL on 2012-09-03
> **ELMIT said:**
> The script is now running for a while, but I wonder if it really works this time:



Just to make sure what this does:
It uses all directories (1 level) under the ~/1T5recovery 
It seaches for the string, and if not founded it goes to the next.

What does it do when it found it? I need to know the file name ;-)
It seems to me it will only stop, letting me still guess which file it is ;-(

Okay, that was weird. Ignore this.

---

### Post by MG&amp;TL on 2012-09-03
> **ELMIT said:**
> The script is now running for a while, but I wonder if it really works this time:



Just to make sure what this does:
It uses all directories (1 level) under the ~/1T5recovery 
It seaches for the string, and if not founded it goes to the next.

What does it do when it found it? I need to know the file name ;-)
It seems to me it will only stop, letting me still guess which file it is ;-(

Yup, it will:

1. Go over every file in that tree.

2. Grep every file for "string". 

3. If it finds something, it will print the line, and the filename it found it in.

4. When done, it will exit.

You need to remove the * from the end of your filename. *find  *does that for you, you're just making it only read the directories in that file.

If you've got a tree, and you only want the toplevel, use:

```
for files in /lost/*; do grep "string" $files /dev/null*; *done
```

---

### Post by ELMIT on 2012-09-03
Thank you so much, .. you saved me a lots of time (to figure out some configurations files)

---

### Post by ELMIT on 2012-09-04
I still need an improvement to that script ;-)

The string is too often in the files I am looking for. So I can only see now the last file the string was included.

Can we change the script so, that the file name will be stored into a log file? 


----

I need to copy the script and change here more:

While I was doing the search I found that many files I do not need anymore. To be save I would like to move these files with a certain string into a new directory with the file name <directory>-<filename>
then I can go one more time through these files and just delete them all. I know that I have about 49 GB of such files !!!! (It was an unsuccessfully web crawling test, that retrieved their database as single web pages, ...)

---

### Post by drdos2006 on 2012-09-04
Yes you can output to a log file.

for files in /lost/*; do grep "string" $files /dev/null; done

for files in /lost/*; do grep "string" $files >> logfile.txt; done

regards

---

### Post by steeldriver on 2012-09-04
I think a nice general way to do something like this over multiple directories would be

```
while read -d $'\0' file; do echo do something with "$file"; done < <(find . -type f -exec grep -lsIZ 'yourtext' {} \;)
```Note that grep has the following options 

-l : print the filename instead of the default matching string
-s : suppress error messages (unreadable files and so on)
-I : ignore binary files (just in case there are any - you may not need this)
-Z : separate the outputs by the null character instead of space (prevents word splitting in the while loop)

You can do anything you like with $file once you find it - move, delete, rename, save to log

---

### Post by MG&amp;TL on 2012-09-05
> **ELMIT said:**
> I still need an improvement to that script ;-)

The string is too often in the files I am looking for. So I can only see now the last file the string was included.

Can we change the script so, that the file name will be stored into a log file? 


----

I need to copy the script and change here more:

While I was doing the search I found that many files I do not need anymore. To be save I would like to move these files with a certain string into a new directory with the file name <directory>-<filename>
then I can go one more time through these files and just delete them all. I know that I have about 49 GB of such files !!!! (It was an unsuccessfully web crawling test, that retrieved their database as single web pages, ...)

First request:

```
for files in /lost/*; do grep "string" $files /dev/null >> results.txt*; *done
```Second one might be a bit more complicated.
If there's important stuff in there, I suggest using cp instead of mv to start with.

```
for files in /lost/*; do grep -ls "string" $files | tr '/' '-' | awk '{print "/new/location/"$0}' | xargs mv $files &> /dev/null; done
```This is ugly, but I think it works. I'd appreciate it if someone else could check this for me before the OP uses it.

*for files in /lost/*  *--go over all files in /lost/

*do grep -ls "string" $files  *--print all the files that match "string"

*tr '/' '-''* --change any "/" to "-".

awk '{print "/new/location/"$0}'--tack the /new/location onto the front of our new filename.

*xargs mv $files  *move the file (use cp if unsure!) to our filename we've made.

*&> /dev/null  *--so we don't get a lot of errors from non-matching files.

---

### Post by dragonfly41 on 2012-09-05
Just to add a few tools which might help ..

see post #5 here ..

[http://ubuntuforums.org/showthread.php?t=1933990&highlight=textstat](http://ubuntuforums.org/showthread.php?t=1933990&highlight=textstat)

---

