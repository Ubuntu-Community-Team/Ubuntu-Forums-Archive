---
title: "Rar unexpected end"
date: 2012-02-09
forum: General Help
---

### Post by constantmin on 2012-02-09
Hello everyone!

I had a problem while trying to unrar a file. The error said 
"CRC failed- Unexpected end of archive".

I searched the forum and found a similar topic here
[http://ubuntuforums.org/showthread.php?t=1141933](http://ubuntuforums.org/showthread.php?t=1141933) 

but the solution posted there didn't work for me because the seperated files were already inside another rar.

Does anyone have a solution in mind?
Thanks in advance

---

### Post by Mark Phelps on 2012-02-09
OK ... as mentioned before in the previous thread ...

If the files end with .001, .002, ... .00n -- this is a file that was broken into pieces using hjsplit, and the pieces were then combined into a single archive file.

You have two steps to do, at least:
1) Extract all the pieces from the large archive file.  This will give you a bunch of little .nnn files
2) Use hjsplit to combine these into a single file

Don't be surprise, when you're done to get another .rar file.

Update: Also recall, that in cases where the original archive was password-protected, or the full archive is corrupted, you can also get this same error message.

Also, you may need to use "unrar" in Linux to do this.  You can install that from the Software Center.

---

### Post by constantmin on 2012-02-09
Yes, i have unrar. 
The problem is i tried to unrar the big file (your step one) 
and at this point i got the error, so i could not proceed with joining them.

I tend to believe that it was a problem with the files (missing or something) after all, because nothing else works..

---

### Post by Mark Phelps on 2012-02-10
Unfortunately, if unrar doesn't work, then it's likely that the archive is missing one of its parts, or one or more of the parts present is the wrong size -- neither of which you can fix.

---

### Post by constantmin on 2012-02-11
I think that this is the case, too... 
So, i just have to find the file from another source i guess..

Thanks for your help! :)

---

