---
title: "&quot;no such file or directory&quot; error in runing an exe file"
date: 2011-12-12
forum: General Help
---

### Post by nedahp on 2011-12-12
Hi every one,

I have a problem and i would really be thankful if anyone help me.

I have a c++ code for "booksim"  simulator   which i  want to run it in ubuntu. till now i  never had problems in running such codes so like the other times I  copied the folder of my code on desktop and using terminal  i tried to run it.when i use "make" command every thing goes well but after that when i try to run the exe file named "booksim" with ./booksim command , an error message reported "no such a file or directory ".
but "booksim" is already exists in the folder.i thought maybe it is a permission problem so i checked the permission by "ls -l" command and it is right too.

can anyone help me please with this problem? I can not understand why this happens?

---

### Post by lechien73 on 2011-12-12
Hi & welcome to the forums,

I'm not familiar with booksim, so I can't offer any specific assistance with regard to it.

However, strace is my toy of the moment, so you could try running booksim like this:

```
strace -e open booksim
```

It should tell you what files / directories the program is attempting to open. It will appear on the line that says ENOENT (No such file or directory).

---

### Post by nedahp on 2011-12-12
thanks for your reply.
but i think it is not important what my c++  program is implementing,forget about booksim please.
imagine that i  have an execution file after compiling my c++ program.in general what causes to report "no such file or directory" message when someone try to run that file with "./filename" command?(except permission reasons) 
the error is :
 bash: ./booksim: not a such file or directory
booksim is just a name for my execution file

please help me,this problem is driving me crazy

---

### Post by The Cog on 2011-12-12
All I can imagine is that you are typing the wrong filename. Linux is case sensitive, so "./booksim" is not the same as "./Booksim". Or maybe somehow there's a hidden character in the file name? A space at the end of the filename can be hard to figure out. Try using tab completion in bash - type "./" and then press the tab key a couple of times to get a list of possible filename completions.

Or drag/drop the file from a file manager window to a command prompt.

---

### Post by lechien73 on 2011-12-12
Are you sure that the file has the execute bit set?

From the directory that contains booksim, if you run:

```
chmod 777 ./booksim
```

Does the ./booksim command still give the same error?

---

### Post by oldos2er on 2011-12-12
Are you using a 64-bit system and trying to run a 32-bit app?

---

### Post by nedahp on 2011-12-13
> **lechien73 said:**
> Are you sure that the file has the execute bit set?

From the directory that contains booksim, if you run:

```
chmod 777 ./booksim
```

Does the ./booksim command still give the same error?
thank you for your suggestion, but i have done that before. when i use "ls -l"in terminal it shows me booksim is executable(-rwxr-xr-x) but it still dose not work !

---

### Post by nedahp on 2011-12-13
> **oldos2er said:**
> Are you using a 64-bit system and trying to run a 32-bit app?
can you explain more about this case please? yes,I have a 64-bit system,but i have no idea about the application

---

### Post by oldtimer7777 on 2011-12-13
> **nedahp said:**
> can you explain more about this case please? yes,I have a 64-bit system,but i have no idea about the application

That's not it. It is the chmod command you need to use.  You need to make the newly created exe executable within Linux.

It is part of the securty of Linux.

---

### Post by nedahp on 2011-12-13
> **The Cog said:**
> All I can imagine is that you are typing the wrong filename. Linux is case sensitive, so "./booksim" is not the same as "./Booksim". Or maybe somehow there's a hidden character in the file name? A space at the end of the filename can be hard to figure out. Try using tab completion in bash - type "./" and then press the tab key a couple of times to get a list of possible filename completions.

Or drag/drop the file from a file manager window to a command prompt.
Hi,
I tried a tab after ./booksim but it did not work,also when i drag the file to a common prompt it gives me '/home/neda/Desktop/src/booksim' and when i'm in src path and use the same type for "booksim" with "./",still gives me error!
is there any other hidden characters which i can  try?
do you think this problem can be causes by my linux version or the installation of my system?
on the other hand i could run the other execution files before thus i think it can't be my system or my linux version
I wish i could send you the folder of program and you just try to run an exe file yourself,but i can not fine a place for attaching files.

---

### Post by oldtimer7777 on 2011-12-13
> **nedahp said:**
> Hi,
I tried a tab after ./booksim but it did not work,also when i drag the file to a common prompt it gives me '/home/neda/Desktop/src/booksim' and when i'm in src path and use the same type for "booksim" with "./",still gives me error!
is there any other hidden characters which i can  try?
do you think this problem can be causes by my linux version or the installation of my system?
on the other hand i could run the other execution files before thus i think it can't be my system or my linux version
I wish i could send you the folder of program and you just try to run an exe file yourself,but i can not fine a place for attaching files.

Did you try chmod?

You need to chmod your newly created files in Linux to make them executable. 

Research chmod command on Google search engine.

Every file you create in Ubuntu needs to have permissions, and chmod sets permissions of files.

---

### Post by nedahp on 2011-12-13
> **oldtimer7777 said:**
> Did you try chmod?

You need to chmod your newly created files in Linux to make them executable. 

Research chmod command on Google search engine.

Every file you create in Ubuntu needs to have permissions, and chmod sets permissions of files.
Yes,I did
I used "chmod a+x booksim" but still has error after using "./booksim" command.
"ls -l" in the path that my execution file is in it,shows me "booksim" is executable but this error happens again ! :(

---

### Post by MartijnNL on 2011-12-13
You might want to try renaming the file and then try running it with it's new name. Then you know for sure there are no unintended characters within the filename.

If that doesn't work, could you paste the output of:
```
ls -al /home/neda/Desktop/src
```

---

### Post by mcduck on 2011-12-13
This might sound obvious, but I thought I still should aks just to make sure... You are talking about "exe file" all the time. Do you mean you catually complied the program into a .exe file, or are you just referring to the file being an executable program?

If the file name actually has the .exe extension, you'll of course need to also use it when executing the file. And also make sure you actually complied the program into ELF binary instead of a windows executable...

(anyway, the error you get simply means that either you are using the wrong filename, or are not currently in the directory where the file is located. If you are absolutely sure the file is located in your current directory, make sure you don't have a space at the end of the file name or something (I've seen people having that issue couple of times, it's kind of hard to spot since you can't see it)

---

### Post by oldos2er on 2011-12-13
> **nedahp said:**
> can you explain more about this case please? yes,I have a 64-bit system,but i have no idea about the application

What does ```
file booksim
``` say?

Edit: Can you tell us which version of Ubuntu you're running? If it's 11.04 or older, you might need to install ia32-libs to run 32-bit apps.

---

### Post by nedahp on 2011-12-13
Thanks to everyone for their suggestions and help,

fortunately my problem finally solved :)
I deleted  the executable file which already exists in src folder,and tried to compile the code from beginning.a new executable file(booksim)  generated after that is now executes with "./booksim" command.

Thank you again

---

### Post by MartijnNL on 2011-12-14
Good to hear. Can you mark the thread as solved using the Thread Tools on top?

---

