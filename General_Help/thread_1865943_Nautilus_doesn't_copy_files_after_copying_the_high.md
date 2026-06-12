---
title: "Nautilus doesn't copy files after copying the highlighted name of a file"
date: 2011-10-20
forum: General Help
---

### Post by almariado on 2011-10-20
Hi to everyone
I've come across an odd problem in nautilus in ubuntu 11.10.

When renaming a file or directory you highlight it's name and then copy it, after that you're no longer able to copy/paste files.
You have to close nautilus and open it again to copy/paste files once more.

Has someone else experienced this problem?
Any solutions/suggestions?

Cheers!

---

### Post by dcstar on 2011-10-21
> **almariado said:**
> Hi to everyone
I've come across an odd problem in nautilus in ubuntu 11.10.

**When renaming a file or directory you highlight it's name and then copy it**, after that you're no longer able to copy/paste files.
You have to close nautilus and open it again to copy/paste files once more.


No you don't, "Renaming" has nothing to do with Copying, they are two totally different functions.

Copy/Paste works fine on my test 11.10 system.

---

### Post by almariado on 2011-10-21
Thanks for your answer.

Maybe I didn't explain correctly, English isn't my first language.

To repeat this behavior do this in Nautilus in List View:
- Right click a file in Nautilus and chose Rename. Nautilus will highlight the file name (except the extension)
- Now Right click again on the highlighted part of the name and chose Copy.
- Press Esc
- Now try copying a file, you will be able to chose the option "Copy", but when you try to Paste, nothing happens.

I did some more testing after my first post and I found out that this behavior only occurs in "List View", if you chose "Compact" or "Icon" view, it will work fine.

I think it has something to do with a previous bug nautilus had in list view too, when renamaming a file Nautilus would automatically highlight the whole name, even the extension:
[http://ubuntuforums.org/showthread.php?t=1618015](http://ubuntuforums.org/showthread.php?t=1618015)
There was even a bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+s...us/+bug/658555](https://bugs.launchpad.net/ubuntu/+s...us/+bug/658555)

They finally corrected that, but a new bug appeared. Bummer! :(
 
I better report this bug on launchpad 

Again, thanks for your answer mate.
Cheers!

---

