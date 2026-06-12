---
title: "Linux is all files . Is win too ?"
date: 2010-03-20
forum: General Help
---

### Post by denarced on 2010-03-20
I heard somewhere that it's true that everything in Linux is a file and we all know this is true. But then I heard that in Windows too, everything is a file, we just can't see that without doing some probing. Is this true ??

---

### Post by Zimmer on 2010-03-20
> **denarced said:**
> I heard somewhere that it's true that everything in Linux is a file and we all know this is true. But then I heard that in Windows too, everything is a file, we just can't see that without doing some probing. Is this true ??

You do not need to probe too far to see it in Windows, C:\Windows\system32
Which is why deleting files can have an adverse effect on the working of your computer :)

So, Erm.. yes...  Operating System and data, an electronic filing system, like a giant filing cabinet ( which IMHO is the way to visualise the computer and approach some sort of understanding as to how it all works...) 
[http://www.linuxnewbieguide.org/content/overview-chapters](http://www.linuxnewbieguide.org/content/overview-chapters)

---

### Post by prodigy_ on 2010-03-20
"Everything is a file" principle can't be applied to Windows. For a simple reason: "file" in this case is an abstraction layer, something that allows you to have (theoretically) universal I/O mechanics for everything. Because everything is also a stream of bytes, a stream of ASCII characters. (When a modern *NIX system tells you that it uses Unicode, it lies. Because yes, you get one more abstraction layer, but the OS doesn't even know what Unicode is, it knows only ASCII.)

In Windows, if you'll hack your way deep into the kernel, you may see a similar picture, but as a user (no matter what are your privileges) or as an ordinary program, you're locked out. A simple example: imagine that you have a fakeraid. *NIX will show you the member disks of the array as "files" in /dev. In Windows the driver won't even let you know that they exist.

---

### Post by denarced on 2010-03-20
> **prodigy_ said:**
> "Everything is a file" principle can't be applied to Windows. For a simple reason: "file" in this case is an abstraction layer, something that allows you to have (theoretically) universal I/O mechanics for everything. Because everything is also a stream of bytes, a stream of ASCII characters. (When a modern *NIX system tells you that it uses Unicode, it lies. Because yes, you get one more abstraction layer, but the OS doesn't even know what Unicode is, it knows only ASCII.)

In Windows, if you'll hack your way deep into the kernel, you may see a similar picture, but as a user (no matter what are your privileges) or as an ordinary program, you're locked out. A simple example: imagine that you have a fakeraid. *NIX will show you the member disks of the array as "files" in /dev. In Windows the driver won't even let you know that they exist.

Sounds logical.

---

### Post by Mark Phelps on 2010-03-20
> **denarced said:**
> I heard somewhere that it's true that everything in Linux is a file and we all know this is true. But then I heard that in Windows too, everything is a file, we just can't see that without doing some probing. Is this true ??

The expression I heard, when I was working in Unix, is that everything is "flat files".  This was most generally true because all the configuration stuff in Unix was contained in ASCII files that could be easily opened and changed with a text editor.

The same is most definitely NOT true in current MS Windows. In quite a few cases, you need an app of some kind to read the information stored in a data set in MS Windows.  You simply can't open them and changed them using a text editor.

But, yeah, basically every OS that is not embedded in firmware is essentially a set of "files".

---

