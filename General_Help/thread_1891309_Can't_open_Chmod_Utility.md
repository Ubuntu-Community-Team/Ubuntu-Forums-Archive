---
title: "Can't open Chmod Utility"
date: 2011-12-05
forum: General Help
---

### Post by Wiking on 2011-12-05
Hello, I'm trying to learn how to write shell scripts, in a tutorial on the net I was reading it said the following,

> Save your file, and then make sure that it's set executable. You can do this using the chmod utility, which changes a file's mode. 

However, when I click on Chmod Utility from the menu nothing opens, nothings runs, I also tried Alt+F2 typed Chmod, and still nothing will open.

How do I open Chmod? Can I open it in konsole?

---

### Post by killermist on 2011-12-05
chmod is a console command.

From a terminal, "chmod +x somefile.sh" should make the file executable.

[edit]
```
chmod --help
```
will get you the listing of chmod's options.

---

### Post by drmrgd on 2011-12-05
chmod is a terminal command.  You can check out the details by typing "man chmod"  so that you can learn how to use it.

Alternatively, if you'd prefer GUI, you can right click on the file in Dolphin and choose Properties, followed by the Permissions tab.  Both will do the same function.

---

### Post by Wiking on 2011-12-05
Thanks guys.

Oh just a question, when I'm pointing Chmod to a file, do I just type the name of the file, or do I have to point to where it is? 

Ex. home/documents/

---

### Post by killermist on 2011-12-05
Depends on the context.
-R is recursive mode, so the starting point(s) should be directories
For other uses, you should just use the filename(s) (with path if it might be ambiguous from the console.

Be careful when using recursive, because if applying the wrong parameters, you could have an entire directory that is writable, but not readable of browsable/listable.

[edit]
I'd recommend making a little sandbox directory (like /home/user/sandbox), create a few empty files, subdirectories, and more empty files in it, and try several chmod commands on those files to see how it works.

---

### Post by nothingspecial on 2011-12-05
> **Wiking said:**
> Thanks guys.

Oh just a question, when I'm pointing Chmod to a file, do I just type the name of the file, or do I have to point to where it is? 

Ex. home/documents/

If you are in your Documents folder then just the file name will do, if not then you need to specify either the full path or the path from where you are to the file.

Remember that linux is case sensitive, so unless you have renamed the default folders it will be Documents with a capital D, and the command is chmod with a lower case C

---

### Post by Wiking on 2011-12-05
I was finally able to run the script. I tried several methods and found that the only one that worked was when I used the full path  

/home/user/Documents/Scripts/test_script.sh

I tried running the script with just the file name and Konsole could not open, even though they were in the Documents folder. So I made a folder for the scripts and wrote the full path and it worked!

At least I got it running.

---

### Post by drmrgd on 2011-12-05
If you've added:

```
#! /bin/bash
```

to the start of your script, you should be able to execute the script in this way (be sure you're in the same directory as the script and that you've made it executable):

```
./test_script.sh
```

---

