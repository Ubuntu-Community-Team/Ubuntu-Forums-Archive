---
title: "Need help turning a command into a script..."
date: 2012-02-07
forum: General Help
---

### Post by x-shaney-x on 2012-02-07
I have a command I found somewhere for converting .MTS files from my camcorder into .MP4.
What I would ideally like is to turn this command into a script I can place into /usr/local/bin or something that I could use for converting future vids the same way.

Ideally I would then just open a terminal and type the scriptname followed by the filename?

The command in question is: ```
 ffmpeg -i 00001.MTS -f mp4 -vcodec copy -acodec copy 00001.mp4
```

---

### Post by cortman on 2012-02-07
```
#!/bin/bash

mts=$1
mp4=$2

ffmpeg -i $mts -f mp4 -vcodec copy -acodec copy $mp4.mp4
```

With this you'd need to run the command and the filename of the .mts and the new filename as well. Your command would be

```
foo my_vid.mts my_vid
```

Make the script executable by running

```
chmod +x foo
```

and then copy it to /bin-

```
sudo cp foo /bin
```

Let me know if this works.

EDIT: Alternately, try this-

```
#!/bin/bash

mts=$1

ffmpeg -i $mts -f mp4 -vcodec copy -acodec copy -y 
```

With this, hopefully all you need to run is

```
foo my_vid.mts
```

and it'll name the new video the same name as the old. I don't know enough about ffmpeg to say if this -y tag will work or not, but give it a try (on a test video). Ffmpeg is a pretty amazing program, I'm finding out- the man pages are almost like a Gilgamesh epic (some 50 pages).

---

### Post by x-shaney-x on 2012-02-08
I couldn't get the second example to work for some reason, though I haven't had time to look into the reason why.

The first one works fine and does just what I want though.
Many thanks :)

---

### Post by pixiq on 2012-02-08
Have a look at my thread, where I try to get efficient compression and suitable frame size, frame rate and bit rate to display video from my MTS files.

[http://ubuntuforums.org/showthread.php?t=1920371](http://ubuntuforums.org/showthread.php?t=1920371)

I use it as a batch job to convert all MTS files in the current directory. And as you see I am right now trying to make it more efficient. According to the advice, I should use the newest version of ffmpeg (instead of the one from the repos) and adjust the scripts to that, but I have not had the time to make all that work yet. (It works as it is in the first post, but slowly.)

Reuse part of my code if you wish :smile: For example, you can use the construct
```
"${1/.MTS}.mp4"
```to get the extension mp4 when your original file has the extension MTS
so if "$1", the first parameter is 00012.MTS it makes your output file become 00012.mp4

---

### Post by cortman on 2012-02-08
> **pixiq said:**
> Have a look at my thread, where I try to get efficient compression and suitable frame size, frame rate and bit rate to display video from my MTS files.

[http://ubuntuforums.org/showthread.php?t=1920371](http://ubuntuforums.org/showthread.php?t=1920371)

I use it as a batch job to convert all MTS files in the current directory. And as you see I am right now trying to make it more efficient. According to the advice, I should use the newest version of ffmpeg (instead of the one from the repos) and adjust the scripts to that, but I have not had the time to make all that work yet. (It works as it is in the first post, but slowly.)

Reuse part of my code if you wish :smile: For example, you can use the construct
```
"${1/.MTS}.mp4"
```to get the extension mp4 when your original file has the extension MTS
so if "$1", the first parameter is 00012.MTS it makes your output file become 00012.mp4

Nice. So how does the forward slash and curly brackets work as far as negating the extension?

---

### Post by pixiq on 2012-02-08
> **cortman said:**
> Nice. So how does the forward slash and curly brackets work as far as negating the extension?
This works in ***bash***
You find an explanation in ```
man bash
``````
       ${parameter/pattern/string}
              Pattern substitution.  The pattern is expanded to produce a pat&#8208;
              tern  just  as in pathname expansion.  Parameter is expanded and
              the longest match of pattern against its value is replaced  with
              string.   If  pattern  begins with /, all matches of pattern are
              replaced  with  string.   Normally  only  the  first  match   is
              replaced.  If pattern begins with #, it must match at the begin&#8208;
              ning of the expanded value of parameter.  If pattern begins with
              %,  it must match at the end of the expanded value of parameter.
              If string is null, matches of pattern are deleted and the / fol&#8208;
              lowing pattern may be omitted.  If parameter is @ or *, the sub&#8208;
              stitution operation is applied to each positional  parameter  in
              turn,  and the expansion is the resultant list.  If parameter is
              an array variable subscripted with  @  or  *,  the  substitution
              operation  is  applied  to each member of the array in turn, and
              the expansion is the resultant list.

```

---

### Post by cortman on 2012-02-08
Thanks!

---

