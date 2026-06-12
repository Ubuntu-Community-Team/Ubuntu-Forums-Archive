---
title: "More problems with bash scripting and spaces in directories"
date: 2009-08-19
forum: General Help
---

### Post by Pi72 on 2009-08-19
Hello people

Well, this is the task I want to do: I have a dir with lots of dirs in it, each dir has one file in it with an unrelated name. What I want to do is rename each one of those files as the folder containing it, plus an extra extension (.zip), and then move it to the parent dir and delete the original dir.

So, imagine we have these in out current directory:
crash/whatever.zip
cross/crlf.zip
warning/w.ico

After running the script, the current directory would contain none of the directories crash, cross and warning, but only these three files:
crash.zip
cross.zip
warning.zip

Note that I don't care that the ico file changed extension as zip. The script will only work with directories in the current level, as supposedly they will not have anything else in them except that one file.

The problem I have is changing to dirs which have spaces in them. As soon as one dir has one space, I can't change to it, and the script results go to hell. I've not reached yet the "rename and move" part since I can't make the "change into" one. The code looks like:

```
#!/bin/bash
for DIR in $(ls -d */)
do
  folder=$(echo $DIR|head -c -2)
  zip=$(echo ${folder}.zip)
  cd $folder
  ls
  cd ..
done 


```

I've tried quite a lot of combinations of adding quotes, to no avail. I guess I'll have the same problems renaming the file if the folder name contains spaces, but I don't have much experience with batch scripting (this is only my second "for" loop in one year!)

Could anyone help me complete this? Thanks in advance!

---

### Post by DaithiF on 2009-08-19
Hi,
when you do:
for DIR in $(ls -d */)
the results of ls are being split according to bash's IFS (internal field separator), which is any whitespace -- so that the DIR will contain partial directory names and therefore won't work correctly.  Nothing you do with quoting is going to get around that.

You could set the IFS to something else (e.g. a newline character), but I think an easier way is as follows:

find . -mindepth 1 -maxdepth 1 -type d | while read DIR
do
  zip="${DIR}.zip"
  cd "${DIR}"
  ls
  cd ..
done

---

### Post by Pi72 on 2009-08-19
I wasn't aware that the problem lied there. Your method is great, I avoided easily all those problems; plus it allowed me to correct a bug with the other script I made today.

So today I recreated one script which I had as batch file since MS-DOS 5.0 and I was still using it past year under XP!

Thank you very much for your advice!

---

### Post by asmoore82 on 2009-08-19
The absolute best way to handle filenames in Bash - although it may not always be possible -
is by forgoing external commands in favor of the shell's own abilities.

This can even handle the case of a filename with an actual newline in it -
which is not illegal in Unix-like systems...

```
for dirs in */
do
   echo "$dirs"
done
```

---

