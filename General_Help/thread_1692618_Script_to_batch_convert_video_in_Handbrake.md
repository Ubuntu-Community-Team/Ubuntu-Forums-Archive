---
title: "Script to batch convert video in Handbrake"
date: 2011-02-21
forum: General Help
---

### Post by AsmodeusRimmon on 2011-02-21
I've looked everywhere I could but I must be blind.

I have Ubuntu 10.04 Server and I'm trying to batch convert .avi to .m4v in folders and subfolders. I can't seem to find a script to do that. Can anyone help me?

Thanks

---

### Post by down_to_earth_sort_of_guy on 2011-02-26
Here you go...

[http://hints.macworld.com/article.php?story=2006111622030031](http://hints.macworld.com/article.php?story=2006111622030031)

---

### Post by charithjperera on 2011-12-30
Here is a possibly useful shell script. The default settings are for cheap anime that can be encoded into 40mb quite easily, just change that stuff as you'd desire.

```
#!/bin/bash
#Handbrake batch script to recursively encode every file in a certain directory
FILES=/media/path/to/input/files/*/*
for f in $FILES
do
  #f is the input file names, this line replaces all avi's (input) with mkv's (output)
  g=${f/avi/mkv}
  

  echo "Processing ${f} file..."

  # Edit this line with the various parameters you want to use. See https://trac.handbrake.fr/wiki/CLIGuide
  HandBrakeCLI -C 2 -i "${f}" -o "${g}" -e x264 -S 40 -2 -T -E AC3 -B 64 -5 -8 strong

done
```

---

### Post by Juvencio on 2012-07-16
make sure all your video files are in the current folder.
No sub-folders will be scanned.

1. Run Handbrake

2. Select the Source folder and let Handbrake scan.
   May take a while depending on the amount of files.
   When done you will see your files under Title:

3. now you will see on top (File Queue View Help)
   under Queue select Add All  Queue.

Hope this helps some one.

ps. you can also setup to your preferd settings

Way to sort a folder full of video files into seperate folders [http://ubuntuforums.org/showthread.php?t=1709484]("http://ubuntuforums.org/showthread.php?t=1709484")

---

### Post by Cowboybebop79 on 2012-07-17
> **Juvencio said:**
> make sure all your video files are in the current folder.
No sub-folders will be scanned.

1. Run Handbrake

2. Select the Source folder and let Handbrake scan.
   May take a while depending on the amount of files.
   When done you will see your files under Title:

3. now you will see on top (File Queue View Help)
   under Queue select Add All  Queue.

Hope this helps some one.

ps. you can also setup to your preferd settings

Way to sort a folder full of video files into seperate folders [http://ubuntuforums.org/showthread.php?t=1709484]("http://ubuntuforums.org/showthread.php?t=1709484")

That just saved hours of work =D> Probably worth a beer at least ;)

---

### Post by tinmanjim on 2013-05-27
> **Juvencio said:**
> make sure all your video files are in the current folder.
No sub-folders will be scanned.

1. Run Handbrake

2. Select the Source folder and let Handbrake scan.
   May take a while depending on the amount of files.
   When done you will see your files under Title:

3. now you will see on top (File Queue View Help)
   under Queue select Add All  Queue.

Hope this helps some one.

ps. you can also setup to your preferd settings

Way to sort a folder full of video files into seperate folders [http://ubuntuforums.org/showthread.php?t=1709484]("http://ubuntuforums.org/showthread.php?t=1709484")

Ubuntu 12.04 running Handbrake 0.9.9 - I can't find any option to "add all to queue" anywhere. Was that feature removed from this version?

---

### Post by AleveSicofante on 2013-06-08
> **tinmanjim said:**
> Ubuntu 12.04 running Handbrake 0.9.9 - I can't find any option to "add all to queue" anywhere. Was that feature removed from this version?

You'll find it on the global menu (see attached picture).

(If you hate the fact that the global menu is hidden, please subscribe this bug and let your voice be heard: [https://bugs.launchpad.net/unity/+bug/682788](https://bugs.launchpad.net/unity/+bug/682788))


[ATTACH=CONFIG]243653[/ATTACH]

---

### Post by Arjunanda on 2014-03-28
I just could not figure out how this thing works, and had to manually add over 200 videos one by one. 
It took ages. There must have been easier ways, but now they are in the queue, so done. But I would really aprreciate easier ways, and more intuitive user interface.

---

### Post by AleveSicofante on 2014-03-28
Didn't you see the picture I attached? Have you actually read this thread? It's all explained here. I agree a better UI wouldn't hurt, but the current one is not that impossible and definitely no need to add 200 videos manually...

---

### Post by ctgcwiqc on 2014-09-08
> **AleveSicofante said:**
> Didn't you see the picture I attached? Have you actually read this thread? It's all explained here. I agree a better UI wouldn't hurt, but the current one is not that impossible and definitely no need to add 200 videos manually...

I did as suggested but it keeps crashing with th 400+ videos I have in que.  I put 5 in que and will see how that goes.

---

