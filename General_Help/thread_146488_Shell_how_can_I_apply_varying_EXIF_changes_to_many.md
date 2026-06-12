---
title: "Shell: how can I apply varying EXIF changes to many files at once?"
date: 2006-03-18
forum: General Help
---

### Post by SlugO on 2006-03-18
Okay, so I've got a bunch of JPG images with wrong EXIF dates from my friend's camera. I've been using jhead to correct them one by one like this:```
jhead -ts2006:01:16-18:44:00 img_1059.jpg
```Is there any better way? I've been trying to search from Google if I could change them all at once but haven't had any luck.

I basically want to do this: change EXIF dates of files img_{**1058-1101**} so that the first file has a certain time and date then each next file has the same time as the previous **+2** minutes. Gotta get them in order for F-spot... ;)

I do know how to use the command line and also some programming but I just can't figure out how to perform this with a single command :confused:

---

### Post by Quirky on 2006-03-18
Dates are a tricky one. I can't think of any good way to add minutes which wrap to hours, etc using just the command line. Try this bit of python, place it in a file and run it with *python <file>*. The time may be suspect to your current locale, so perhaps comment out the line with "commands.getoutput" to check it would do what you want first, before acutally commiting yourself to changing the dates:

```

import time, glob, commands

timestr='2006:01:16-18:44:00'
format='%Y:%m:%d-%H:%M:%S'
interval=2*60
pattern='*.jpg'

current_time=int(time.strftime('%s',time.strptime(timestr,format)))
for jpg in glob.glob(pattern):
  datestr=time.strftime(format, time.gmtime(current_time))
  cmd = 'jhead -ts'+datestr+' '+jpg
  print cmd
  output = commands.getoutput(cmd)
  print output
  current_time+=interval

```

---

### Post by drl on 2006-03-18
Hi, SlugO.

I don't know anything about jhead, but it looks like your problem is the kind that a shell loop could address.

It would go something like this:

```
#!/bin/sh

minutes=0
for file in *.jpg
do
  $minutes=`expr $minutes + 2`
  echo Command -- jhead -ts2006:01:16-18:$minutes:00 $file
done
```

You have 2 variables that are changed each time through the loop: the file name is taken care of by the "for" construct, and the minutes are done by "expression" function "expr".

So you'd enter this in a file, then ask the shell to run it -- an easy way might be: "sh ./s1", assuming you placed the commands in file "s1".

This will NOT do any real operations yet, because you'd want to look over the operations first.  Once you are satisfied it would work, you would remove the "echo Command --" characters, and you're good to go ... cheers, drl

PS I often work on a sample data set first, so you could copy a few of the  files to a scratch directory and the do the shell script there.

( edit 1: type )

---

### Post by drl on 2006-03-18
Hi.

Quirky has a good point.  My solution will *wrap* after 60 files.  To muck with the hours would add complexity.  You might be able to move and do 50 files at a time, especially if this is is a one-shot operation ... cheers, drl

---

### Post by Quirky on 2006-03-18
All this coding and I bet theres a jhead option like "-interval +2min" or something :)

---

