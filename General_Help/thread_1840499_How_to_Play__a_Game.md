---
title: "How to Play  a Game"
date: 2011-09-07
forum: General Help
---

### Post by onaridge on 2011-09-07
I successfully installed my first game in Ubuntu, a demo for the latest Penumbra game using the Bash shell command. The guts are in my home folder. Problem is I don't know how to run the game. I don't see any kind of executable in there and I got a message after I installed that said something to the effect of "installed correctly please find the executable in the home folder to launch".

What do I do?

---

### Post by papibe on 2011-09-07
Could you post the result of this in the folder you unpacked it?
```
$ ls *.bin *.app *.exe 
```
Regards.

---

### Post by onaridge on 2011-09-07
loren@loren-linux1:/home$ $ ls *.bin *.app *.exe
$: command not found
loren@loren-linux1:/home$  ls *.bin *.app *.ex
ls: cannot access *.bin: No such file or directory
ls: cannot access *.app: No such file or directory
ls: cannot access *.ex: No such file or directory
loren@loren-linux1:/home$ $ ls *.bin *.app *.exe
$: command not found


I must be doing something wrong. I tried it without the $ and that didn't work either.

---

### Post by papibe on 2011-09-07
I used '$' to represent the prompt. Just paste the command:
```
ls -l  *.bin *.app *.exe
```

Regards.

---

### Post by onaridge on 2011-09-07
Yup I did that too but also repasted what you wrote and got the same result:


loren@loren-linux1:~$ ls -l  *.bin *.app *.exe
ls: cannot access *.bin: No such file or directory
ls: cannot access *.app: No such file or directory
ls: cannot access *.exe: No such file or directory

---

### Post by papibe on 2011-09-07
I believe when you unzip the file, a new directory was created. Let's call that directory penumbra_dir. Then, try this:
```
$ cd penumbra_dir
$ ls -l  *.bin *.app *.exe
```
Regards.

---

### Post by onaridge on 2011-09-08
I had actually tried that before I even asked on the forum. But here's the output even when I type in the actual folder which is PenumbraOvertureDemo.


oren@loren-linux1:~$ cd penumbra_dir
bash: cd: penumbra_dir: No such file or directory

loren@loren-linux1:~$ cd penumbraOvertureDemo
bash: cd: penumbraOvertureDemo: No such file or directory
loren@loren-linux1:~$ cd PenumbraOvertureDemo-dir
bash: cd: PenumbraOvertureDemo-dir: No such file or directory

---

