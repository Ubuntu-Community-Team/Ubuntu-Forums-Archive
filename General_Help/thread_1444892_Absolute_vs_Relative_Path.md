---
title: "Absolute vs Relative Path"
date: 2010-04-01
forum: General Help
---

### Post by gatorguy on 2010-04-01
I'm taking a UNIX/Linux class and currently use Ubuntu Desktop and Server. Have a question about an assignment. Not trying to cheat, just want to better understand.

If you were to navigate via a command line shell, how do you display the absolute path? I think the pwd command would give me that information. When I enter that command it displays all the folders/directories back to the root from where I'm currently at. Hopefully I'm interpreting what absolute path is.

My next question is how do you display your relative path. Let me take a step back. What is relative path and I guess after I get that I also need to figure out how to display it to the screen.

The actual assignment has us creating a directory and then navigating to that particular directory and displaying both the absolute and relative path and piping it to a text file. I know how to navigate the file system and pipe output to text, I'm just not seeing any decent examples on how to display the relative and absolute path that you're in to the screen. 

Thanks for any assistance and helping me learn Linux,
Dan - aka Gatorguy

F.Y.I. - I did read over all the chapters the course offers for this section prior to posting. Unfortunately they don't actually give you any examples or even use the words "relative path" or "absolute path" in the book.

---

### Post by Chronon on 2010-04-01
Relative path is the path relative to the current working directory.  Absolute path is referenced from the root directory.

A path like ./Music/Fire.mp3 is a relative path.  So is ../tools/config.sh

---

### Post by gatorguy on 2010-04-01
Thanks for the quick reply! So would it be safe to say that the pwd command would show the absolute path of the directory I'm in? 

How do you display the relative path you're located in? I'm digging through all the Linux commands now trying to find one that will do this.

Thanks,
Dan - aka Gatorguy

** On a side note, are directories called directories or folders in Linux?

---

### Post by Chronon on 2010-04-01
Yes, pwd prints the absolute path of the current working directory.

The current directory's relative path is always simply ".".  Relative paths are used to describe where another location is relative to the current working directory.

I'm not sure if there's a preference.  I consider folder and directory to be interchangeable terms.

---

### Post by gatorguy on 2010-04-01
Thanks for the verification concerning the pwd command and absolute path. I guess at this point I'm just trying to figure out how to display the relative path to display and then will use that to pipe to a txt file. 

I tried using:

ls > relative.txt

But this doesn't give me the relative path. Do you know of a command I can type in at the shell that would output the relative path? I tried typing in a period at the command prompt based on your response below, but I'm assuming I'm being too literal with your reply.

Thanks,
Dan

---

### Post by Chronon on 2010-04-01
Given an absolute path you can try to generate a relative path by substituting . for the absolute path of the current working directory.  

```
chronon@desktop:~$ locate LengthScan1.eps                                                                  04/01/10  8:06 PM
/home/chronon/Documents/Dropbox/diss/figs/CavityLengthScan1.eps
/home/chronon/Documents/diss/figs/CavityLengthScan1.eps
/home/chronon/Plots/LengthScan1.eps
chronon@desktop:~$ pwd                                                                                     04/01/10  8:06 PM
/home/chronon

```
So, the relative paths to those files are:
```
./Documents/Dropbox/diss/figs/CavityLengthScan1.eps
./Documents/diss/figs/CavityLengthScan1.eps
./Plots/LengthScan1.eps
```

You can find relative paths to locations that have the same parent directory as the current working directory too, since ../ points to the parent directory.

---

### Post by km0r3 on 2010-04-01
> **gatorguy said:**
> I'm taking a UNIX/Linux class and currently use Ubuntu Desktop and Server. Have a question about an assignment. Not trying to cheat, just want to better understand.

If you were to navigate via a command line shell, how do you display the absolute path? I think the pwd command would give me that information. When I enter that command it displays all the folders/directories back to the root from where I'm currently at. Hopefully I'm interpreting what absolute path is.

My next question is how do you display your relative path. Let me take a step back. What is relative path and I guess after I get that I also need to figure out how to display it to the screen.

The actual assignment has us creating a directory and then navigating to that particular directory and displaying both the absolute and relative path and piping it to a text file. I know how to navigate the file system and pipe output to text, I'm just not seeing any decent examples on how to display the relative and absolute path that you're in to the screen. 

