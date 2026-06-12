---
title: "Need help: Unable to locate package ''X'' (Merlin Linkage)"
date: 2011-09-18
forum: General Help
---

### Post by gulsah on 2011-09-18
Hi everyone,
I am a new linux user and all the commands and terminal application is very difficult for me to understand. My problem is about installation of a program. I am trying to install a program called ''MERLIN'' for linkage analysis which is used in genetics. I downloaded [Linux-merlin.tar.gz]("http://www.sph.umich.edu/csg/abecasis/Merlin/download/Linux-merlin.tar.gz")      For GNU/LINUX systems from the website [FONT=monospace]: [http://www.sph.umich.edu/csg/abecasis/Merlin/download/](http://www.sph.umich.edu/csg/abecasis/Merlin/download/)[/FONT] . After that I opened the terminal application and write this command '' sudo apt-get install merlin''. However the output message is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package merlin
Therefore I could not install the program on my computer. 
At this point, what can I do to install this program? Thank you.

---

### Post by Elfy on 2011-09-18
That needs to be compiled

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by gulsah on 2011-09-18
Thank you, but I am still in a trouble with the ''./configure''. I will attach the screenshots of steps that I performed and the results.

---

### Post by Elfy on 2011-09-18
You need to be in the folder that results from extracting the archive.

If the folder is on your Desktop

cd ~/Desktop/merlin-1.1.2

Then run the compile. 

If it's elsewhere then change to the necessary directory.

---

### Post by gulsah on 2011-09-18
I performed everything in the folder that resulted from the extraction of files now, however, same result still there. I will attach the screenshot :)

---

### Post by Bobhuber on 2011-09-18
> **gulsah said:**
> Hi everyone,
I am a new linux user and all the commands and terminal application is very difficult for me to understand. My problem is about installation of a program. I am trying to install a program called ''MERLIN'' for linkage analysis which is used in genetics. I downloaded [Linux-merlin.tar.gz]("http://www.sph.umich.edu/csg/abecasis/Merlin/download/Linux-merlin.tar.gz")      For GNU/LINUX systems from the website [FONT=monospace]: [http://www.sph.umich.edu/csg/abecasis/Merlin/download/](http://www.sph.umich.edu/csg/abecasis/Merlin/download/)[/FONT] . After that I opened the terminal application and write this command '' sudo apt-get install merlin''. However the output message is:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package merlin
Therefore I could not install the program on my computer. 
At this point, what can I do to install this program? Thank you.
The file that you downloaded Linux-merlin.tar.gz does not need to be compiled. Just extract it in the directory of your choice and you are supposed to be able to run the executable (I assume it is merlin) from there. However not knowing anything at all about the the program (or what its supposed to do) I did just that and the program does nothing so I can't be of any other assistance.

---

### Post by gulsah on 2011-09-18
> **Bobhuber said:**
> The file that you downloaded Linux-merlin.tar.gz does not need to be compiled. Just extract it in the directory of your choice and you are supposed to be able to run the executable (I assume it is merlin) from there. However not knowing anything at all about the the program (or what its supposed to do) I did just that and the program does nothing so I can't be of any other assistance.
Although I have tried to run the program without compiling, it did not work. Still, thank you for your help.

gulsah@ubuntu:~$ cd dls
gulsah@ubuntu:~/dls$ ls
Linux-merlin.tar.gz  merlinn
gulsah@ubuntu:~/dls$ cd merlinn
gulsah@ubuntu:~/dls/merlinn$ ls
ChangeLog        LICENSE.twister  merlin-regress  pedmerge  README
examples         [COLOR=DarkRed]merlin      [/COLOR]     minx            pedstats
hapmapConverter  merlin-offline   minx-offline    pedwipe
gulsah@ubuntu:~/dls/merlinn$ [COLOR=Purple]./merlin -d dat -p ped -m map[/COLOR]
bash: ./merlin: No such file or directory
gulsah@ubuntu:~/dls/merlinn$

---

