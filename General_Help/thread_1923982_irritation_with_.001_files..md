---
title: "irritation with .001 files."
date: 2012-02-11
forum: General Help
---

### Post by ThaDoctor99 on 2012-02-11
Okay so I got a lot of files that end in .001 .002 all up to .025
and there is a lot of them, they have a lot in common
they all are like basename.301-med.avi.001, and I really don't like to issue commands to join them all, that is to error prone, but I just can't think of a way to make a script to do this.

Could somebody be nice and help me here...

Greetings Denmark

---

### Post by k999 on 2012-02-12
So you want to join the files together to one large file? If they all have the same name except .001 - .025, you should be able to do:

cat basename.301-med.avi.* > complete-basename.301-med.avi

If you want to doublecheck that the files are assembled in the right order, you can write:

echo cat basename.301-med.avi.*

and you can always type out all the file names manually on the command line:

cat basename.301-med.avi.001 basename.301-med.avi.002 basename.301-med.avi.003 > all.avi

---

### Post by ThaDoctor99 on 2012-02-12
thanks, although that part is not the problematic thing, it is to script that it should unpack basename.301-med.avi.001 >.025 and then do the same thing to basename.302-med.avi.001>.025 un till basename.302-med.avi.001>.025
I just really want to write something that join all of those to the basename.number.avi I just can't figure that part out.

---

### Post by Vaphell on 2012-02-12
you could mention what these numbered files are exactly? Base file cut to pieces or some archive split to multiple volumes?
Gluing files together is not the same as unpacking from multiple volume archives.

---

### Post by ubuntu27 on 2012-02-12
[http://ubuntuforums.org/showthread.php?t=1853215](http://ubuntuforums.org/showthread.php?t=1853215)

SO, just join the files 

basename.301-med.avi.001 to basename.301-med.avi.025

and repeat the process for the other one.

---

### Post by ThaDoctor99 on 2012-02-12
Yeah it is just if I do it by hand I probably mess it up at some point, it would be nice if I could make a script that would take the basename.301-med.avi.001 through basename.301-med.avi.025 and join that and repeat the process with basename.302-med.avi.001 through .025 until there are no more
basename.3*.avi.001 files...
When I tried to make such a script in bash I couldn't come up with anything that wouldn't just mess it up. there is up till basename.320*

---

### Post by Vaphell on 2012-02-12
try
```
for i in 301 302; do cat basename.${i}-med.avi.{001..025} > complete-basename.${i}-med.avi; done
```

---

### Post by ThaDoctor99 on 2012-02-12
It is a whole season of films that somebody put up in split files... 
so from 1 - 20 (macgyver if anybody cares).
And I feel it to be tedious and error prone to type in a lot of commands I could probably use the last advice just with 301 302 -> 320 :D better than typing the commands multiple times.

---

### Post by Vaphell on 2012-02-12
so use ```
for i in {301..320}
``` to generate 301-320 range

you can use up arrow to get last commands and you can modify them

!! = last command

highlight select + middleclick paste in terminal is a foolproof way to follow command sequences posted on the net, you don't have to type anything

tab key can be used in terminal for autocompletion to reduce the number of typos (file, folder and command names)

---

### Post by Mark Phelps on 2012-02-13
If you just want to rejoin the pieces into a single file, then look around for hjsplit.  There is a java version of it you can run in Linux.

---

### Post by HiImTye on 2012-02-13
you can piece them together in Pitivi, if you don't feel comfortable using the CLI, just remember that you don't want to 'save' the project you want to 'render' your project

---

### Post by ThaDoctor99 on 2012-02-13
I feel more comfortable in the CLI than a lot of fancy graphics.
I just looked for a way to script this as to automate.

---

### Post by HiImTye on 2012-02-13
I understand, then a for loop is the best option

---

### Post by ThaDoctor99 on 2012-02-13
I would agree if I could make my computer understand that it is not acceptable that it gives me a file that is 4.0 KB when I know it is supposed to be 350MB (the usual size for tv episodes in the 40 minutes range..)

---

### Post by ThaDoctor99 on 2012-02-13
I suppose I got it working with a little more tricking... So now I will add that to my extraction collection, should make a script for this at some point :D

---

