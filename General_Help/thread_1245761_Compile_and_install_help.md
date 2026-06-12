---
title: "Compile and install help"
date: 2009-08-20
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-08-20
i read this:
[http://ubuntuforums.org/showthread.php?t=611117](http://ubuntuforums.org/showthread.php?t=611117)
so i ran
```
 sudo apt-get install build-essential
```and dont know what to do next
trying to install same program just a different version 14.5.3

---

### Post by zvacet on 2009-08-21
You downloaded compressed package.Right click on it to uncompress it.That will make folder.If you downloaded it at desktop type 

```
cd Desktop
```

and then 

```
cd your_folder_name
```

and then type 

```
make READLINE=1
	make test
	sudo make install
```

---

### Post by pqwoerituytrueiwoq on 2009-08-23
got some errors
```
user@user-laptop:~$ cd Desktop
user@user-laptop:~/Desktop$ cd mathomatic-14.5.3
user@user-laptop:~/Desktop/mathomatic-14.5.3$ make READLINE=1
cc -Wall -Wshadow -Wno-char-subscripts -fomit-frame-pointer  -O -DUNIX -DVERSION=\"`cat VERSION`\" -DREADLINE   -c -o main.o main.c
In file included from main.c:44:
includes.h:47:31: error: readline/readline.h: No such file or directory
includes.h:48:30: error: readline/history.h: No such file or directory
main.c: In function 'main':
main.c:102: warning: implicit declaration of function 'rl_initialize'
main.c:103: warning: implicit declaration of function 'using_history'
main.c:104: warning: implicit declaration of function 'stifle_history'
main.c:105: error: 'rl_inhibit_completion' undeclared (first use in this function)
main.c:105: error: (Each undeclared identifier is reported only once
main.c:105: error: for each function it appears in.)
main.c:178: warning: implicit declaration of function 'read_history'
main.c: In function 'exit_program':
main.c:458: warning: implicit declaration of function 'write_history'
make: *** [main.o] Error 1
user@user-laptop:~/Desktop/mathomatic-14.5.3$ make test
Testing Mathomatic...
cd tests && time ../mathomatic -t all 0<&- >test.out && diff -u all.out test.out
time: cannot run ../mathomatic: No such file or directory
Command exited with non-zero status 127
0.00user 0.00system 0:00.00elapsed ?%CPU (0avgtext+0avgdata 0maxresident)k
0inputs+0outputs (0major+70minor)pagefaults 0swaps
make: *** [test] Error 127
user@user-laptop:~/Desktop/mathomatic-14.5.3$ sudo make install
[sudo] password for user: 
install -d /usr/local/bin
install -d /usr/local/share/applications
install -d /usr/local/share/pixmaps
install -m 0755 mathomatic /usr/local/bin
install: cannot stat `mathomatic': No such file or directory
make: *** [bininstall] Error 1
user@user-laptop:~/Desktop/mathomatic-14.5.3$ 

```

---

### Post by gesslein on 2009-08-24
sudo apt-get install libreadline5-dev

before compiling will fix that.

Regards,
George Gesslein II

---

