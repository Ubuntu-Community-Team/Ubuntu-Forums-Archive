---
title: "Xubuntu 11.10 Permission denied on some .exe compiling"
date: 2012-02-27
forum: General Help
---

### Post by meridius10 on 2012-02-27
I have been happily compiling C programs until now. 
 
I copied an example with a global variable and when I try to execute the program, I get a ```
bash...Permission denied 
``` msg. One other bit of code is also denied, but I'm pretty sure it executed yesterday.
 
My laptop has not been on the internet since I started compiling so it can't be an update that has caused this.
 
The other .exe files are all running ok with no permission problems.
 
Any ideas?

---

### Post by Paddy Landau on 2012-02-28
> **meridius10 said:**
> The other .exe files are all running ok with no permission problems.
Programs with the .exe extension are intended for Windows, not Linux, which may go some way to explaining your problem.

If that is not the problem (perhaps you put .exe as an extension deliberately), check your execution file's privileges. It should have the execute-bit set. You can do this from Nautilus (right-click the executable file > Permissions > Allow executing file as program), or from the the command line:
```
chmod +x *filename*
```

---

### Post by meridius10 on 2012-02-28
I'm not entirely sure why some of the .exe files were executing whilst others were not. 
 
The book I am going through gives the example of: gcc *filename*.c -o *filename*.exe,
but I changed that to: gcc *filename*.c -o *filename*, which seems to have resolved the problem after entering *./filename* in the cmd prompt.
 
Whilst this has resolved the problem, I'm trying to understand the default behaviour of .exe files in Ubuntu. I thought these were not supposed to run at all.

---

### Post by Paddy Landau on 2012-02-28
Extensions have no meaning in Linux. Linux always attempts to work out the type of file by its contents.

So, for example, you can have a PDF called *lookatme.odt*, a JPG photo called *seeme.pdf*, an MP4 video called *viewme* (with no extension) and an executable file called *runme.doc*.

Windows requires an extension; Linux does not. The files *myfile* (without a dot) and *myfile.* (with a dot) are two different files. The file *.htaccess* has an extension but no name (this file name is used on websites and is hard to create on Windows).

Multiple dots are permitted, e.g. *File.2012.02.28* is a valid file name. Spaces are also permitted, but they need special handling on the command line.

(In other words, Linux does not treat the dot in a file name any differently from any other character. The term *extension* is relevant only to human eyes; it has no meaning to Linux.)

A file is deemed executable if, and only if, its executable bit is set.

Thus, the command:
```
gcc filename.c -o filename.exe
```creates an executable file called *filename.exe*, so to run it you need to enter:
```
./filename.exe
```If you are writing for Windows, you must add .exe. For Linux, the standard is to use no extension, but as I explained this is optional. You can call it *filename.whatalongextension* if you wish.

If you try to run a Windows executable file (*filename.exe* compiled for Windows, not for Linux) from Nautilus, then Nautilus will call Wine. Wine is a front-end that attempts to run Windows programs on Linux. Wine is by no means perfect, and more Windows programs will fail to work than will succeed. You can look up a program in [the Wine database]("http://appdb.winehq.org/") to find out how well it will run (assuming it has been tested).

If you wish to install Windows programs and (try to) run them on Linux, I strongly recommend you use PlayOnLinux. PlayOnLinux is in the repositories, and is a front-end to Wine, hiding its complexity (Wine is complex to use).

HTH

---

### Post by meridius10 on 2012-02-28
Thanks for explaining the file extensions to me in Linux. I think I will carry on compiling without using .exe as it makes no sense to add that in.
 
I had previously tried Wine and gave up on it, but it's good to know there is a different option with PlayOnLinux.
 
I have now reached the stage where I am using Ubuntu for one thing and Windows for another on separate computers. It is very nice to get away from Microsoft as much as possible as most companies have become fixed on their products, that we are obliged to learn, which is not a good thing.

---

### Post by MG&amp;TL on 2012-02-28
> **meridius10 said:**
> Thanks for explaining the file extensions to me in Linux. I think I will carry on compiling without using .exe as it makes no sense to add that in.
 .

If it works for you, great, but if you want to distribute it for linux, please chop the exe off. Command-line nerds do not like adding ".exe" onto every command! (particularly as it reminds of them of Windows)

---

