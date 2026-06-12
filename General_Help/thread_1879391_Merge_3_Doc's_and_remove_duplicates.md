---
title: "Merge 3 Doc's and remove duplicates"
date: 2011-11-11
forum: General Help
---

### Post by KLStringer on 2011-11-11
I have 3 text files with 4351, 6589, and 475 files names in them respectfully. I need to combine them into one text file and remove any duplicate file names. I've tried a couple different ways in Windows/Excel but even though it would say that duplicates were removed their still there.

A co-worker said that I could use sed and awk to do this but doesn't remember how and I don't have any experience using either.

Can a kind soul walk me through how I would do this using sed & awk?

Thank You in advance for the lesson.

---

### Post by oldfred on 2011-11-11
I know very little about what you want to do, but saved this link to doing something similar with dpkg lists of apps to reinstall which are simple text files.

HowTo: Create a list of installed packages
Compare two lists: kdford post #70
[http://ubuntuforums.org/archive/index.php/t-261366.html](http://ubuntuforums.org/archive/index.php/t-261366.html)

---

### Post by KLStringer on 2011-11-11
Thank you for the link it looks promising but will have to wait till Monday before I can play around with it.

---

### Post by aeronutt on 2011-11-11
If you only need to do this once, something like the following set of commands might work:

cat file1 file2 file3 > newfile1
sort newfile1 > newfile2
uniq newfile2 > newfile3

The point being, commands cat, sort, and uniq are your friend in this case.

---

### Post by KLStringer on 2011-11-14
> **aeronutt said:**
> If you only need to do this once, something like the following set of commands might work:

cat file1 file2 file3 > newfile1
sort newfile1 > newfile2
uniq newfile2 > newfile3

The point being, commands cat, sort, and uniq are your friend in this case.


Just got time to work on this again and this is just what I was looking for quick & simple thank you.

---

