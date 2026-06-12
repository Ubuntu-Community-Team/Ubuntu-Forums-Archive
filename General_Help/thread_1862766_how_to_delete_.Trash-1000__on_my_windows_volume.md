---
title: "how to delete .Trash-1000  on my windows volume?"
date: 2011-10-17
forum: General Help
---

### Post by Gianmaria on 2011-10-17
Hi

i deleted some files on my windows 7 and ubuntu 10.10 create a folder .Trash-1000 
and i can't delete under windows , but i can see it

i can't see with ubuntu file manager

i mounted windows 7 
and i can't see this folder

so with the console
cd /media/yourdiskname

youdiskname under windows is "windows 7"
but the console doesn't accept cd /media/windows 7
so 
```
cd /media
dir
```
and i get 
floppy	floppy0  Windows\ 7 			 		
i did copy and paste it

cd /media/windows 7 doesn't work
i tried a lot but nothing

how could i do it?
is there a way to see this folder in ubuntu file manager and delete with it?

thanks
cheers

---

### Post by Pynalysis on 2011-10-17
> **Gianmaria said:**
> Hi

i deleted some files on my windows 7 and ubuntu 10.10 create a folder .Trash-1000 
and i can't delete under windows , but i can see it

i can't see with ubuntu file manager

i mounted windows 7 
and i can't see this folder

so with the console
cd /media/yourdiskname

youdiskname under windows is "windows 7"
but the console doesn't accept cd /media/windows 7
so 
```
cd /media
dir
```and i get 
floppy    floppy0  Windows\ 7                      
i did copy and paste it

cd /media/windows 7 doesn't work
i tried a lot but nothing

how could i do it?
is there a way to see this folder in ubuntu file manager and delete with it?

thanks
cheers

Have you enabled hidden files/folders? Try pressing Ctrll+h to enable/disable them.

Hope that helps!

---

### Post by jtarin on 2011-10-17
Any file in Linux with a "."(dot) before it is a hidden file that you cannot not see until you open Nautilus and you do as Pynalysis suggest.

---

### Post by Gianmaria on 2011-10-17
> **Pynalysis said:**
> Have you enabled hidden files/folders? Try pressing Ctrll+h to enable/disable them.

Hope that helps!
thanks it **works **with ubuntu file system

but i can not see these folders inside wondows volume ,and i don't know why...

did you check to mount a windows volume , delete a folder , empty the trash and see if you can see with ctrl +h?


thanks a lot


> **jtarin said:**
> Any file in Linux with a "."(dot) before it is a  hidden file that you cannot not see until you open Nautilus and you do  as Pynalysis suggest.
thanks for the information

---

### Post by Mark Phelps on 2011-10-17
MS Windows does NOT use the Linux filesystem convention of preceding a filename with a period to "hide" it. So, that does not have anything to do with your ability to see the file or directory in MS Windows.

Your "cd" command didn't work because you have "Windows 7".  Notice the embedded blank.  So, you were REALLY trying to cd to "Windows".  You have to enclose the directory name in quotation marks if it contains embedded blanks.

Also, if this is an OS partition that you are messing with by mounting it in Linux, that is asking for trouble.  Do not be surprised if, one of these days, when you go to boot into that OS, it fails to boot.

---

