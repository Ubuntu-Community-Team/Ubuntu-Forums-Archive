---
title: "Cannot erase file with bad filename"
date: 2010-01-20
forum: General Help
---

### Post by ofir_k on 2010-01-20
I downloaded a zip file which contained a file with a bad filename, like this (I didn't notice it, only after extract):
&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;!

I extracted it and then, when I wanted to delete it I got "File doesn't exits".
Because of the bad filename, I can't copy, move, rename the file.
I also tried to Shift+Del the entire folder but with no success.

I use kubuntu and working with dolphin.

Is there a way of handling such files?

---

### Post by bsaber on 2010-01-20
You can see the file from Dolphin but can't remove it? Have you tried removing it from the command line?

Assuming you only have one zip in the directory, you could do rm *.zip from the command line. That might work.

---

### Post by ofir_k on 2010-01-20
The file is a text file which was extracted from a zip file...

Now I have the following structure:
SomeDir
- &#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;!.txt

Trying to delete with Dolphin fails with an error message "File doesn't exists".


I managed to delete the file by browsing with Dolphin to SomeDir and issuing bsaber's command:
> rm *.txt

Thanks for your help!

I reported a bug:
[https://bugs.edge.launchpad.net/ubuntu/+source/dolphin/+bug/510018](https://bugs.edge.launchpad.net/ubuntu/+source/dolphin/+bug/510018)

---

### Post by bsaber on 2010-01-20
Glad it helped. :D

---

### Post by jamesisin on 2010-01-20
Using a wildcard (*) can be so dangerous.  I wonder if it would have worked to just ls on the directory and then use tab completion to get the exact file name (or some similar method).

---

### Post by llamabr on 2010-01-20
> **jamesisin said:**
> Using a wildcard (*) can be so dangerous.  I wonder if it would have worked to just ls on the directory and then use tab completion to get the exact file name (or some similar method).

true.  rm comes with the -i (interactive) flag set to on by default, in ubuntu (thank you ubuntu for protecting me from myself).  That way, if there are more than one *txt it will ask you for each one.

thy ubuntu be done.

---

### Post by jamesisin on 2010-01-20
True.  I would still do the ls before so that I could satisfy myself I was looking at the correct file.

---

### Post by mhdbnoimi on 2011-01-26
> **ofir_k said:**
> I downloaded a zip file which contained a file with a bad filename, like this (I didn't notice it, only after extract):
&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;&#65533;&#65533;!

I extracted it and then, when I wanted to delete it I got "File doesn't exits".
Because of the bad filename, I can't copy, move, rename the file.
I also tried to Shift+Del the entire folder but with no success.

I use kubuntu and working with dolphin.

Is there a way of handling such files?

Ive same issue but instead of unrecognized files I've unrecognized folder as shown in [this post](http://kubuntuforums.net/forums/index.php?topic=3114470.0)

Do you know any way for removing that king of folders?

---

### Post by jamesisin on 2011-01-28
Have you tried using tab-completion as suggested above?

---

### Post by rubengs on 2011-10-02
I use this script to fix bad encoded file names: 

```
#!/bin/bash

#NTFS to UTF-8

if [ $# -gt 0 ];then

    convmv -f cp850 -t utf-8 -r --notest "$@"| zenity --progress --pulsate --text="conversion in progress" --auto-close

fi

exit 0

 

```

---

### Post by jamesisin on 2011-10-02
Can you break down what your script is doing?

---

### Post by nothingspecial on 2011-10-02
Thanks for the information :D

But please don't bump old threads to the top.

Closed.

---

### Post by nothingspecial on 2011-10-02
Ok, I suppose it's still active.

Opened :)

---

