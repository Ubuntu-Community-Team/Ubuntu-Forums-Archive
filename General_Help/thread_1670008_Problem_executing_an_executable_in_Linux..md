---
title: "Problem executing an executable in Linux."
date: 2011-01-18
forum: General Help
---

### Post by Crux_Dissimilata on 2011-01-18
I coded a simple hello world program to see if I can get something to work on my own in Linux. I used the command "sudo g++ hello.cpp -o helloWorld" to build the executable. However when I am in the terminal (in the right path) and I type "helloWorld" or "sudo helloWorld" it does not run. I look over at google and it told me that I could be in the wrong directory (path) what I am not, or the file permissions could be set wrong. However I looked it up on google as well and I can't see nothing wrong with the file permissions. Hoping someone could lend a helping hand. These are the file permissions as received from "ls -l".
> drwxr-xr-x 3 root root 4096 2011-01-18 19:38 bin
-rw-r--r-- 1 root root 1050 2011-01-18 19:37 hello.cbp
-rwxr-xr-x 1 root root 7734 2011-01-18 19:41 helloWorld
-rw-r--r-- 1 root root  117 2011-01-18 19:37 main.cpp
drwxr-xr-x 3 root root 4096 2011-01-18 19:38 obj

---

### Post by Lukiwuki on 2011-01-18
Try
> sudo ./helloWorld

---

### Post by Lukiwuki on 2011-01-18
Try
> sudo ./helloWorld

---

### Post by Lukiwuki on 2011-01-18
Open a terminal and type
sudo ./helloWorld

---

### Post by Vaphell on 2011-01-18
```
./helloWorld
```
system looks for programs in folders listed in PATH variable, i doubt your project's dir is there.
. = current directory

why do you run everything as root? you don't need to use sudo for everything, you can program, compile and run programs without it.

---

### Post by Lukiwuki on 2011-01-18
Sry my internet sucks and i like post 500 times everytime I post sth :/

---

### Post by Vaphell on 2011-01-18
ubuntuforums are extremely crappy lately. Just press Post once and don't bother when it looks like it failed. Your post will appear in few minutes.

---

### Post by hawkmage on 2011-01-18
Why are the files owned by root?  You should do the coding as your self.  You should not have to use sudo to create and compile your code.  developing coed as root is a bad practice, it can lead to unexpected permission issues

---

