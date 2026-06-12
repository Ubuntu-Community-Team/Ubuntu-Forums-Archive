---
title: "Help with cp command in script please"
date: 2010-03-04
forum: General Help
---

### Post by GuiGuy on 2010-03-04
The following works when I execute it from a command line (shell):
> cp -anv "/mnt/Music/BB King - (1995) Lucille & Friends [320]/13 - Hummingbird.mp3" /media/myusbdrive/

But I'd like to run it from a shell script. However that gives me an error with brackets, ie "(1995)" will cause a fail.

Renaming the files is not practical.

Is there a delimiter of some kind that I should be using around the "("?

TIA

---

### Post by gmargo on 2010-03-04
Is that really the command in the shell script?  Or is it just what you think is happening (because of a loop or wildcard expansion or something)?  If that string is verbatim in the script, it should work.  (If not, try a) single quotes, b) #!/bin/bash instead of #!/bin/sh.)  Is the -n option preventing an overwrite?

---

### Post by Girya on 2010-03-04
a \ will escape the ()'s. When I copied and pasted the file name to experiment with it pasted into the cmd line with lots of whitespaces. Those will cause you all kinds of trouble unless you escape them also. If I was doing what you are trying to do I'd write a script to rename the files without whitespaces and ()'s  

something like this might work: (test it on a copy first) 

```
find . -name "*.mp3" -exec rename 's/ //g' {} \; && find . -name "*.mp3" -exec rename 's/\(//g' {} \; && find . -name "*.mp3" -exec rename 's/\)//g' {} \;
```

somebody else could probably clean up my ugly code a lot.

---

### Post by GuiGuy on 2010-03-04
> **Girya said:**
> a \ will escape the ()'s. 


Many thanks. That's fixed it.

---

### Post by GuiGuy on 2010-03-04
> **gmargo said:**
> Is that really the command in the shell script? 

Yes. I have converted a music playlist to copy files to a flash drive. The \ escape before (as pointed out in Girya's post fixes it nicely.

Thanks

---

