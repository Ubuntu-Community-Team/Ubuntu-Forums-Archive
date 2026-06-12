---
title: "how do you exclude a file from a wildcard statement"
date: 2011-09-08
forum: General Help
---

### Post by bigdee973 on 2011-09-08
how do you exclude a file from being included a wildcard statement in terminal.

for example:

say i want to copy an paste all text files ...
cp *.txt /home/whoever/Desktop

except file NOTthisfile.txt..

how do i do that?

---

### Post by papibe on 2011-09-08
```
$ find -iname '*.txt' -not -name NOTthisfile.txt -exec echo cp {} /home/whoever/Desktop \;
```
find files:
[INDENT]-iname case insensitive match to *.txt
-not add a negative condition to the match (next expression).
-name match exact name NOTthisfile.txt
-exec for every file found execute the next command.
{} represents the matched file on the command.
[/INDENT]
NOTE: to make this example safe, instead of copying the files, I'm printing (using echo) the command you want execute. That way you can see what's going on, makes changes, etc. To actually execute the copy just remove the 'echo'.

Hope it helps,
Regards.

---

### Post by bigdee973 on 2011-09-08
i removed echo and set everything the right way according to my system however i get this error.

find: missing argument to `-exec'

---

### Post by papibe on 2011-09-08
Could you post the exact command you are running (pasted from the terminal)? 
Regards.

---

### Post by Habitual on 2011-09-08
> **bigdee973 said:**
> how do you exclude a file from being included a wildcard statement in terminal.

for example:

say i want to copy an paste all text files ...
cp *.txt /home/whoever/Desktop

except file NOTthisfile.txt..

how do i do that?

```
cp *.txt !(NOTthisfile.txt) /home/whoever/Desktop
```

---

### Post by bigdee973 on 2011-09-10
> **Habitual said:**
> ```
cp *.txt !(NOTthisfile.txt) /home/whoever/Desktop
```

Sorry that didnt work neither. this is what i get and it still includes the file i asked not to copy


fellayaboy@fellayaboy-Dimension-4600:~$ cd Pictures/
fellayaboy@fellayaboy-Dimension-4600:~/Pictures$ ls
nathaniel.jpg
Orange-Background-1280X960-2641.jpg
Orange_Fractal_wallpaper_by_OrangeRoom.jpg
orange-scrunch-001.jpg
screenshots
space.jpg
Super_Mario_Bros._Game.jpg
Super-Mario-World-Super-Mario-Advance-2-super-mario-world-5611247-1024-768.jpg
unemployconfim
fellayaboy@fellayaboy-Dimension-4600:~/Pictures$ cp *.jpg !(space.jpg) /home/fellayaboy/Desktop/
cp: warning: source file `nathaniel.jpg' specified more than once
cp: warning: source file `Orange-Background-1280X960-2641.jpg' specified more than once
cp: warning: source file `Orange_Fractal_wallpaper_by_OrangeRoom.jpg' specified more than once
cp: warning: source file `orange-scrunch-001.jpg' specified more than once
cp: omitting directory `screenshots'
cp: warning: source file `Super_Mario_Bros._Game.jpg' specified more than once
cp: warning: source file `Super-Mario-World-Super-Mario-Advance-2-super-mario-world-5611247-1024-768.jpg' specified more than once
cp: omitting directory `unemployconfim'
fellayaboy@fellayaboy-Dimension-4600:~/Pictures$

---

### Post by bigdee973 on 2011-09-10
> **papibe said:**
> ```
$ find -iname '*.txt' -not -name NOTthisfile.txt -exec echo cp {} /home/whoever/Desktop \;
```
find files:
[INDENT]-iname case insensitive match to *.txt
-not add a negative condition to the match (next expression).
-name match exact name NOTthisfile.txt
-exec for every file found execute the next command.
{} represents the matched file on the command.
[/INDENT]
NOTE: to make this example safe, instead of copying the files, I'm printing (using echo) the command you want execute. That way you can see what's going on, makes changes, etc. To actually execute the copy just remove the 'echo'.

Hope it helps,
Regards.


nevermind it worked! i didnt capitilize a word.. how would i go about excluding 2 more files.

---

### Post by sisco311 on 2011-09-10
In bash, you can use extended globs:
```
shopt -s extglob
cp !(NOTthisfile.txt) /path/to/dest
```

See:
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

---

### Post by bigdee973 on 2011-09-10
> **sisco311 said:**
> In bash, you can use extended globs:
```
shopt -s extglob
cp !(NOTthisfile.txt) /path/to/dest
```

See:
[http://mywiki.wooledge.org/glob](http://mywiki.wooledge.org/glob)

strange..i did the command but it seems it removed my files and never copied them to my desktop

fellayaboy@fellayaboy-Dimension-4600:~/Pictures$ ls
nathaniel.jpg                               orange-scrunch-001.jpg  Super_Mario_Bros._Game.jpg
Orange-Background-1280X960-2641.jpg         screenshots             Super-Mario-World-Super-Mario-Advance-2-super-mario-world-5611247-1024-768.jpg
Orange_Fractal_wallpaper_by_OrangeRoom.jpg  space.jpg               unemployconfim
fellayaboy@fellayaboy-Dimension-4600:rm /home/fellayaboy/Desktop/*.jpg
fellayaboy@fellayaboy-Dimension-4600:~/Pictures$ cp !(space.jpg) /home/fellayaboy/Desktop
cp: omitting directory `screenshots'
cp: omitting directory `unemployconfim'
fellayaboy@fellayaboy-Dimension-4600:~/Pictures$ ls
screenshots  unemployconfim

and i checked desktop..theres nothign their

---

### Post by sisco311 on 2011-09-10
You didn't enabled the extglob option, hence ! was treated as the history expansion character.

---

### Post by papibe on 2011-09-10
> **sisco311 said:**
> You didn't enabled the extglob option, hence ! was treated as the history expansion character.
extglob is enabled by default in both of my systems (both Server and Desktop):
```
$  shopt | grep extglob
extglob        	on

