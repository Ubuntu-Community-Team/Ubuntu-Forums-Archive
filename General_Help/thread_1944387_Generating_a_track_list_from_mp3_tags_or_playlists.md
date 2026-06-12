---
title: "Generating a track list from mp3 tags or playlists?"
date: 2012-03-21
forum: General Help
---

### Post by zero2xiii on 2012-03-21
Hay all,

I like to buy CDs and then rip them, and then reburn CDs with certain types op music grouped. But I want to create a tracklist for the CD aswell. Normaly I do this by hand, but this is tedious and somewhat errorous.

The idea is:

Create playlist in rhythmbox,
Burn new CD
Save tracklist
Print tracklist.

Now if I save the playlist, there is so much extra information that I dont need, and if the file name is different than what I want, I need to type the missing info extra.

Example: File=Blah Blah Blah.mp3
ID3 Tag: Artist=KE$SHA
         Title=Blah Blah Blah

Is there an easy way to do this, even if it requires some command line program that I can then scrip to transform my playlists into track lists?

Thanks in advance

---

### Post by zero2xiii on 2012-05-05
Sigh,

I got this script working. It transforms my rythmbox music player saved playlists to text track lists. It is working sofar. It is invoked by rightclicking on the playlist, and then running the script trought nautilus script function. So it WILL NOT WORK under another program.

But it does work. Ubuntu 10.04.4

Cherz

```
#!/bin/bash

file=` echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | tr -d '\n'`

sed -e '/playlist/d' -e '/X-GNOME/d' -e '/NumberOfEntries/d' -e'/File/d' \
-e 's/Title//g' -e 's/=/. /g' "$file" > "$file".txt 
```

---

### Post by BoogeyOfTheMan on 2012-07-23
> **zero2xiii said:**
> Sigh,

I got this script working. It transforms my rythmbox music player saved playlists to text track lists. It is working sofar. It is invoked by rightclicking on the playlist, and then running the script trought nautilus script function. So it WILL NOT WORK under another program.


Nice script. If one wanted to have it list artist name and album, how would one modify that script?

---

### Post by zero2xiii on 2012-07-23
Wow,

It will be somewhat much more comprehensive. You will need to actualy read the Tag from the file.

Might peek at it. But I have never done something like that. Will see what I can do.

Cherz

---

### Post by zero2xiii on 2012-07-23
Hay,

Seems like a have found a tool that will make scripting something somewhat easier.

Its called "mp3info". Will look into it tomorrow and post a possible solution here.


Cherz

---

### Post by zero2xiii on 2012-07-24
Hay,

So just an update. I got this script going and working. Works under nautilus and with the playlists saved with rhythmbox. Please note this needs mp3info to be installed:

```
sudo apt-get install mp3info
```

Script goes like this:

```
#!/bin/sh

input=` echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | tr -d '\n'`

grep "file://" "$input" | sed -e 's_File[0-9]*=file://__g' -e 's_%20_ _g' > "$input"_stage1.txt

while read p; do
  mp3info -p "%t - %a, %l\n" "$p" | sed 's_ - , _ERROR_g' >> "$input"_stage2.txt
done < "$input"_stage1.txt

cat -n "$input"_stage2.txt > "$input"_tracklist.txt
rm "$input"_stage1.txt
rm "$input"_stage2.txt
 
exit 0
```

Please note that there are some 'issues' with the mp3info package complaining about the tags some times. These files will have the word ERROR printed in the tracklist generated.

"man mp3info" for details on this and why it happens, aswell as the used syntax for formating of the actual track list.

Currently it outputs:
Title - Artist, Album.

Hope this help some folks aswell :)

Cherz,
Philip

---