Thanks for any assistance and helping me learn Linux,
Dan - aka Gatorguy

F.Y.I. - I did read over all the chapters the course offers for this section prior to posting. Unfortunately they don't actually give you any examples or even use the words "relative path" or "absolute path" in the book.

Found some useful resources:

[http://en.wikipedia.org/wiki/Path_%28computing%29](http://en.wikipedia.org/wiki/Path_%28computing%29)
[http://linux.about.com/od/itl_guide/a/gdeitl29t01.htm](http://linux.about.com/od/itl_guide/a/gdeitl29t01.htm)
[http://www.linuxforums.org/forum/linux-programming-scripting/26969-absolute-vs-relative-pathing.html](http://www.linuxforums.org/forum/linux-programming-scripting/26969-absolute-vs-relative-pathing.html)

The Wikipedia article is really good.

---

### Post by gatorguy on 2010-04-02
Thanks for all the assistance. I understand the difference between the two (relative vs absolute paths), but was hoping their was a command similar to pwd that would display the relative path I was in from the command prompt. I was hoping to pipe the display results to text. So far I haven't seen a way and I'm not sure how to run that code that was provided. Still pretty new at Linux.

Thanks again for all the assistance,
Dan

---

### Post by kaibob on 2010-04-02
> **gatorguy said:**
> ...Do you know of a command I can type in at the shell that would output the relative path?
I don't know of a command that by itself will give the relative path. You could use parameter expansion, but that doesn't seem like a very good solution.

```
$ echo $PWD
/home/kaibob/documents

$ echo "${PWD##*/}"
documents

$ echo "./${PWD##*/}"
./documents
```

The Bash Reference Manual uses the term directory and never uses the term folder. So, I normally use the term directory.

---

### Post by irishbreakfast on 2010-04-02
I just did <apropos directory> and found dirname.
Do <man dirname> and have a read.

---

### Post by lisati on 2010-04-02
Before I got a machine with Windows preinstalled, I generally used the words "directory" and the related "subdirectory". These days I also use the word "folder" as well.

---

### Post by jobix on 2010-04-02
> **gatorguy said:**
>  
...
I tried using:

ls > relative.txt

But this doesn't give me the relative path. Do you know of a command I can type in at the shell that would output the relative path? I tried typing in a period at the command prompt based on your response below, but I'm assuming I'm being too literal with your reply.

Thanks,
Dan

The question doesn't make sense. A relative path is always relative to something. Without that "something", it's relatively futile to look for a relative path :)

An analogy would be: Relative to New York, the time in California is 3 hours behind. So you could say the relative time difference is 3 hours. But if you took out New York from the picture, then ask this question "what is the relative time in California?", it doesn't make sense. Relative time in California but relative to what?


Let's say you have this directory structure:

/home/user/dan/dir1/subdir1/file1
/home/user/dan/dir1/subdir2/file2
/home/user/dan/dir2/subdir1/file3
/home/user/dan/dir2/subdir2/file4

Also, for convenience sake, let us assume that file1, file2, file3, file4 are unique names. The following statements are true.

The absolute pathname of file2 is /home/user/dan/dir1/subdir2/file2.
The relative pathname of file2 relative to file1 is ../subdir2/file2.
The relative pathname of file2 relative to file3 is ../../dir1/subdir2/file2.
The relative pathname of file2 relative to file4 is ../../dir1/subdir2/file2.
The relative pathname of file4 relative to file2 is ../../dir2/subdir2/file4.

As you can see, the relative pathname of a file is different depending on what it is relative to.

Hope this helps.

---

### Post by kaibob on 2010-04-02
The following is from the Ubuntu Documentation: 

> A relative path name is one that doesn't start with /; in that case, the directory tree is traversed starting from a given point, which changes depending on context, called the current directory. In every directory, there are two special directories called . and .., which refer respectively to the directory itself, and to its parent directory. <snip>

**Examples**

An absolute path name, pointing to what is normally an executable file on an Ubuntu system:

/usr/bin/test

An absolute path name, but pointing to a directory instead of a regular file:

/usr/bin/

A relative path name, which will point to /usr/bin/test only if the current directory is /usr/:

bin/test

A relative path name, which will point to /usr/bin/test if the current directory is any directory in /usr/, for instance /usr/share/:

../bin/test

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

So, in retrospect, I agree with jobix that the OP has not provided the from-to information necessary to answer his question.

---

