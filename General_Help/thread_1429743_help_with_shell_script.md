---
title: "help with shell script"
date: 2010-03-14
forum: General Help
---

### Post by ryanf4321 on 2010-03-14
hi, i'm trying to write a shell script that can notify my of files in my home directory that are old, so i can look into deleting them. I want the files to be printed each on their own line.

I'm not sure what way I should go about doing that, should I use grep to find the date and compare that with todays date?

any suggestions are appreciated

---

### Post by ryanf4321 on 2010-03-14
update, so far this somewhat works.

[COLOR="DarkOrange"]d=`ls /home`

for date in `ls -l /home | cut -c 46-47`
do
        if [ $date -lt 11 ]
        then
                echo Maybe you should delete /home/$d
        fi
done
[/COLOR]

but i need it to print just the name of the directory that is less than 11, not all of them.

---

### Post by slakkie on 2010-03-14
find $HOME -mtime +31 -print

print all files, which haven't been modified in the last 31 days (or more).

---

### Post by ryanf4321 on 2010-03-14
thanks for the quick reply. that seems alot simpler than what I had, but I basically just need to find the date on each directory in home and if thats older than a month or so, to print that. Like say I have 8 or 9 folders in my home directory, I just need to it to notify if any of those are older than a certain date.

---

### Post by nemilar on 2010-03-14
You can modify that find command to only show directories with -type.

```
 find $HOME -mtime +30 -type d -print
```

Which is: 
find in $HOME everything that has a modified time of 30 days ago or greater, that is a directory.

---

### Post by ryanf4321 on 2010-03-14
hmm..that still isn't quite what i need or maybe i just don't understand. your suggestion gives me tons of directories, i only need the ones that aren't hidden and specifically the 4 or 5 users home directories ( ls /home).

this works for me so far in printing those directories that are older than the 11th of march:

directory=`ls /home`

for date in `ls -l /home | cut -c 46-47`

do
        if [ $date -lt 11 ]
        then
                echo Maybe you should delete /home/$directory
        fi
done


The only thing i can't figure out is how to echo the names of those specific directories that are found in the 'date' variable. right now its only printing everything in 'ls /home '

---

### Post by nemilar on 2010-03-14
That's because the find command will give you subdirectores.

If you want to use your script, I would suggest perhaps moving the cut to the test statement, which would leave the original line unmodified.

---

### Post by ryanf4321 on 2010-03-14
how would i put the cut command into the if [  ] though? i'm trying and getting errors

---