### Post by Vaphell on 2012-07-24
i don't think it's safe to assume that %20/space is the only escaped character you can get in URIs
[http://en.wikipedia.org/wiki/Percent-encoding](http://en.wikipedia.org/wiki/Percent-encoding)

i'd go with something like this
```
path="$( echo -en ${p//%/\\x} )"
```
to replace each %NN with \xNN and echo it with -e switch to transform it to the 'true' form
```
$ p=a%20b%21c%25d%2ee
$ path="$( echo -en ${p//%/\\x} )"
$ echo "$path"
a b!c%d.e
```

---

### Post by BoogeyOfTheMan on 2012-07-25
> **zero2xiii said:**
> Hay,

So just an update. I got this script going and working. Works under nautilus and with the playlists saved with rhythmbox. Please note this needs mp3info to be installed:

```
sudo apt-get install mp3info
```

Script goes like this:

```
#!/bin/sh

input=` echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | tr -d '\n'`

grep "file://" "$input" | sed -e 's_File[0-9]*=file://__g' -e 's_%20_ _g' > "$input"_stage1.txt

while read p; do
  mp3info -p "%t - %a, %l\n" "$p" | sed 's_ - , _ERROR_g' >> "$input"_stage2.txt
done < "$input"_stage1.txt

cat -n "$input"_stage2.txt > "$input"_tracklist.txt
rm "$input"_stage1.txt
rm "$input"_stage2.txt
 
exit 0
```

Please note that there are some 'issues' with the mp3info package complaining about the tags some times. These files will have the word ERROR printed in the tracklist generated.

"man mp3info" for details on this and why it happens, aswell as the used syntax for formating of the actual track list.

Currently it outputs:
Title - Artist, Album.

Hope this help some folks aswell :)

Cherz,
Philip

I tried the new script, but all I'm getting is an empty text file.

---

### Post by Vaphell on 2012-07-25
```
#!/bin/bash

while read sel
do
  while read uri
  do
    path=${uri#file://};
    path=$( echo -en "${path//%/\\x}" )
    mp3info2 -p "%t - %a, %l\n" "$path"
  done < <( grep -o 'file://.*' "$sel" ) > "$sel"_tracklist.txt
done < <( echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" )
```

my tidier version of the script, using mp3info2 which can reach to id3v2 tags for data, it works just fine.
are you sure you selected playlist files before running that script?

---

### Post by BoogeyOfTheMan on 2012-07-25
Yeah. The old script still works. 

I just tried the tidier version, and it still outputs a blank file. 

When using this, should I save the playlist as a standard playlist, an m3u or an xml?

---

### Post by Vaphell on 2012-07-25
.pls

did you install mp3info and mp3info2? without these you won't get the data extracted from ID3 tags


you can debug the script from command line
in the beginning have
```
NAUTILUS_SCRIPT_SELECTED_FILE_PATHS=/path/to/some/existing/playlist.pls
```
to assign it a value, just like nautilus would
use # to comment out redirection to file ( >/>> file )
and then run the script to see the output in terminal, you should get either good stuff or errors.

---

### Post by BoogeyOfTheMan on 2012-07-25
I installed mp3info, but not mp3info2. when I tried that I get the unable to locate package message

EDIT.
THe only other packages I see in synaptic are libmp3-info-perl and mp3info-gtk. Should those be installed?

---

### Post by Vaphell on 2012-07-25
sorry, it appears it's bundled in libmp3-tag-perl

---

### Post by BoogeyOfTheMan on 2012-07-25
> **Vaphell said:**
> sorry, it appears it's bundled in libmp3-tag-perl

Heres the pls file I've been working with. The original script you posted works with it fine, but for some reason the new ones dont.

---

### Post by Vaphell on 2012-07-25
the format appears to be different. In my case (10.04) paths are in URI format
```
FileN=file:///home/me/Music/some%20cool%20tune.mp3
```
while your file has pretty much ordinary paths.
```
FileN=Music/some cool tune.mp3
```
new scripts look for 'file://' part but in your playlist there were none.


try this
```
#!/bin/bash

while read sel
do
  echo "$sel"
  while read f
  do
    path="$HOME/${f#File*=}"
    mp3info2 -p "%t - %a, %l\n" "$path"
  done < <( grep '^File[0-9]' "$sel" ) > "$sel"_tracklist.txt
done < <( echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" )
```

note that the path in .pls is not full so i add $HOME in front of it. I don't know what the format is supposed to be if files are in a location outside $HOME and what do do with it.

if you have a tidy structure on a per-album basis you could use a script that would parse the paths and didn't rely on 3rd party software to get to Album name from ID3 tags.

While testing i noticed that mp3info2 is somewhat slow, so in case of 10000 files it will take some time ;-)

---

### Post by BoogeyOfTheMan on 2012-07-25
That one worked wonderfully. Thank you sir.

---

