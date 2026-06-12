---
title: "Shell scripting help... good deed for the aged?"
date: 2011-08-31
forum: General Help
---

### Post by macey on 2011-08-31
...please?
Hello, I have a very handy little bit of script that uses mplayer and oggenc to encode practically any audio file I have encountered into vorbis/ogg. Here it is:-

mkfifo $1.wav
if nice -n 10 oggenc --ignorelength -q 5 $1.wav -o $1.ogg & nice -n 10 mplayer $1.flac -vc null -vo null -nocache -ao pcm:fast:file=$1.wav && rm $1.wav

If I call this (within a folder of *flac files in this example) it will convert from *flac to *.ogg.

I want a little bit of code to add to this so that it can be called to convert ALL of the files in a folder. 

I know I could take the effort and dig into shell sripting/loops/variables etc but I did all of that years ago -- cobol/pascal/assembler/basic/c.. but I am now 61 and to be honest, I can't be arsed so please, please help a very old mainframe sysprog?? 
Go on, do a good deed for that day, only take some of you a few minutes. ](*,)

---

### Post by Habitual on 2011-08-31
are there any non-flac audio filetypes in a flac directory?

OldGuysRule!

---

### Post by macey on 2011-08-31
> **Habitual said:**
> are there any non-flac audio filetypes in a flac directory?

OldGuysRule!

No, there wont be...

---

### Post by sisco311 on 2011-08-31
```
#!/bin/bash

# exit if dirctory doesn't exist or can't be accessed
cd "$1" || exit 1

shopt -s nullglob
for f in *.flac
do
    # remove ext
    file="${f%.flac}"
    echo "${file}.wav" "${file}.ogg" "$f"
done
```?

---

### Post by macey on 2011-08-31
> **sisco311 said:**
> ```
#!/bin/bash

# exit if dirctory doesn't exist or can't be accessed
cd "$1" || exit 1

shopt -s nullglob
for f in *.flac
do
    # remove ext
    file="${f%.flac}"
    echo "${file}.wav" "${file}.ogg" "$f"
done
```?

Pardon my ignorance but, what exactly does this do?. I get the gist but what about the shopt -s nullglob? Shell options but what does setting nullglob do?

---

### Post by seawolf167 on 2011-08-31
What about using ffmpeg? That should be able to convert to ogg

```
#!/bin/bash
for file in *.flac
do 
newname="${file%.flac}"
ffmpeg -ab 320k -i "$file" "${newname}.ogg"
done
```

---

### Post by macey on 2011-08-31
> **seawolf167 said:**
> What about using ffmpeg? That should be able to convert to ogg

```
#!/bin/bash
for file in *.flac
do 
newname="${file%.flac}"
ffmpeg -ab 320k -i "$file" "${newname}.ogg"
done
```

