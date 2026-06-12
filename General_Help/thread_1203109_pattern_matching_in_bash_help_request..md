---
title: "pattern matching in bash help request."
date: 2009-07-02
forum: General Help
---

### Post by Coder68 on 2009-07-02
I am working my way thorugh a couple of books on using the command line in Linux.  I keep finding errors in these books. :frown:

Anyway, I am only in the early stages here so please be kind!

I did a search, but I did not find what I was looking for.

Right now I am going through a book on Bash.... and here is my issue with what the book has.

I have these files in a folder
file1 file2 File3 Amy.txt Fred.txt amy.txt fred.txt

If I do a search for f* I get as expected
file1 file2 fred.txt

Now the book says to search for uppercase wildcards do
echo [A-Z]*
and I should get File3 Fred.txt (Per the book)

But I get all the files except for amy.txt

Why is this not working?

Thanks!

C68

---

### Post by Jebtrix on 2009-07-02
Wait, so your getting file1 file2 as a result also?

---

### Post by kaibob on 2009-07-03
I think this thread explains things:

[http://ubuntuforums.org/showthread.php?t=890525](http://ubuntuforums.org/showthread.php?t=890525)

For example,

> $ touch bob Bob jane Jane joe Joe
$ echo [A-Z]*
bob Bob jane Jane joe Joe
$ export LC_ALL=C ; echo [A-Z]*
Bob Jane Joe

---

### Post by Coder68 on 2009-07-03
Thanks Kiabob!

I did add the code to the bottom of my .bashrc file (After making a backup!) and it works.

I tested this inline and it works, but only for that time. That is why I added it to my .bashrc file.

C68

---

