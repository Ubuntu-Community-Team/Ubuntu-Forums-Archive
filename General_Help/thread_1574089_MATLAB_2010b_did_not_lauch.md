---
title: "MATLAB 2010b did not lauch"
date: 2010-09-13
forum: General Help
---

### Post by sammy0131 on 2010-09-13
Hi Ubuntu folks,

I am totally new to Ubuntu and today I installed the latest MATLAB. Because of the permission problem (I think) I couldn't install under usr/local/ so instead I installed under home/MY NAME/MATLAB/2010b/ after creating the folders to install (am I already wrong at this point??)

I see "matlab" under /2010b/bin/ but when I type "matlab" on command prompt, it doesn't launch. 

Can anyone let me know what was wrong with what I did??

Thanks in advance!!

---

### Post by Gunman1982 on 2010-09-13
If you change to your matlab directory 'cd /home/NAME/MATLAB/2010b/bin' you have to start it using './matlab'. Or you use the absolute path right from beginning as '/home/NAME/MATLAB/2010b/bin/matlab'

If the directory is not part of the PATH variable the system doesn't know where to look for the matlab executable.

---

### Post by sammy0131 on 2010-09-13
Thanks for the reply! As I was waiting, I moved the MATLAB folder under local and created a launcher with the following command:

sh /usr/local/MATLAB/R2010b/matlab -desktop

and it worked. But I have to type this command on the terminal every time:(
I will try your way.

---

### Post by sammy0131 on 2010-09-14
I don't know why the direct path doesn't work. So far only when I typed using 'sh' command with the direct path worked. Any idea?? Does anyone also know the easier way to launch the program? It is painful to write the full path every time.

---

