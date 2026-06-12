---
title: "Change names of thousands of files"
date: 2011-08-26
forum: General Help
---

### Post by DeMus on 2011-08-26
Hi,
My wife and I just come back from a wonderful holiday. Now, after I placed the pictures on the computer, I found out many names are different from other names. I have no idea why my camera did this.
I have names like IMG_0123 and I have names like _MG_0124. With what code can I change the names starting with the underscore to a name starting with I so _MG_0124 becomes IMG_0124?
Who can help me please? Thank you.

---

### Post by decoherence on 2011-08-26
Before I tell you, be sure that your camera hasn't done this for good reason. For instance, is there a '_MG_1234' and a 'IMG_1234'? If so, running the command I'd suggest will overwrite the file named IMG_1234 with the file named _MG_1234. So first, check for files with the same number using the following command (after you cd in to the directory with the pictures of course)

ls | awk -F'MG_' '{print $2}' | sort | uniq -c | sort

This will print out a list showing the number of occurrences of a given number. Files that share the same number will appear at the bottom of the list, so if the last item on the list starts with the number 1, you are good to go. For example, if the last line looks like 

1 1234

I know that there is only one file that has 1234 in it. If, however I see

2 1234

I know that there is both a _MG_1234 and an IMG_1234 and the below command will overwrite the latter file. If this is the case, let me know and I can pull together a script that will work around it. If there are only a few, you can rename them manually.

With that out of the way, here is the command. Assuming all of your pictures are in one directory, cd to that directory and run

rename _MG IMG *

yes, all that work to run such a simple command. But you have to be careful with the shell ;)

---

### Post by DeMus on 2011-08-26
Thank you so much, but shouldn't it be ren _MG* IMG*?
Didn't you forget the star?
Just to make sure I understand it.

---

### Post by sisco311 on 2011-08-26
Try one of the GUI mass renaming tools like: gprename, purrr, gwenrename, krename, thunar...

---

### Post by coffeecat on 2011-08-26
... or Gthumb, which has a tidy renaming utility built-in and being an image editing app, you can look at the photos you are renaming.

**EDIT**: sorry, no, that's probably not going to work if you've got all your IMG_0123's mixed in with your _MG_0124's. Nevertheless, it's useful on occasion.

---

### Post by sisco311 on 2011-08-26
> **decoherence said:**
> rename _MG IMG *


In Ubuntu, rename is the Perl based rename command, your syntax will work with rename.ul ;)

@OP:
With the perl based rename you can try something like:
```
rename **-n** 's/_MG(.*)/IMG$1/' *
```

Invoked with the **-n** option will show what files would have been renamed. Remove **-n** to actually rename the files.

---

### Post by DeMus on 2011-08-26
Thank you all, I will try some of the suggestions to find out which works best for me.
Thank you again

---

### Post by decoherence on 2011-08-26
> **sisco311 said:**
> In Ubuntu, rename is the Perl based rename command, your syntax will work with rename.ul ;)

Ah, sorry. Tested on Fedora ;) Nice catch

---

