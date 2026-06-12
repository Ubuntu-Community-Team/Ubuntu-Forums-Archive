---
title: "Tutorial: How to extract troublesome .rar files with p7zip and terminal!"
date: 2011-09-19
forum: General Help
---

### Post by AlexOnVinyl on 2011-09-19
So, recently I've been having issues with extracting full .rar files with Archive Extractor (fileroll) on my Natty 32bit computer.  And after doing some research here and there, and some hard thinking, **I found the solution to troublesome rar files that aren't allowing you to extract all the files.**

The solution is to use **p7zip via Terminal! **
(for being a noob, this is an accomplishment for me)

So I wanted to share with you how to do so.

[SIZE=2][B]1. Go grab p7zip-rar via Terminal (easiest way to get all the dependencies) 
[/B][/SIZE]```
sudo apt-get install p7zip-rar
```[SIZE=2][B]2. Once it's done installing - go ahead and navigate to the folder where your troublesome rar file is via Terminal "cd".
[/B][/SIZE]```
 cd path/here/
``` example: ```
cd ~/Downloads/
``` the tilda in front of the forward slash is to show that the directory you're trying to cd into is in your "Home" folder.  

**[SIZE=2]3.[/SIZE]** [SIZE=2][B]When you get to your folder - use this command:
[/B][/SIZE]```
7z x FileName.rar
``` The 'x' is important because this signifies to 7zip to extract the file with that file name. the original syntax is ```
7z x filename.7z
``` but since we're extracting a rar file, we replace the '.7z' with '.rar'

[B]Hopefully this will have extracted the .rar file successfully where the unrar command didn't.  If you run into any errors, then it could just be the rar file itsself.

Also, one last thing:  [/B]
If your archive is split into multiple volumes, specify the lowest numbered volume.
```
7z x filename.rar(or 7z).001
```Then if you want to extract to another directory
```
7z x FileName.7z -o/home/user/Desktop/foldername
```Hope this helps\\:D/

---

### Post by PayPaul on 2011-10-12
I have a similar problem and I do appreciate this possible solution to it. Yet I'd like to know if it's possible to get a diagnosis or better information on what might be wrong with any particular .rar file. Is there such a method or program to do so?

---

### Post by msinfo on 2011-10-16
Million Thanks!  :D AlexOnVinyl :D

Info was really valuable for me, because I am new to Ubuntu.
Nice, Short, Simple, with example, this article is really awesome.
Thanks for sharing and making Ubuntu popular with newbies like me.

Stay Connected

---

### Post by AlexOnVinyl on 2011-10-23
> **PayPaul said:**
> I have a similar problem and I do appreciate this possible solution to it. Yet I'd like to know if it's possible to get a diagnosis or better information on what might be wrong with any particular .rar file. Is there such a method or program to do so?

Not sure yet, unfortunately...

---

