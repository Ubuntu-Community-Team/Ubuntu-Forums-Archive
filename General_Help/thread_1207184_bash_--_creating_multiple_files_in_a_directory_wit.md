---
title: "bash -- creating multiple files in a directory with a single command?"
date: 2009-07-07
forum: General Help
---

### Post by ecmatter on 2009-07-07
I've been digging through man pages all evening, and not finding what I'm looking for...

I need to create 100 files with sequential file names (file_100, file_101, file_102, ... file_199) in a directory.  I've already written a script that does the job, but what I'm wondering is if there's a way to assign the sequential file names in a single command without using a script?  

Like this, but in a single line:

```

me@laptop:~$ cp ~/template.txt ~/dir/file_100
me@laptop:~$ cp ~/template.txt ~/dir/file_101
me@laptop:~$ cp ~/template.txt ~/dir/file_102

etc...

```It would seem to me that there *should* be some way to do this without manually assigning each file name and without a script, but I'm either looking in the wrong place, or making this far more difficult than it should be.  A shove in the right direction would be greatly appreciated.

---

### Post by lswb on 2009-07-07
Something like this
```

#!/bin/bash
for (( i=100;i<200;i++ )) do
cp whatever "file$i"
done

```

---

### Post by wojox on 2009-07-07
You can do anything with a for loop.

+1

---

### Post by synapsys on 2009-07-07
so... as one line....

```
for (( i=100;i<200;i++ )) do cp whatever "file$i"; done
```

---

### Post by ecmatter on 2009-07-07
Like I said, I've already written a script.  What I'm looking for is a way to do it without a script.  To find out if there's a way to automate assigning the file names at the command line.

---

### Post by ecmatter on 2009-07-07
> **synapsys said:**
> so... as one line....

```
for (( i=100;i<200;i++ )) do cp whatever "file$i"; done
```

That's what I'm looking for.

I had no idea that you could do that.

Thanks.

---

### Post by lswb on 2009-07-07
You can use the single line form like synapsis posted directly at the command prompt. There's lots of other ways to generate the numerical sequence, e.g. the 'seq' command. If you need a more generalized way and reuseable method it wouldn't be hard to write a script that took parameters for the common part of the file name and the sequence you wanted to use. Without getting into error checking and failure handling, something like this:

makefiles
```

#!/bin/bash
for (( i<$2; i<$3; i++ )) do touch "$1$i" ; done

```

Substitue the file creation method of your choice where I used "touch"

Then, for your original example, (after chmod +x and putting on your path) you would call it like:

makefiles file 100 200

---

### Post by ecmatter on 2009-07-08
Thank you, lswb and synapsys.  Your posts led me to what I was after...

```

for i in {100..199}; do cp ./template ./dir/file_$i; done

```

^That^ makes a lot more sense to me than the (( i=100;i<200;i++ )) bit from both of your responses.  I've only just started learning bash, so much of this is cart-before-horse.

thanks again!

---

### Post by synapsys on 2009-07-08
I guess it depends on whether you know any other programming languages as to which makes more sense.....

---

### Post by ecmatter on 2009-07-08
Yeah, I'm starting from scratch.

---

