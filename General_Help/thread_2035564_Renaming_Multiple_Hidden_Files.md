---
title: "Renaming Multiple Hidden Files"
date: 2012-07-30
forum: General Help
---

### Post by Neutronst4r on 2012-07-30
Greetings!
First of, it's my first post. I switched to Ubuntu - and Linux in general - just a few days ago. I am still learning most stuff. So, in any case... thank you for you help and patience :)


[LIST=1]
[*] I have a lot of music (ca. 110 GB) and I am still looking for a player/organizer. Rhythmbox practically does everything I need. There is just one little beauty tweak I want. In Library under Music, there are two entries: "Music" and ""Purchased from Ubuntu One". I don't want any sub-entries. When I click "Music" under "Library", I want it to directly show all my songs. Is that possible?
[*]While I decided to use this chance after having a new clean OS, I wanted to clean up my music library and encountered a big problem. Under Windows I used Winamp and it's Auto-Organizer used to format my song files in the following way: ```
<Track#>. - <Artist> - <Song Name>.<File format>
```While at that time it seemed to me a good idea to add the extra "." after "<Track#> and it didn't hurt anybody. Now in Ubuntu I have the huge problem, that songs that didn't have a Track# in their ID3-Tag simply start with a "." which apparently makes them hidden. I only noticed this behavior after deleting about 25 folders which didn't contain any files and that made me suspicious... I was able to recover them from Thrash, but then I also noticed that Rythmbox does not detect hidden music files, so i have to rename them.
[/LIST]
 
What I tried:

[LIST=1]
[*] I was looking for a way to remove all "." 's from files that start with it and installed GPRename, but that didn't show hidden files either...
[*] Then I was looking for a terminal command line that would do the trick, something like that was describes in this thread [http://ubuntuforums.org/showthread.php?t=1778221](http://ubuntuforums.org/showthread.php?t=1778221). ```
find /dir -type f -name "sixteen*" -exec mv {} "${echo {} | sed 's/sixteen/16/'}"
```But I have absolutely no idea how to code the thing I need, especially how to tell it, that it should only remove "." 's from the front of the file names and not the end.
[*]I also tried to use EasyTag, but in crashes after its done scanning. It just keeps using 100% of one of my CPUs for like >20 minutes and nothing happens.
[/LIST]
 
Does anyone have an idea how to resolve these issues?^^

---

### Post by vexorian on 2012-07-30
On one hand, yes, there is a good chance you can do it with bash. On the other hand, I don't know that much bash. So, here is a python hack:

```

import os
import sys
PREF = "x"
files = os.listdir("./")
for file in files:
    if (file[0] == '.'):
        os.system( 'mv "%s" "%s%s"'%(file,  PREF,  file ) )

```

Make sure the spaces stay like that.

Change the x in the PREF="x" to whatever prefix you want to add.

Place this script in ~ ( You know how ~ is your home folder). Name it fixfolder.py.


Then get a terminal window and use **cd** to enter the folder that has the issue. Type

```

python ~/fixfolder.py

```
Should run the script using that folder.

---

### Post by steeldriver on 2012-07-30
you could use 'rename' - to avoid renaming . and .. the search pattern is a bit more complicated - it says find any name beginning with a literal . and followed by at least one other character excluding . and then replace with whatever came after the dot

```
rename -nv 's/\.([^.]+)/$1/' \.*
```check what it reports and if it looks a-ok remove the -n to do the replacement for real, i.e.

```
rename -v 's/\.([^.]+)/$1/' \.*
```

EDIT : on second thoughts this might be better:

```
rename -nv 's/\.[ \t]*-[ \t]*//' \.*
```

which replaces any leading string of literal . followed by whitespace-hyphen-whitespace i.e.

. - <Artist> - <Song Name>.<File format> ---> <Artist> - <Song Name>.<File format>

---

### Post by Neutronst4r on 2012-07-30
Okay, that's a great start. Thank you very much. There is one big problem thought:

The Program you wrote does not recognize files in sub-folders. My Music-Library has a structure like this: /<Artist>/<Album>/<Song>.mp3

---

### Post by steeldriver on 2012-07-30
oops missed that bit, how about

```
find . -type f -name '\.*' -exec rename -nv 's/\.[ \t]*-[ \t]*//' {} \;
```

---

### Post by Neutronst4r on 2012-07-30
Thank you very much steeldriver, that did the trick.

Vexorian your programm worked too, except for the subfolders. Thank you anyway!

---

