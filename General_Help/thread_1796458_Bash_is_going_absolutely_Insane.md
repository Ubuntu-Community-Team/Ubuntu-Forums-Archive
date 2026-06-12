---
title: "Bash is going absolutely Insane"
date: 2011-07-03
forum: General Help
---

### Post by IrrationlArtist on 2011-07-03
Hello. I was working in a folder containing some notes I've written in a terminal environment and the terminal simply does not recognize the file, even though it's obviously there!

I previously used the command mmv to relocate said files to my notes folder. I'm a CLI intermediate, with an average amount of experience with the terminal. That being said, I'm at a loss to explain it. I've tried rebooting, running as root, you name it.

Displayed below is a picture of the situation. Note that personal information is blurred out for privacy. Thank you in advance for helping, as not only is this rather serious, but I would really, really, really hate to lose these files if the disk is corrupt or something like that.

[IMG]http://dl.dropbox.com/u/22697905/bashisflipping.png[/IMG]

---

### Post by papibe on 2011-07-03
The command ls aligns its output perfectly (in columns). Do you see how your output is not "apparently" aligned? My guess is that some filenames have a character before its readable name. If it's just an space, you could do this:
```
$ cat " December 13, 2010.txt"
```
or
```
$ cat \ December\ 13,\ 2010.txt
```
If it is another character, came back here so we can help you.

Hope it helps.

---

### Post by Sealbhach on 2011-07-03
It's probably the spaces in the filenames that are causing the problem. Try renaming it as December_13_2010.txt and see if that makes a difference.

---

### Post by IrrationlArtist on 2011-07-03
How did I miss that!? Thank you both so much, I feel like a complete idiot now... Well, at least I know it's not serious. :D Thanks again.

---

### Post by haqking on 2011-07-03
looks like a filename 101 issue.

Spaces are allowed but never recommended, replace spaces with underscore as above _

edit: oh well you chimed in above at same time ;-) glad you got it sorted

---

### Post by prodigy_ on 2011-07-03
A simple script to remove any leading spaces/tabs from names in the current directory and replace any remaining spaces/tabs with underscores:
```
#!/bin/bash

for OldFileName in *
do
        NewFileName="$(echo "$OldFileName" | sed -e 's/^[ \t]*//' -e 's/[ \t]/\_/g')"
        test "$NewFileName" = "$OldFileName" || mv -T "$OldFileName" "$NewFileName"
done
```

---