```
I don't see the typical 'cp: cannot stat...' error, so it seems it is set. That should have worked (unless that was not an accurate copy/paste of the terminal).

bigdee973, Could you check if extglob is set in your system?

Regards.

---

### Post by papibe on 2011-09-10
> **bigdee973 said:**
> how would i go about excluding 2 more files.
If you are trying to copy just the files in the actual directory, and not not recursively through the subdirectories, I would advice following sisco311's advice and use something like this:
```
$ cp !(file1|file2|file3) /path/to/dest
```
Play with echo a little bit before using the cp command:
```
$ echo *
$ echo !(space.jpg)
$ echo !(*.jpg)
$ echo !(space.jpg|nathaniel.jpg)
```

Now, if there are more files you want to copy, but they are in the directory tree, 'find' will do the trick:
```
$ find . -type f -name '*.jpg' -not -name 'file1' -not -name 'file2' -not -name 'file3' -exec echo cp {} /home/fellayaboy/Desktop/ \;

```
Note that again I'm echoing the command so you can debug it first.

Hope it helps,
Regards.

---

### Post by bigdee973 on 2011-09-11
> **sisco311 said:**
> You didn't enabled the extglob option, hence ! was treated as the history expansion character.

pah!..silly me...it worked! thank you and please forgive my noobieness :P

---

### Post by sisco311 on 2011-09-11
You're welcome! I'm glad it worked.

---

### Post by bigdee973 on 2011-10-18
hey can u give me a link to history expansion tutorial

---

### Post by sisco311 on 2011-10-18
I'd start with the man page.
```
man bash | less +/^"HISTORY EXPANSION"
```
[http://www.gnu.org/s/bash/manual/bash.html#History-Interaction](http://www.gnu.org/s/bash/manual/bash.html#History-Interaction)

---

