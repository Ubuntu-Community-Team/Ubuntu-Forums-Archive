---
title: "Bash Script - renaming files from CSV"
date: 2010-09-28
forum: General Help
---

### Post by clownschoolphd on 2010-09-28
Hello,

I need some help with a bash script.  I'm a scripting n00b and in a little over my head.  I imagine there'll be a lot of if's and cuts and maybe some regexing? --Spooky.

I have a folder with a bunch of audio files and a csv file with information I need to use to generate names for the files.

$ ls audio_holder_folder/
00001.WAV
00002.MP3
00003.WAV
00004.MP2
00005.WAV
00006.MP3

$ cat audio_data.csv
00001,show 1 title,22-Oct-08
00002,show2title,22-Oct-08
00003,show3 title,22-Oct-08
00004,show4title,22-Oct-08
00005,show 1 title,23-Oct-08
00006,show2title,23-Oct-08

My scripting knowledge is limited (though growing!). But to tell you the truth, I'm not sure where to start here.  Especially given that some files have spaces in the names and there are different file extensions that need to handled correctly.

At the end of the day, I need to match a file name with the first column of the csv and rename it with the second two columns and keep the file extension.

File "00001.WAV" would become "show 1 title 22-Oct-08.WAV"

I have a few years worth of files to rename.  So this is a perfect opportunity to advance my scripting skills.  I'm fine with reading/googling/man pages and I do want to understand the how's and why's of how to do this, but I'm going to need some help getting started.

Would appreciate the help anyone is willing to give.

---

### Post by DaithiF on 2010-09-28
Hi, maybe something like this:
```
#!/bin/bash
IFS=,
shopt -s nullglob
while read id title date
do
        for file in audio_holder_folder/$id.*
        do
                ext=${file#*.}
                echo mv "$file" "audio_holder_folder/$title $date.$ext"
        done
done < audio_data.csv

```
remove the echo if happy with what its doing.  (though you might prefer to cp to a different directory rather than mv, for absolute safety).

---

### Post by clownschoolphd on 2010-09-28
Daithi,

That worked prefectly!  Thank you very much.  I did end up copying to a new directory instead of moving.  

Actually a lot easier than I thought it would be.  Nowhere near as much text parsing as I thought would be necessary.

Appreciate it!


Now that that's automated, I'll be googling for exactally what "shopt -s nullglob" means. :)



shopt [-pqsu] [-o] [optname ...]
    Toggle the values of variables controlling optional shell behavior. With no options, or with the -p option, a list of all settable options is displayed, with an indication of whether or not each is set. The -p option causes output to be displayed in a form that may be reused as input. Other options have the following meanings:

        -s
            Enable (set) each optname. 

nullglob
    If set, bash allows patterns which match no files (see Pathname Expansion above) to expand to a null string, rather than themselves.

---

### Post by DaithiF on 2010-09-29
Hi, the reason for using nullglob is hopefully clear, but in case not ... if nullglob wasn't set, and if there was some pattern e.g. 00007, for which there was no matching file(s), then the glob 00007.* would return '00007.*' and then the code that does something with matching items would have to first check for an existing file before trying to operate on it.  With nullglob turned on, 00007.* returns nothing, which means no extra logic is required.

---

