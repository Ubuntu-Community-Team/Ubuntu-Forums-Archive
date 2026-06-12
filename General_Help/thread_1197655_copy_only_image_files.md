---
title: "copy only image files?"
date: 2009-06-26
forum: General Help
---

### Post by googlegot on 2009-06-26
I need to copy all the images (specifically jpgs) out of a couple thousand folders into a single folder.  Is there a simple way to do this, or am I stuck sifting through every single folder for images?

---

### Post by rushikesh988 on 2009-06-26
I think you should use the Image browser like picasa to do this ....I think F spot photo viewer also does it  (sure)

---

### Post by Tyke91 on 2009-06-26
```
for file in `find /this/is/where/you/search -iname *.jpg` ; do cp $file /this/is/your/destination; done
```^_^

No installing programs, no fancy formats or anything. Get your computer to sift though all the thousands of folders for you

all you need for this operation is bash :D

(If you wanna see visual feedback, i suggest putting a -v tag after cp. so it would be do cp -v $file /destination )

PS: Copy paste it. those aren't single quotes, they're tilde marks (`)... it will work better if you just c/p it instead of writing it yourself.

PSS: for more help in understanding basic commands, look @ my sig.

---

### Post by googlegot on 2009-06-26
unfortunately that command does not copy anything to the destination folder, I need to copy from /media/disk and all subdirectories to /media/stuff/stuff

when i run the command, it does not copy a thing

---

### Post by Tyke91 on 2009-06-26
odd... works for me just fine. 

please paste the output of
```
for file in `find /media/disk -iname *.jpg` ; do echo $file | less; done
```have you created the folder /media/stuff/stuff ? It needs to exist before anything else happens

```
mkdir /media/stuff/stuff
```and try the code again. IF it works


your stuff might be saved as jpeg, in which case just add that e to the code instead.

---

### Post by googlegot on 2009-06-26
that command is not creating a file to post actually, I think there is something very wrong in what im doing, let me check if the directories i have listed exist...

they definately do, but still nothing is being copied

---

### Post by Tyke91 on 2009-06-26
> **googlegot said:**
> that command is not creating a file to post actually, I think there is something very wrong in what im doing, let me check if the directories i have listed exist...

they definately do, but still nothing is being copied

errm... explain to me exactly what you are putting in. are you copy/pasting or are you typing? This command only finds files that end in .jpg (regardless of case) so if you had .jpeg you would have to put an e in there.

---

### Post by geirha on 2009-06-26
This (run in a terminal) should list all jpegs under /media/disk
```
find /media/disk -iname "*.jpg"
```

And this should copy them to /media/stuff/stuff
```
find /media/disk -iname "*.jpg" -print0 | xargs -0 -- cp --backup=numbered -v -t /media/stuff/stuff
```

The above should be completely safe with regards to paths containing whitespace. The reason Tyke91's command doesn't work for you, may be that it encounters paths with spaces, or it may be due to not quoting the argument to -iname, which will make it fail if there are jpegs in the current working directory.

EDIT: Sorry, made a mistake myself earlier. Fixed it now.

---

### Post by Tyke91 on 2009-06-26
ah, i hadn't thought of that!

I tend not to put whitespace in my file names :)

EDIT: you might wanna do 
```
find /media/disk -iname "*.jpg" | less
```and then hit control + c to kill it when you know it works. otherwise you might be waiting for a while


EDIT: Just tested on my machine, the find script handles whitespace and files in the root directory just fine...

---

