---
title: "7zip compression settings"
date: 2011-12-30
forum: General Help
---

### Post by emptycoder on 2011-12-30
Hello everyone.
I'm facing a problem with compressing files, 7zip doesn't have GUI on Linux, installing it means that Archive Manager will gain an ability to compress and open 7z file formats only.
I have huge files that I need to compress on Ultra mode, but I didn't know how to do that, I tried some command lines but no luck.
I was wondering if there's any way to edit 7zip settings so I can make Ultra Mode as a default with Archive Manager for 7z format?
If you have any info about this matter, please let me know. Thanks.

---

### Post by 2F4U on 2011-12-30
You get the available options by typing 

```
man 7zip
```

in a terminal.

This site has a nice tool that will generate the command line for you after you select some settings:

[http://www.howtoadvice.com/7zipHelper](http://www.howtoadvice.com/7zipHelper)

---

### Post by emptycoder on 2011-12-30
I tried that command and that's what I got
No manual entry for 7zip
(Alternatively, what manual page do you want from section 7zip?)
I already checked that website, and it doesn't work for some unknown reason, even if it works, it would be a real pain to do that to hundreds of files, I was looking for a fast solution, that if there's any.:confused:

---

### Post by Telengard C64 on 2011-12-30
To read 7zip's manual I use:

```
man 7z
```

If installed, the HTML documentation for 7zip should be at **/usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm**.

> **emptycoder said:**
> I was wondering if there's any way to edit 7zip settings so I can make Ultra Mode as a default with Archive Manager for 7z format?

I don't know how to configure Archive Manager, but here's the command to use *Ultra* compression:

```
7z a -mx=9 /PATH/TO/ARCHIVE.7z FILE
```

If you want to archive all the **.txt** files in **/home/user/Documents**

```
$ cd /home/user/Documents
$ 7z a -mx=9 /mnt/hdd2/user-txt-files.7z *.txt

```

If you want to archive the entire directory tree **/home/user/Documents**:

```
$ cd /home/user/
$ 7z a -mx=9 /mnt/hdd2/user-documents.7z Documents/

```

Read the documentation for more.

HTH

---

### Post by emptycoder on 2011-12-30
Thanks for info, but what if I want to compress more than a one file?
Example: let's say I have two files on Desktop, BladeRunner.avi and BladeRunner.txt and I want to compress them both to just one 7z format compressed file with ultra mode. and naming that file BladeRunner.7z
How would the commands look like?
I'm trying to see the whole picture so I can understand what am I doing, thanks.

---

### Post by guestolo on 2011-12-30
I'm pretty sure the following would work

7z a -t7z /home/<user>/Desktop/BladeRunner.7z /home/<user>/Desktop/BladeRunner.txt /home/<user>/Desktop/BladeRunner.avi  -mx9

Edit>>Keep in mind, I didn't change to Desktop directory in terminal
Forgot to add Desktop to the location: Fixed

---

### Post by Telengard C64 on 2011-12-30
> **emptycoder said:**
> Example: let's say I have two files on Desktop, BladeRunner.avi and BladeRunner.txt and I want to compress them both to just one 7z format compressed file with ultra mode. and naming that file BladeRunner.7z

In the spirit of Ubuntu CoC I won't give a "RTFM" response ... even though I already pointed you to the documentation and suggested reading it.  :P

```
$ cd /home/USERNAME/Desktop
$ 7z a -mx=9 BladeRunner.7z BladeRunner.avi BladeRunner.txt

```

Also consider using globbing.

```
7z a -mx=9 BladeRunner.7z BladeRunner*
```

It doesn't have to be any more complicated than that, but if your needs grow more demanding then you will benefit greatly by learning Bash and reading the 7zip manual.

---

### Post by emptycoder on 2011-12-30
hey, i did read the manual and i found nothing about ultra compressing mode, i even tried F+ctrl and no ultra was found.
i will mark it as solved, thanks....

---

### Post by Telengard C64 on 2011-12-30
> **guestolo said:**
> 7z a -t7z /home/<user>/Desktop/BladeRunner.7z /home/<user>/Desktop/BladeRunner.txt /home/<user>/Desktop/BladeRunner.avi  -mx9

Careful there. Some commands get prickly about the order of arguments.

[quote=man 7z]SYNOPSIS
        7z [adeltux] [-] [SWITCH] <ARCHIVE_NAME> <ARGUMENTS>...[/quote]

[list]
[*]**[adeltux]** = Commands, pick one and only one. We are using the **a** command (add files).
[*]**SWITCH** = Options to control how 7z works. We are using **-mx=9** to set the compression level.
[*]**<ARCHIVE_NAME>** = The name of the archive file to process. The archive file will be created if it doesn't already exist. We are adding files to the archive BladeRunner.7z.
[*]**<ARGUMENTS>...** = Names of files to operate on. When adding these are files on the system (outside the archive). When extracting they are names of files in the archive (to be extracted). We are adding the files **BladeRunner.avi** and **BladeRunner.txt**
[/list]

---

### Post by Telengard C64 on 2011-12-30
> **emptycoder said:**
> hey, i did read the manual and i found nothing about ultra compressing mode,

Then you didn't read **/usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm**. This is where the full documentation is located on my system. The 7z manpage (**man 7z**) points you to the full documentation because the manpage itself is very terse.

---

### Post by emptycoder on 2011-12-30
thanks a lot for the info, i think i know where to go from here now, i just needed a boost.
thank you very much.

---

### Post by Telengard C64 on 2011-12-30
You're welcome. :)

---