Fair comment! But in my experience of ffmpeg -ab seems to have no effect on the bitrate, always seems to default to 120 (if my memory serves me well..

---

### Post by sisco311 on 2011-08-31
> **macey said:**
> Pardon my ignorance but, what exactly does this do?. I get the gist but what about the shopt -s nullglob? Shell options but what does setting nullglob do?

For each .flac file in the directory it prints the file name with different suffix (extension). The name of the directory must passed as an argument to the command. You may also want to add some extra checks, like:
```

# exit if $1 is not a dir
# run the scrip in the current working dir if no dir specified 
if [ "$1" ]
then
    cd "$1" || exit
fi

```

If no matching file names are found, and  the  shell  option nullglob  is not enabled, the word is left unchanged. So if you run the loop in a directory where are no .flac files, then the value of the f variable becomes *.flac and your command inside the loop will probably throw a *no such file or directory*  error.

If the nullglob option is set, and no matches are found, the word is  removed and the body of the for loop is not executed.

```

sisco@acme:~/xtmp$ mkdir -p foo
sisco@acme:~/xtmp$ cd foo/
[color=red]sisco@acme:~/xtmp/foo$ echo *.flac
*.flac[/color]
sisco@acme:~/xtmp/foo$ shopt -s nullglob 
[color=green]sisco@acme:~/xtmp/foo$ echo *.flac
 [/color]
sisco@acme:~/xtmp/foo$ shopt -u nullglob 
sisco@acme:~/xtmp/foo$ > 1.flac
sisco@acme:~/xtmp/foo$ echo *.flac
1.flac
sisco@acme:~/xtmp/foo$ shopt -s nullglob 
sisco@acme:~/xtmp/foo$ echo *.flac
1.flac

```

---

### Post by ron999 on 2011-08-31
> **macey said:**
> Fair comment! But in my experience of ffmpeg -ab seems to have no effect on the bitrate, always seems to default to 120 (if my memory serves me well..

Yes, because with Vorbis "**-aq**" is preferred.
Like this:-
```
ffmpeg -i "$file" -acodec libvorbis -aq 6 "${newname}.ogg"
```

The quality values are in a table here:- [http://en.wikipedia.org/wiki/Vorbis#Technical_details]("http://en.wikipedia.org/wiki/Vorbis#Technical_details")

---

### Post by seawolf167 on 2011-08-31
> **ron999 said:**
> Yes, because with Vorbis "**-aq**" is preferred.
Like this:-
```
ffmpeg -i "$file" -acodec libvorbis -aq 6 "${newname}.ogg"
```The quality values are in a table here:- [http://en.wikipedia.org/wiki/Vorbis#Technical_details](http://en.wikipedia.org/wiki/Vorbis#Technical_details)

Ahh, good to know, thanks ron999

---

### Post by macey on 2011-08-31
> **ron999 said:**
> Yes, because with Vorbis "**-aq**" is preferred.
Like this:-
```
ffmpeg -i "$file" -acodec libvorbis -aq 6 "${newname}.ogg"
```

The quality values are in a table here:- [http://en.wikipedia.org/wiki/Vorbis#Technical_details]("http://en.wikipedia.org/wiki/Vorbis#Technical_details")

Bloody great!

Can I do this from my home directory to convert all files within my home directory?:-

find -name *.flac |<your routine>

---

### Post by seawolf167 on 2011-08-31
Just replace my previous ffmpeg command with the new one from ron999 and your bash script will be ready to go and work in any directory.

```
#!/bin/bash
for file in *.flac
do 
newname="${file%.flac}"
ffmpeg -i "$file" -acodec libvorbis -aq 6 "${newname}.ogg"
done
```

---

### Post by macey on 2011-08-31
> **seawolf167 said:**
> Just replace my previous ffmpeg command with the new one from ron999 and your bash script will be ready to go and work in any directory.

```
#!/bin/bash
for file in *.flac
do 
newname="${file%.flac}"
ffmpeg -i "$file" -acodec libvorbis -aq 6 "${newname}.ogg"
done
```

Great, one last question..
How do I get libvorbis? :-

$ sudo apt-get install libvorbis
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libvorbis

---

### Post by ron999 on 2011-08-31
> **macey said:**
> Great, one last question..
How do I get libvorbis? :-

It's probably already built into FFmpeg.
Test it with one file:-
```
ffmpeg -i filename.flac -acodec libvorbis -aq 6 filename.ogg
```

---

### Post by macey on 2011-08-31
> **ron999 said:**
> It's probably already built into FFmpeg.
Test it with one file:-
```
ffmpeg -i filename.flac -acodec libvorbis -aq 6 filename.ogg
```

No it isn't:-

Unknown encoder 'libvorbis'

---

### Post by ron999 on 2011-08-31
> **macey said:**
> No it isn't:-
Unknown encoder 'libvorbis'
OK
Try using option **B** or **C** here:- [http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs")

---

### Post by macey on 2011-08-31
> **ron999 said:**
> OK
Try using option **B** or **C** here:- [http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs")


Ok, cracked it! Forgot that I had a non-standard install of ffmpeg, (option A from your link!)
removed it and re-installed from apt-get install & all worked as desired!
Thanks for all your help everyone!:):):):popcorn::guitar:

---

