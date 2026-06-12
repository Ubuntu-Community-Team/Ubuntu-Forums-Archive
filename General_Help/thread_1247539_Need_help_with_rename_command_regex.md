---
title: "Need help with rename command regex"
date: 2009-08-23
forum: General Help
---

### Post by DirkGently on 2009-08-23
Hey all,

I'm really bashing my head on this one. I'm trying to do a batch rename of some cowboy bebop episodes and can't manage to clean up the file names in one "rename" line. Here is how they look

[aX]_Cowboy_Bebop_-_Session_00_SessionString.mp4

and I want to go to...

Cowboy_Bebop-Session00_SessionString.mp4

I'm way to stubborn at this point to do them one by one...any chance there is anyone out there with the regex expertise i need? 

A breakdown of the resulting expression would be much apprecated. :)

---

### Post by Brandon Williams on 2009-08-23
Provided that the current and new filenames always match the pattern that you've specified, you could do something simple like this:
```
for f in [aX]_Cowboy_Bebop_-_Session_*.mp4; do
    mv $f Cowboy_Bebop-Session${f#[aX]_Cowboy_Bebop_-_Session_}
done
```

The first line contains a file "glob" that matches all mp4 files with the common string at the beginning of the file name. The * indicates that any number of any character is allowed to occur in that position.

The second line contains the variable substitution ${f#[aX]_Cowboy_Bebop_-_Session_}, which means to strip the specified string from the beginning of the variable's value and output the remaining characters. Having stripping the common part of the string from the filename, we then prepend the new common string at the beginning and make that the target of a file rename.

---

### Post by DirkGently on 2009-08-23
That worked like a dream. Thanks for the tip. I had to escape the braces tho, so for future reference:

```
for f in \[aX\]_Cowboy_Bebop_-_Session_*.mp4; do
    mv $f Cowboy_Bebop-Session${f#\[aX\]_Cowboy_Bebop_-_Session_}
done
```

again, thanks a ton brandon

EDIT: actually that left my file names like this:

Cowboy_Bebop-Session00_-_SessionString.mp4

Any clue as to how I could fix the while name from the original format at the top?

---

### Post by Brandon Williams on 2009-08-23
Ah-hah ... I didn't realize that you mean that '[' and ']' were actually in the file name.

As for the additional "_-_" in the middle of the name, you could modify the loop to look like this:
```
for f in Cowboy_Bebop-Session*.mp4; do
    mv $f ${f%_-_*}-${f#*_-_}
done
```
The ${f#*_-_} is doing about what it did before ... remove the shortest matching glob from the beginning of the variable value. The ${f%%_-_*} removes the longest matching glob from the end. This will work as long as "_-_" only occurs once in the file name. Otherwise, it will replace the first instance of "_-_" with "-", and leave any other occurrences in place.

If you used ## in the first one instead of just #, it would remove the longest match from the beginning instead of the shortest, and % instead of %% would remove the shortest match instead of the longest from the end.

---

