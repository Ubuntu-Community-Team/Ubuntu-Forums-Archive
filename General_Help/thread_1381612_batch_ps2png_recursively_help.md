---
title: "batch ps2png recursively help"
date: 2010-01-15
forum: General Help
---

### Post by Swift Wolf on 2010-01-15
Hi,
 
Is there a way to batch convert recursively using ps2png?
 
Thanks

---

### Post by lorsen on 2010-01-15
Can you be a bit more precise?

---

### Post by Swift Wolf on 2010-01-15
Ok

ps2png converts ps files to png.  It requires two arguments so to run it looks like this

ps2png foo.ps foo.png

where foo.ps is the input file and foo.png is the output file.  (In my case I want the filenames to be the same)

What I want to do is search recursively through my folders for all *.ps files and then run ps2png on them. 

I tried using find, but got no happiness. 

Thanks again

---

### Post by Portmanteaufu on 2010-01-15
Here's a bash script that will do it. Put this in a file and make it executable.

```

#!/bin/bash
for FILE in `find . -name '*.ps'`
do
        NEWFILE=`echo $FILE | sed 's/.ps$/.png/g'`
        ps2png $FILE $NEWFILE
done

```

Let me know if you need clarification.

---

### Post by Swift Wolf on 2010-01-18
Sorry that I have taken so long to reply.
 
Your solution worked perfectly.  Thank you for help.

---

