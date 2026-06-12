---
title: "how to remove file ?"
date: 2012-10-04
forum: General Help
---

### Post by winzip on 2012-10-04
I'm using  rm -r  /home/user/myfolder/*   to remove  files




I  want to  exclude  one specific file   ** abc.xml**  from removal  .

 rm -r  /home/user/myfolder/*  -x abc.xml   // Is this a correct command ?

---

### Post by drmrgd on 2012-10-04
Have a look at the man pages for rm.  There is no -x option for rm.  As far as I know there is no exclude option, and you would have to manually deselect a file from deletion.

---

### Post by winzip on 2012-10-04
> **drmrgd said:**
> Have a look at the man pages for rm.  There is no -x option for rm.  As far as I know there is no exclude option, and you would have to manually [COLOR=Red]**deselect a file**[/COLOR] from deletion.

only command line. I can not use GUI.

I am using Ubuntu 10 Server OS.

Can you suggest a command line workaround ?

---

### Post by drmrgd on 2012-10-04
No, I understand.  Deselect is not a GUI command only.  I mean you'll have to manually choose what not do delete.  As one example, you could use the find command with the '-exec rm' argument.  Something like this:

```
touch file{1,2,3,4,5,6,7,8,9}.txt
$ ls
file1.txt  file2.txt  file3.txt  file4.txt  file5.txt  file6.txt  file7.txt  file8.txt  file9.txt
$ find . -type f ! -name "file1.txt" -exec echo rm {} \;
rm ./file4.txt
rm ./file7.txt
rm ./file8.txt
rm ./file5.txt
rm ./file9.txt
rm ./file3.txt
rm ./file6.txt
rm ./file2.txt

```

This will delete all the "file*.txt" files that I made except file1.txt (the "! -name file1.txt" part of the line).  Note that I preceded rm with 'echo' just to have it output what it will delete in order to verify that it works correctly.  If I'm satisfied that it's working OK, I can just remove the "echo" part in order to have it actually execute.

---

### Post by steeldriver on 2012-10-04
or have a look at extended shell globbing (extglob), something like

```
rm !(abc.html)
```

---

### Post by drmrgd on 2012-10-04
> **steeldriver said:**
> or have a look at extended shell globbing (extglob), something like

```
rm !(abc.html)
```

Nice one!  I totally forgot extglob.  That's a heck of a lot less typing!

---

### Post by winzip on 2012-10-04
> **drmrgd said:**
> Nice one!  I totally forgot [COLOR=Red]**extglob**[/COLOR].  That's a heck of a lot less typing!

Do I need to install anything to avail this feature ?

Or  its available in ubuntu 10 server OS ?





I guess in that case  my command will be like this ...

rm -r  /home/user/myfolder/*  !( abc.xml)

right  ?

---

### Post by drmrgd on 2012-10-04
I believe that should be part of the shell by default.  Also, it looks like the command is correct if you want to recursively delete everything from /home/user/myfolder/ except for abc.xml.  You can always dry run test the rm command by putting "echo" in front of it just to be sure you don't accidentally delete something you didn't intend to:

```
echo rm -r /home/user/myfolder/* !(abc.xml)
```

---

### Post by steeldriver on 2012-10-04
^^^ I think that would delete everything - and *then* try to *not* delete 'abc.html'  (they are separate patterns to rm)

I'm not sure that globbing is going to work for you in a **recursive** delete - if you had **a file 'abc.html' in the top level 'myfolder'** that you wanted to exclude from the delete then the command would simply be

```
rm -r /home/user/myfolder/!(abc.html)
```i.e. you just replace the '*' (everything) glob with a more specific '!(abc.html)' (everything except 'abc.html')

However if 'abc.html' is somewhere else in the hierarchy then you will probably need to use 'find' (because 'rm -r' will delete the containing directory even if it is non-empty)

AFAIK the extglob option is enabled by default (at least in the interactive shell - you may need to enable it with shopt if you are doing it in a script - I don't know)

---

### Post by drmrgd on 2012-10-04
> **steeldriver said:**
> ^^^ I think that would delete everything - and *then* try to *not* delete 'abc.html'  (they are separate patterns to rm)

I'm not sure that globbing is going to work for you in a **recursive** delete - if you had **a file 'abc.html' in the top level 'myfolder'** that you wanted to exclude from the delete then the command would simply be

```
rm -r /home/user/myfolder/!(abc.html)
```i.e. you just replace the '*' (everything) glob with a more specific '!(abc.html)' (everything except 'abc.html')

However if 'abc.html' is somewhere else in the hierarchy then you will probably need to use 'find' (because 'rm -r' will delete the containing directory even if it is non-empty)

AFAIK the extglob option is enabled by default (at least in the interactive shell - you may need to enable it with shopt if you are doing it in a script - I don't know)

Hmmm...good catch.  I wasn't sure how that worked exactly.

This is exactly why I *ALWAYS* echo a batch rm command before committing!  I think that's a lesson you (hopefully!) only need to learn once.

---

### Post by steeldriver on 2012-10-04
Actually after playing around a little, it looks like it might work if you combine it with the 'globstar' pattern - for example if I have

```
$ ls -R myfolder/
myfolder/:
abc.html  subfolder1  subfolder2  subfolder3

myfolder/subfolder1:
abc.html  pqr.html  xyz.html

myfolder/subfolder2:
abc.html  pqr.html  xyz.html

myfolder/subfolder3:
abc.html  pqr.html  xyz.html

```then

```
$ rm /home/steeldriver/myfolder/**/!(abc.html)
```leaves

```
$ ls -R myfolder/
myfolder/:
abc.html  subfolder1  subfolder2  subfolder3

