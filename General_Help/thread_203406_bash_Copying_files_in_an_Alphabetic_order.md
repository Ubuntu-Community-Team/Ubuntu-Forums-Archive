---
title: "bash: Copying files in an Alphabetic order"
date: 2006-06-25
forum: General Help
---

### Post by stimpack on 2006-06-25
My mp3 player plays on the order that files were copied. When I copy from kde/gnome/bash shell they get copied in a fixed order probably related to where on the disk they are and not based on filename.

My files are of this format:

```
01-AudioTrack 01.mp3  06-AudioTrack 06.mp3  11-AudioTrack 11.mp3
02-AudioTrack 02.mp3  07-AudioTrack 07.mp3  12-AudioTrack 12.mp3
03-AudioTrack 03.mp3  08-AudioTrack 08.mp3  13-AudioTrack 13.mp3
04-AudioTrack 04.mp3  09-AudioTrack 09.mp3  14-AudioTrack 14.mp3
05-AudioTrack 05.mp3  10-AudioTrack 10.mp3  15-AudioTrack 15.mp3

```

And need to be copied alphabetically so track 1 gets played first etc..

The space in the filename seems to cause endless problems, yet I have many ripped directorys, renaming is not an option.

I have tried various things: (\tmp would be my mp3 player, but serves as an example)

```
cp `ls -Q` \tmp
cp "`ls -Q`" \tmp
cp `ls -Q1` \tmp
cp `ls -b` \tmp
```

and many more combos.

Any help would be appreciated!.

---

### Post by .t. on 2006-06-25
"cp -r . /tmp" should do it. "cp -r" means do a recursive copy. "." means the current directory, and "/tmp" is /tmp. It should copy them exactly as they are in ., and alphabetic copying shouldn't make any difference to the order played. It doesn't change filenames, so it's still in order.

EDIT: Oh, and directories in *NIX are expressed by a "/", not a "\" as in DOS/Windows. So it's "/tmp". A "\" is used to denote a special character, such as a space, which otherwise would be interpreted by the shell, and not passed on to the application.

---

### Post by ayoli on 2006-06-25
Is that help you ?
```
for i in `ls |sort -n`; do
   cp $i /where/you/want/;
done;
```
regards.

---

### Post by mlind on 2006-06-25
if you have problems with files that have whitespaces or other weird charachters on their name, put name inside quotation marks ""

for example
```

cp "01-AudioTrack 01.mp3" /tmp

```

```

mkdir /tmp/mymp3
cp *.mp3 /tmp/myp3

```

If you really need to apply so sorting, you can use ls | sort

---

### Post by stimpack on 2006-06-25
Thanks all but no joy.

@ .t. the order in which they are copied does matter to my mp3 player, thats the only thing it uses, not filename or anything. Its kinda annoying.

@ayoli: This gives me the same problem that my attempts gave, namely
```
cp: cannot stat `01-AudioTrack': No such file or directory
cp: cannot stat `01.mp3': No such file or directory
cp: cannot stat `02-AudioTrack': No such file or directory
cp: cannot stat `02.mp3': No such file or directory
```

etc.., that space is causing problems, even then double quoting with "`ls |sort -n`" or slash escaping `ls -b |sort -n` do not work.

Its a puzzle :/

---

### Post by ayoli on 2006-06-25
sorry, that's true that sort won't work due to spaces in filenames.

---

### Post by Quirky on 2006-06-25
This might do it:
```
find . -type f -print0 | sort -z -n  | xargs -0 cp --target-directory='/tmp'
```

Or if not, another hacky way is to replace the space with a character, then return it to a space before doing the copy. Like this:

```
for i in $( ls *.mp3 | sort -n | sed 's% %~%g') ; do  echo "${i/~/ }" ; cp "${i/~/ }" /tmp/  ; done
```

That depends on the fact that your file doesn't have a "~" in it, which is why it is hacky.

---

### Post by ayoli on 2006-06-25
[QUOTE=Quirky]This might do it:
```
find . -type f -print0 | sort -z -n  | xargs -0 cp --target-directory='/tmp'
```

Or if not, another hacky way is to replace the space with a character, then return it to a space before doing the copy. Like this:

```
for i in $( ls *.mp3 | sort -n | sed 's% %~%g') ; do  echo "${i/~/ }" ; cp "${i/~/ }" /tmp/  ; done
```

That depends on the fact that your file doesn't have a "~" in it, which is why it is hacky.[/QUOTE]
your first code works great, but the second doesnt replace the ~ on echo, so cp should fail:
```
[16:47:56@ayoli.zone]:~/test >$ ls
01-AudioTrack 01.mp3  01-AudioTrack 02.mp3
[16:49:45@ayoli.zone]:~/test >$ for i in $( ls *.mp3 | sort -n | sed 's% %~%g') ; do  echo "${i/~/ }" ;done;
01-AudioTrack~01.mp3
01-AudioTrack~02.mp3
```

---

### Post by stimpack on 2006-06-25
Hey thanks guys that worked perfect, now I can listen to my tracks in order :).

---

### Post by Quirky on 2006-06-26
Well, the second approach was a hack :) 

My sample set was too limited, they had just one space. The ${i/~/ } should have been ${i//\~/ } - note the extra slashes - the first replaces just the first space and tilde replaces, the second replaces all tildes, escaping them with spaces.

---

