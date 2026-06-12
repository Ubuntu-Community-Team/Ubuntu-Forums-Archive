---
title: "Access Denied/Unknown command"
date: 2010-10-17
forum: General Help
---

### Post by layers on 2010-10-17
Hi. I am a relatively new to Linux, and I have a problem which I cannot resolve. Any help would be appreciated, and thanks in advance.

I wrote this simple C++ program, dealing with classes(that's what we're learning at school). For some reason, after compilation, I cannot run it, as I would normally do with any other program.

```
#include <iostream>
using namespace std;

class Warrior
{
	public:
	int health;
	int speed;
	void attack()
	{
		cout << "I am attacking" << endl;
	};
};


int main()
{
	Warrior t;
	t.health = 87;
	t.speed = 92;
	
	cout << "My health is " << t.health << "My speed is " << t.speed << endl;
	
	t.attack();
	
	return 0;
}
```

so, I go to terminal, and after

```
ibo@ibo-laptop:~$ cd Desktop
ibo@ibo-laptop:~/Desktop$ g++ -c t.cpp -o t
ibo@ibo-laptop:~/Desktop$ ./t
bash: ./t: Permission denied
ibo@ibo-laptop:~/Desktop$ sudo ./t
[sudo] password for ibo: 
sudo: ./t: command not found
ibo@ibo-laptop:~/Desktop$ 

```

What gives?

---

### Post by efflandt on 2010-10-17
**ls -l Desktop** (or **ls -l** once you cd Desktop)

Does "t" have execute permission?
Assuming you are in that directory try **chmod u+x t** (or **chmod a+x t** or **chmod 755 t** for anyone to run it).

**man chmod** from a terminal for more info.

---

### Post by layers on 2010-10-17
```
ibo@ibo-laptop:~$ cd Desktop
ibo@ibo-laptop:~/Desktop$ ls -l
total 60
-rwxr-xr-x 1 ibo ibo  285 2010-10-09 02:07 calibre.desktop
-rw-r--r-- 1 ibo ibo 4696 2010-10-17 12:23 Driver.cpp
-rw-r--r-- 1 ibo ibo  177 2010-10-17 12:24 Driver.h
-rw-r--r-- 1 ibo ibo  961 2010-10-17 11:38 Employee.h
-rwxr-xr-x 1 ibo ibo  477 2010-10-09 01:45 gnome-terminal.desktop
-rwxr-xr-x 1 ibo ibo 4583 2010-10-11 16:21 google-chrome.desktop
drwxr-xr-x 7 ibo ibo 4096 2010-10-11 19:15 matlab
-rw-r--r-- 1 ibo ibo  852 2010-10-17 11:37 Staff.h
-rwxr--r-- 1 ibo ibo 2460 2010-10-17 17:03 t
-rw-r--r-- 1 ibo ibo  318 2010-10-17 15:59 t.cpp
-rw-r--r-- 1 ibo ibo  864 2010-10-17 15:51 test.cpp
-rwxr-xr-x 1 ibo ibo 1381 2010-10-09 01:44 thunderbird.desktop
-rw-r--r-- 1 ibo ibo 2460 2010-10-17 16:00 t.o
ibo@ibo-laptop:~/Desktop$ chmod 755 t
ibo@ibo-laptop:~/Desktop$ ./t
bash: ./t: cannot execute binary file
ibo@ibo-laptop:~/Desktop$ 

```

---

### Post by sisco311 on 2010-10-17
The -c option says not to run the [linker]("http://en.wikipedia.org/wiki/Linker_(computing)").  Then the output consists of object files output by the assembler.

Don't use it:
```
g++ t.cpp -o t
```

---

### Post by layers on 2010-10-17
Thank you sisco311 and efflandt.

---

### Post by &#24746;&#39764;&#12398;&#31070; on 2010-10-17
Please make sure to mark this thread as SOLVED!

---

