---
title: "CLI syntax issue: substiting {} with find command"
date: 2010-02-13
forum: General Help
---

### Post by lucasart on 2010-02-13
Hello everyone,

My problem is rather simple, I would like to use the {} which is the "loop variable" of the find command in usual substitution patterns. More precisely, let's say I would like to convert all my *.flac files with $flacdir (including subdirs) into *.wma with the ffmpeg command: here is a for loop attempt that actually works

```

export IFS=$'\n'
for flac in $(find $flacdir -type f -iname \*.flac)
do
    # build the wma filename (in the same directory)
    wma="${flac%.flac}.wma"

    # convert $flac to $wma
    ffmpeg -i $flac -acodec wmav2 -ab 128kb $wma
done
export IFS=" "

```

But then I wanted to be clever and replace all this garbage by a one liner find command! This is mainly because I want to improve my understanding of the Linux shell (don't be too harsh, I'm a newbie, recently repented Windows user). So here is my "approximate" attempt:

```

find $flacdir -type f -iname '*.flac' -exec \
    ffmpeg -i {} -acodec wmav2 -ab 128kb "${{}%.flac}.wma" \;

```

Bash throws my with a message like "bad substitution", and what it doesn't like is this construction

```

"${{}%.flac}.wma"

```

which would work if {} was a normal variable, as we have seen in the for loop above with the construction:

```

"${flac%.flac}.wma"

```

I know I am very close to the solution, but there must be some subtility I am missing. Help appreciated :)

---

