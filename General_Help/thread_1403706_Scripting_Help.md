---
title: "Scripting Help"
date: 2010-02-10
forum: General Help
---

### Post by dardack on 2010-02-10
I wrote this script to convert a mp4 download, extract the audio and convert to mp3:

```
#! /bin/bash
echo $*
mplayer "$*" -vo null -ao pcm:file="$*".wav && lame "$*".wav
rm "$*".wav
```

However, i get a file names, file.mp4.wav.mp3, i would love a way to remove the .mp4.wav part, can this be done with sed somehow?

---

### Post by falconindy on 2010-02-10
rename will do this for you.

```
rename 's/\.mp4\.wav//' *.mp3
```

---

### Post by apmcd47 on 2010-02-10
> **dardack said:**
> I wrote this script to convert a mp4 download, extract the audio and convert to mp3:

```
#! /bin/bash
echo $*
mplayer "$*" -vo null -ao pcm:file="$*".wav && lame "$*".wav
rm "$*".wav
```

However, i get a file names, file.mp4.wav.mp3, i would love a way to remove the .mp4.wav part, can this be done with sed somehow?

[PHP]#! /bin/bash
for mp4 in "$@"
do
   ff=${mp4%.mp4}
   wav=${ff}.wav
   mplayer "$mp4" -vo null -ao pcm:file="$wav" && lame "$wav"
   rm "$wav"
done
[/PHP]

[LIST=1]
[*]Don't use $* in this context - it uses all your arguments in one quoted string - use $@ instead. 
[*]Put the thing in a loop to pull one file out of the argument list at a time
[*]${name%match} removes trailing match from string of $name
[*]I've used variable names mp4 and wav so you can see which is which
[/LIST]
If you only ever use this with one argument use $1 and remove the loop.

Andrew

---

### Post by dardack on 2010-02-11
what is the difference between $@ and $*?

---

### Post by kaibob on 2010-02-11
> **dardack said:**
> what is the difference between $@ and $*?

The following contains a good explanation of the difference between $* and $@

[http://www.bash-hackers.org/wiki/doku.php/scripting/posparams#mass_usage](http://www.bash-hackers.org/wiki/doku.php/scripting/posparams#mass_usage)

---

### Post by dardack on 2010-02-11
> **apmcd47 said:**
> [PHP]#! /bin/bash
for mp4 in "$@"
do
   ff=${mp4%.mp4}
   wav=${ff}.wav
   mplayer "$mp4" -vo null -ao pcm:file="$wav" && lame "$wav"
   rm "$wav"
done
[/PHP]

[LIST=1]
[*]Don't use $* in this context - it uses all your arguments in one quoted string - use $@ instead. 
[*]Put the thing in a loop to pull one file out of the argument list at a time
[*]${name%match} removes trailing match from string of $name
[*]I've used variable names mp4 and wav so you can see which is which
[/LIST]
If you only ever use this with one argument use $1 and remove the loop.

Andrew

TYVM, I just made one change.

wav=${ff}.wav to wav=${ff}

This way I end up with a File.mp3 instead of File.wav.mp3.  TY so much.

And I See what you mean, i was using $* cause i was only putting 1 file at a time, with $@ i can do ton of files, that is awesome.  Well with the "" and ty for link.

---

