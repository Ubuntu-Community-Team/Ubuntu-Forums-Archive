---
title: "Automate creating directories based on file names and moving files into them"
date: 2011-04-30
forum: General Help
---

### Post by Abdus on 2011-04-30
I have a bunch of .7z files in a directory, and I need to put each one of them into a separate directory, named after the file (without extention). The command line I use:
```
find . -type f | mkdir `sed -e "s:..\(.*\)...:\1:"` ; ls | grep .7z | cp * `sed -e "s:\(.*\)...:.\/\1\/:"`
```
Copying fails though:
```
...
cp: omitting directory `./100205-FMC_6-30-TeX-only/'
cp: omitting directory `./100207-FMC_6-30/'
cp: omitting directory `./100207-FMC_6-30-TeX-only/'
cp: omitting directory `./100209-FMC_6-30/'
cp: omitting directory `./100209-FMC_6-30-TeX-only/'
cp: omitting directory `./100210-FMC_6-30/'
cp: omitting directory `./100210-FMC_6-30-TeX-only/'
...
```
What's wrong?

Any tips? Easier solutions? 

PS. I don't want to use scripts, I want to do it using simple commands and piping.

PS 2. I started this topic here, as I failed to find a "Me linux noob, me needs help" subforums.

---

### Post by erind on 2011-04-30
I'd do it a bit differently, something like:

```
find . -type f -name '*.7z' | 
 while read File
  do
     mkdir "${File%.*}"
     # mv "$File" "${File%.*}"
     cp -p "$File" "${File%.*}"
  done

```

---

### Post by Abdus on 2011-04-30
> **erind said:**
> I'd do it a bit differently, something like:

```
find . -type f -name '*.7z' | 
 while read File
  do
     mkdir "${File%.*}"
     # mv "$File" "${File%.*}"
     cp -p "$File" "${File%.*}"
  done

```

It works. Thank you very much. Spent 2 hours on it.

A question though: what is that thing you just showed me? What script language, I mean, or what should I read to learn using it (and actually understand your code)?

Thanks again.

---

### Post by erind on 2011-04-30
Welcome. That's just shell scripting, and here is a good guide on it:

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

The code is simple - a *'while'* loop reads each line that *'find'* command feeds to it.
*"${File%.*}"* removes .7z extension from each file, one at a time ( see 'Parameter Substitution' in the above link ). Then copy or move the file to their respective directory.

---

### Post by Abdus on 2011-04-30
Thank you. Problem solved, and I got a good opportunity to learn something useful.

---

### Post by Abdus on 2011-05-01
I found a command line (no scripts) solution to the problem, I thought I might share it. It may be not pretty, but it works. :)

```
find . -maxdepth 1 -type f -exec mkdir {}-DIR \; -exec mv {} {}-DIR \; ; find . -maxdepth 1 -type d -exec rename "s:\..{2,3}-DIR::" {} \;
```

What it does:
Find each file in this folder (not subfolders):
find . -maxdepth 1 -type f 

then execute mkdir that creates a folder for every file found, with '-DIR' added to its name:
-exec mkdir {}-DIR \;

then move each file to it scorresponding folder:
-exec mv {} {}-DIR \;

then end this command and start a new one:
;

then find each folder:
find . -maxdepth 1 -type d

then execute rename that will remove the '-DIR' part from the folder's name, as well as the original file extension (provided it was 2-3 letters/digits long and was preceeded by a dot).
-exec rename "s:\..{2,3}-DIR::" {} \;

Enjoy. :)

---

### Post by albertnet on 2012-06-15
> **Abdus said:**
> I found a command line (no scripts) solution to the problem, I thought I might share it. It may be not pretty, but it works. :)

```
find . -maxdepth 1 -type f -exec mkdir {}-DIR \; -exec mv {} {}-DIR \; ; find . -maxdepth 1 -type d -exec rename "s:\..{2,3}-DIR::" {} \;
```

What it does:
Find each file in this folder (not subfolders):
find . -maxdepth 1 -type f 

then execute mkdir that creates a folder for every file found, with '-DIR' added to its name:
-exec mkdir {}-DIR \;

then move each file to it scorresponding folder:
-exec mv {} {}-DIR \;

then end this command and start a new one:
;

then find each folder:
find . -maxdepth 1 -type d

then execute rename that will remove the '-DIR' part from the folder's name, as well as the original file extension (provided it was 2-3 letters/digits long and was preceeded by a dot).
-exec rename "s:\..{2,3}-DIR::" {} \;

Enjoy. :)

Abdus, what an amazing code!!! It works like a charm and took a lot of work off my shoulders, thank you!:guitar:

---

