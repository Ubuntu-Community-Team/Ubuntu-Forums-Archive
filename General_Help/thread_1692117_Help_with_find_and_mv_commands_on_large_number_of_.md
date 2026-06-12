---
title: "Help with find and mv commands on large number of files please?"
date: 2011-02-20
forum: General Help
---

### Post by tnc on 2011-02-20
Hello and Thanks for looking...

We recovered a large number of files from a HD I messed up.  I am attempting to move large numbers of files of a type e.g. .txt  .jpg , into a folder by type to more easily sort through them.  After much reading and experimenting I am finally at a loss.

Here are the commands I have mainly been trying with various edits:

```
sudo find -name "*.txt" -print0 -execdir mv {} /home/tnc/recovered/recoveredtxts
```

```
sudo find -name "*.txt" -print0 | xargs --null mv /home/tnc/recovered/recoveredtxts
```


So far the most common complaint I have gotten "missing arguments to execdir".  
I be stumped.

This is on Ubuntu 10.04
 

Thank-you for your time!
Tim

---

### Post by CHRSB on 2011-02-20
I think you have to tell the find command when to stop? Try a \; at the end.

[http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)
> 
The -exec is an action flag, which says "we want to execute a command"; the command follows it, and is terminated by a semicolon (;).   Now, the semicolon is also a special character for the shell, so we  have to protect it with a backslash, just as we did for the parentheses  earlier.  And once again, we could have used quotes around it instead;  the backslash is one character less, so it's the traditional preference.  [http://ubuntuforums.org/showthread.php?p=8767162](http://ubuntuforums.org/showthread.php?p=8767162)

---

### Post by tnc on 2011-02-21
CHRSB:

Thank-you for your response!

The paragraph you posted was pretty much the piece I was missing.  Maybe been staring at the screen to long?  

Here is the final command that worked:

```
sudo find /home/tnc/recovered -name "*.jpg" -type f -print0 -execdir mv -f {} /home/tnc/recoveredjpegs \;

```

Thank-you muchly!
Tim

---

### Post by asmoore82 on 2011-02-21
The proper `xargs` style way would have been this:
```
find */some/dir* -iname "*.jpg" -print0 | xargs -0 mv -t */some/pictures*
```

You have to use `-t` to tell `mv` that the target directory to move files
into is being given first, followed by all the filenames to move. This is
a GNU extension to `mv` so the pure `find … -exec` method is more portable.

---

### Post by tnc on 2011-02-21
Thanks for that.  

The -t makes sense but what tells xargs what the filenames are?  Or is it just accepting the pipe input as such?
And, naturally, what is the difference between -name and -iname?

Cool stuff!
Tim

---

### Post by asmoore82 on 2011-02-21
Yes, `xargs` receives the filenames from the pipe.
`-print0` to `find` and `-0` to `xargs` pair them up nicely to
exchange the filenames in a special null-delimited format.

`-iname` is the case insensitive search :D.

---

### Post by tnc on 2011-02-21
Hey, Thanks for that!  Good info.

Tim

---

