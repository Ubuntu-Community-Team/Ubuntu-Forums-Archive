---
title: "command line weirdness."
date: 2010-09-08
forum: General Help
---

### Post by Coder68 on 2010-09-08
I am using the worlds crappiest book for Ubuntu. (Forced by the school) Beginner friendly book my rearend! ](*,)

The book does not go into anything about this, (Same with many of the questions at the end of chapters.) but it asks the following question at the end of the chapter, that I am unable to figure out the answer to.

Suppose you have a file named [COLOR=Red]andor[/COLOR].  What error do you get when you run the following command. (The error is not the part I am having an issue with.)

> mv andor and\/or No that is not  V it is \   / without the spaces. 

I get a no such file or directory error. OK so far. 

There is no explanation of what the trailing \ means. (I think it represents a space??) 
There is no explanation for what the leading slash means when it is not part of a path. 

Now for the part I can't figure out.

Under what circumstances is it possible to run the command without producing an error? (Implying it is possible.)

I thought that maybe it was looking for the folder /or so I made that folder under the root dir... /or - same error. Used sudo - same error. 

I can't find any way to make this work.

Can anyone help me? (Besides lighter fluid and a book of matches!)
If so, please explain what it is doing and what the \ and / means in this context.

Thank you,

C68

---

### Post by alphacrucis2 on 2010-09-08
> **Coder68 said:**
> I am using the worlds crappiest book for Ubuntu. (Forced by the school) Beginner friendly book my rearend! ](*,)

The book does not go into anything about this, (Same with many of the questions at the end of chapters.) but it asks the following question at the end of the chapter, that I am unable to figure out the answer to.

Suppose you have a file named [COLOR=Red]andor[/COLOR].  What error do you get when you run the following command. (The error is not the part I am having an issue with.)

 No that is not  V it is \   / without the spaces. 

I get a no such file or directory error. OK so far. 

There is no explanation of what the trailing \ means. (I think it represents a space??) 
There is no explanation for what the leading slash means when it is not part of a path. 

Now for the part I can't figure out.

Under what circumstances is it possible to run the command without producing an error? (Implying it is possible.)

I thought that maybe it was looking for the folder /or so I made that folder under the root dir... /or - same error. Used sudo - same error. 

I can't find any way to make this work.

Can anyone help me? (Besides lighter fluid and a book of matches!)
If so, please explain what it is doing and what the \ and / means in this context.

Thank you,

C68

I believe what you are dealing with is known as a "regular expression" 

[http://en.wikipedia.org/wiki/Regular_expression]("http://en.wikipedia.org/wiki/Regular_expression")


[http://www.regular-expressions.info/reference.html]("http://www.regular-expressions.info/reference.html")

---

### Post by wojox on 2010-09-08
Suppose that the working directory contains a single file named andor.
What error message do you get when you run the following command
line?
$ mv andor and\/or
Under what circumstances is it possible to run the command without
producing an error?
$ mv andor and\/or
mv: rename andor to and/or: No such file or directory
$ mkdir and
$ mv andor and\/or
$ ls and
or
The backslash is superfluous.

---

### Post by anubhavrocks on 2010-09-08
Back slash is the escape character.
Read this:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html](http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_03_03.html)

---

### Post by Coder68 on 2010-09-09
> **wojox said:**
> Suppose that the working directory contains a single file named andor.
What error message do you get when you run the following command
line?
$ mv andor and\/or
Under what circumstances is it possible to run the command without
producing an error?
$ mv andor and\/or
mv: rename andor to and/or: No such file or directory
$ mkdir and
$ mv andor and\/or
$ ls and
or
The backslash is superfluous.

Thank you,

So the /or told mv to rename **andor** to **or** in the **and** dir which was in the current working dir. This seems to only be useful if you have a current dir named **and**. (In this case.)

The \ seems essential. Without it, I get an error of permission denied.  Is this because it sees /or as a folder in the root dir without the \ at the end of and?

Thanks.

C68

---

### Post by gmargo on 2010-09-09
> **Coder68 said:**
> The \ seems essential. Without it, I get an error of permission denied.  Is this because it sees /or as a folder in the root dir without the \ at the end of and?

The backslash is not essential and is ignored in this case because the forward slash does not need escaping; it is interpreted by the shell and not passed on to the **mv** command, which you can see from **mv**'s error message.

Seems like a poor question for a text book.  Are they trying to teach that the destination directory must exist first?  Or something about unneeded escaping?  Or that filenames cannot contain slashes?

Here's a contrived example of when you do need a backslash:  Suppose you want to change a file's name to "foo bar" (with a space in it.)  Then you do:
```

mv andor foo\ bar

```Without the backslash, the **mv** command receives three arguments, not two, and tries to move "andor" and "foo" into the "bar" directory.  With the backslash, the space is embedded in the second argument to **mv** and the "andor" file is renamed to "foo bar".

---

