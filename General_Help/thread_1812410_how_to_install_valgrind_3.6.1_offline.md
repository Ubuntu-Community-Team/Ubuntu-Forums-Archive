---
title: "how to install valgrind 3.6.1 offline?"
date: 2011-07-26
forum: General Help
---

### Post by vikash_chandola on 2011-07-26
I have downloaded valgrind 3.6.1 from [here]("http://valgrind.org/downloads/"). I want to install it, :ohow to do it.How to install valgrind on xubuntu 11.04.
This program is not in software center.:confused:
I am already using code::blocks 10.05. Can i integrate it with codeblocks so that as i debug program in codeblocks valgrind called itself and show memory leaks.

---

### Post by enimeizoo on 2011-07-26
There should be instructions in the tarball. Extract the folder and look for files called README or INSTALL . There should be basic and detailed instructions if they did things right (there is no reason to think they didn't, it is a quite serious project).

That said, do you need to install it offline? It appears to be in the repositories here, you should be able to install it with :
```
sudo apt-get install valgrind
```

Hope it helps!

---

### Post by vikash_chandola on 2011-07-26
> **enimeizoo said:**
> There should be instructions in the tarball. Extract the folder and look for files called README or INSTALL . There should be basic and detailed instructions if they did things right (there is no reason to think they didn't, it is a quite serious project).

That said, do you need to install it offline? It appears to be in the repositories here, you should be able to install it with :
```
sudo apt-get install valgrind
```

Hope it helps!
I know the command you write. I try to install that with the files i download but failed. I will install it with commands you give. :(:(I can't install a software in Linux wtihout software center:(:(
Can you tell me how to run executive files in Linux. I am newbie in Linux so i have very little knowledge of it.I make simple programs in Xubuntu using code blocks 10.05 when i compile and run them via code blocks they run fine but when i click on their executive file it does not run(nothing happen). Am i need to go to terminal to run that if yes then what to do then(in trminal:confused:).

---

### Post by enimeizoo on 2011-07-26
To execute commands you need a terminal emulator. I'm not aware of xfce's menus, so I can't really help more about it. Does alt+F2 show you a prompt or something?

Once in the terminal, the command I gave should install valgrind.

Another problem is that your executables don't work. There are two possible issues. First is that the file could just not have the right permissions to be executed. To solve that, right-click the file, select "properties" search for a permission tab, and you should have the option to make it executable somewhere.
The second possible issue would be that your file should be run in a terminal. Try to open a terminal, go to the directory where your executable is, and assuming your executable is named "a.out", here is the command you should run :
```
./a.out
```This way, you will be able to see the output of your program.

---

### Post by vikash_chandola on 2011-07-26
> **enimeizoo said:**
> To execute commands you need a terminal emulator. I'm not aware of xfce's menus, so I can't really help more about it. Does alt+F2 show you a prompt or something?

Once in the terminal, the command I gave should install valgrind.

Another problem is that your executables don't work. There are two possible issues. First is that the file could just not have the right permissions to be executed. To solve that, right-click the file, select "properties" search for a permission tab, and you should have the option to make it executable somewhere.
The second possible issue would be that your file should be run in a terminal. Try to open a terminal, go to the directory where your executable is, and assuming your executable is named "a.out", here is the command you should run :
```
./a.out
```This way, you will be able to see the output of your program.
thanks. I have already posted this question that how to run executable n this forum even after getting many answers i did not able to run executable but your one answer help me and now i can run executables.
I have installed valgrind using command you give.
THANKS **enimeizoo** !!!!!..................

---

