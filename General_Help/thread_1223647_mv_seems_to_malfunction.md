---
title: "mv seems to malfunction"
date: 2009-07-26
forum: General Help
---

### Post by raywood on 2009-07-26
I'm using 64-bit Ubuntu 9.04.  I am learning to write scripts.  I have a script called x.  It is giving me problems, as follows:

1.  I type "chmod 777 x".  No error messages.  I then type "x".  I get "bash: x: command not found".  But then, in Nautilus (or xfe), when I double-click on x, it runs.  Why won't it run from the command line?

2.  The purpose of x is to move a file from one folder to another.  It reads as follows:

```
#!/bin/sh
mv -iv /folder1/testfile.txt /folder2/
```

When I double-click on x, it works.  Testfile.txt is now in folder2.  But if I make another copy of textfile.txt in folder1 and run x again, the interactive (-i) mode does not work; instead, x automatically creates an unnamed copy of testfile.txt in folder2 -- but this copy is shown as an executable rather than a text file.  I have also tried this with --interactive instead of -i; same result either way.

3.  If I repeat those steps another time (i.e., put a copy of testfile.txt in folder1 and double-click on x again), the interactive mode does function.  At the prompt, I get this message:

```
mv: overwrite `/folder2/\r'?
```

That is, it appears to be asking me if I want to rename folder2 to be called textfile.txt instead.

4.  If I type "y" at that prompt, nothing happens.  No file or folder is renamed.  Terminal hangs.  The cursor just blinks at me.  I blink back.  It blinks again.  We can't go on like this.

5.  If I then click on the upper-right corner of the Terminal box to close down this hung session, all of my open Terminal sessions are closed, as is xfe.

There seem to be multiple departures, here, from what is supposed to happen.  Any ideas why?

---

### Post by wojox on 2009-07-26
Ok 

1.To run in the terminal you need ./x

2. Linux is case sensitive so stop creating the same file mutiple times.

3. When you move a file or folder that already exists it will overwrite it.

---

### Post by raywood on 2009-07-26
***1.To run in the terminal you need ./x***

Right.  Thanks for that.

***2. Linux is case sensitive so stop creating the same file mutiple times.***

This doesn't seem to address my question.

***3. When you move a file or folder that already exists it will overwrite it.***

But, as I say, it doesn't.

---

### Post by trwww on 2009-07-26
> **raywood said:**
> ```
mv: overwrite `/folder2/\r'?
```

It seems to me 2 and 3 are the same thing. Notice that '\r' at the end of the file/folder you're being prompted to overwrite?

I'm guessing that you've created your script on a windows box or something and didnt convert the file to unix based line endings.

So basically you're either not creating, moving, or replacing the file you think you are.

I wish I could pinpoint your exact problem but without being being at your terminal I cant.

For #1, the current directory isn't in bash's $PATH by default, so you have to provide a path to it (./x).

regards,

---

### Post by raywood on 2009-07-27
***I'm guessing that you've created your script on a windows box or something and didnt convert the file to unix based line endings.  So basically you're either not creating, moving, or replacing the file you think you are.***

Astute observation.  You are absolutely correct.  I created a batch file in DOS, using [commands developed in an Excel spreadsheet]("http://raywoodcockslatest.blogspot.com/2009/07/how-to-find-large-number-of-random.html").  I was testing a line from that batch file.  Just now, when I typed the line manually (though it looks the same), it worked.

Thanks!

---

### Post by t4thfavor on 2009-07-27
Excel is notorious for funky characters inside things copied out of it. I would just use a plain old text editor, If you need a good, easy, free one, for windows look for Notepad++ Its got highlighting of syntax, and it supports Unix line endings. Check it out, its mostly like the gedit editor on Ubuntu.

---