myfolder/subfolder1:
abc.html

myfolder/subfolder2:
abc.html

myfolder/subfolder3:
abc.html
```Who knew, huh?

---

### Post by winzip on 2012-10-04
it does not  remove files from other subfolders if there is no abc.xml .

---

### Post by winzip on 2012-10-06
> **winzip said:**
> it does not  remove files from other subfolders if there is no abc.xml .
comments please.

---

### Post by drmrgd on 2012-10-06
Perhaps we are not understanding what you are trying to do correctly.  Steeldriver's globstar method works quite nicely in a test environment for me:

```
tree testrm1
testrm1
&#9500;&#9472;&#9472; abc.html
&#9500;&#9472;&#9472; game2.nes
&#9500;&#9472;&#9472; game3.nes
&#9500;&#9472;&#9472; game4.nes
&#9500;&#9472;&#9472; game5.nes
&#9500;&#9472;&#9472; subfolder1
&#9474;** &#9500;&#9472;&#9472; abc.html
&#9474;** &#9500;&#9472;&#9472; file1.txt
&#9474;** &#9500;&#9472;&#9472; file2.txt
&#9474;** &#9500;&#9472;&#9472; file3.txt
&#9474;** &#9500;&#9472;&#9472; file4.txt
&#9474;** &#9492;&#9472;&#9472; file5.txt
&#9500;&#9472;&#9472; subfolder2
&#9474;** &#9500;&#9472;&#9472; file1.txt
&#9474;** &#9500;&#9472;&#9472; file2.txt
&#9474;** &#9500;&#9472;&#9472; file3.txt
&#9474;** &#9500;&#9472;&#9472; file4.txt
&#9474;** &#9492;&#9472;&#9472; file5.txt
&#9500;&#9472;&#9472; subfolder3
&#9474;** &#9500;&#9472;&#9472; file1.txt
&#9474;** &#9500;&#9472;&#9472; file2.txt
&#9474;** &#9500;&#9472;&#9472; file3.txt
&#9474;** &#9500;&#9472;&#9472; file4.txt
&#9474;** &#9492;&#9472;&#9472; file5.txt
&#9492;&#9472;&#9472; subfolder4
    &#9500;&#9472;&#9472; file1.txt
    &#9500;&#9472;&#9472; file2.txt
    &#9500;&#9472;&#9472; file3.txt
    &#9500;&#9472;&#9472; file4.txt
    &#9492;&#9472;&#9472; file5.txt
```

This is the structure I created, which I think is similar to what you have if I understand you.  Using Steeldriver's globstar method (just echoing what I would delete for now)

```
echo rm testrm/**/!(abc.html)
rm testrm/subfolder1/file1.txt testrm/subfolder1/file2.txt testrm/subfolder1/file3.txt testrm/subfolder1/file4.txt testrm/subfolder1/file5.txt testrm/subfolder2/file1.txt testrm/subfolder2/file2.txt testrm/subfolder2/file3.txt testrm/subfolder2/file4.txt testrm/subfolder2/file5.txt testrm/subfolder3/file1.txt testrm/subfolder3/file2.txt testrm/subfolder3/file3.txt testrm/subfolder3/file4.txt testrm/subfolder3/file5.txt testrm/subfolder4/file1.txt testrm/subfolder4/file2.txt testrm/subfolder4/file3.txt testrm/subfolder4/file4.txt testrm/subfolder4/file5.txt
```

Also making sure that I'm not deleting 'abc.html' with that command (again, in tree structure):

```
tree testrm
testrm
&#9500;&#9472;&#9472; abc.html
&#9500;&#9472;&#9472; game2.nes
&#9500;&#9472;&#9472; game3.nes
&#9500;&#9472;&#9472; game4.nes
&#9500;&#9472;&#9472; game5.nes
&#9500;&#9472;&#9472; subfolder1
&#9474;** &#9492;&#9472;&#9472; abc.html
&#9500;&#9472;&#9472; subfolder2
&#9500;&#9472;&#9472; subfolder3
&#9492;&#9472;&#9472; subfolder4

```

The code deleted everything from the subfolders except for the 'abc.html' file. Note that it did not remove the files from testrm as the code is just looking through the subdirectories of testrm for stuff to delete.  

Is your directory structure significantly different from what we have?  Perhaps an example of how your directory structure is set up would help.

---

