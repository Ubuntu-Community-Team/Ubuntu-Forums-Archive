---
title: "bash script help - 5 field limit??"
date: 2010-04-17
forum: General Help
---

### Post by UserEnzis on 2010-04-17
Hello. I'm trying to write a script to take a 5 field file, do some math, and extend it to 9 fields. Problem is, the script keeps wrapping it to two lines, even tho 9 fields, tab separated (even comma separated) doesn't fill the screen. Even if it did, I'm eventually copying it to an excel sheet anyways, and it really NEEDS to be one line. I've tried things like paste with no luck. It HAS to be possible to do one line, b/c it's way too inconvenient otherwise. Here's an example:

file = adder.sh
```

# this wraps to two lines :(
echo "$f1\t$f2\t$f3\t$f4\t$f5\t$cost\$time\t$rank\t$analysis" > file.txt

# this also forcefully wraps to two lines :(
echo "$f1\t$f2\t$f3\t$f4\t$f5" > file1
echo "$cost\$time\t$rank\t$analysis" >  file2
paste file1 file2 > file.txt

```any help would be much appreciated

---

### Post by blueridgedog on 2010-04-17
Echo them one at a time to a file and see which one is creating a line break, then investigate how the variable is being set, such that it is getting the end of line character.

Alternatively, adjust your scrip to chop of any end of line character when taking the input from the terminal.

---

### Post by efflandt on 2010-04-17
You were missing something, the "t" in the \t before $time

```
# this wraps to two lines :(
echo "$f1\t$f2\t$f3\t$f4\t$f5\t$cost\[COLOR=Red]t[/COLOR]$time\t$rank\t$analysis" > file.txt

# this also forcefully wraps to two lines :(
echo "$f1\t$f2\t$f3\t$f4\t$f5" > file1
echo "$cost\[COLOR=Red]t[/COLOR]$time\t$rank\t$analysis" >  file2
paste file1 file2 > file.txt
```But see **man echo**.  If you want tabs instead of "\t" characters (-e), and want to connect the more than one echo into the same line (-n), and forget generating file1 and file2 by appending instead, try this and compare file1.txt with file2.txt:
[FONT=monospace]
[/FONT]```
# this expands tabs on one line :(
echo -e "$f1\t$f2\t$f3\t$f4\t$f5\t$cost\t$time\t$rank\t$analysis" > file1.txt

# this appends with expanded tabs to one line :(
echo -ne "$f1\t$f2\t$f3\t$f4\t$f5" > file2.txt
echo -e "\t$cost\t$time\t$rank\t$analysis" >>  file2.txt
```[FONT=monospace]
[/FONT]

---

### Post by UserEnzis on 2010-04-18
Hi guys. Thanks for your thoughts. Efflandt, you're pretty perceptive to notice that missing "t".

I've tried the -n and using two lines and checked the man page on echo and still have no luck :(. It seems like whatever I try, unix just wants to forcefully put in it's own newline feed at the end of so many characters. There's GOT to be a way to do this tho. There ARE files out there with long lines, as can be very necessary.

Just FYI, this code is an example of something used in a loop to manipulate a file 10,890 lines long. So it'd be really nice to get the script to work so I don't have to manually change each line.... Any extra thought would be much appreciated. I do believe it's a problem with the "echo" command forcefully causing a line size limit tho. Not sure if there's another way to get what I want and print it to a file.

---

### Post by UserEnzis on 2010-04-18
Hi again. I just figured it out. Blueridgedog, it turns out your post had the answer I should have paid careful attention to right from the start. That newline character was part of the variable retrieved from the original file, since it was the last field and had the newline anyways. Knowing this, I'll look into how to chop off the final character (maybe with some sed trick) from just that one specific field.

efflandt, although your post didn't solve my problem, it still led me to research and learn about a line size limit that, though is much larger, exists in the shell. As I plan to do scripting in the professional world some day, I'm glad to have learned all this. Thank you guys both.

---

### Post by blueridgedog on 2010-04-18
You can get lots of sed examples via Google for dropping the white space at the end of a variable.  Good luck.

Almost everything you could need is here:

[http://sed.sourceforge.net/sed1line.txt](http://sed.sourceforge.net/sed1line.txt)

---

