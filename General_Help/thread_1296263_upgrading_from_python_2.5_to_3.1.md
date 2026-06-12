---
title: "upgrading from python 2.5 to 3.1"
date: 2009-10-20
forum: General Help
---

### Post by pixrael on 2009-10-20
ok i have downloaded and installing acording to the README file 

```

On Unix, Linux, BSD, OSX, and Cygwin:
    ./configure
    make
    make test
    sudo make install

```

all was going excelent, even take a long time installinga and making the test, but after all process when i run the command 
```

python --version

```

it returns **2.5.1**, so it appears i havent really upgrade the python 2.5 to 3.1

can u help me on that?

---

### Post by Bachstelze on 2009-10-20
Paste the output of

```
ls /usr/local/bin/python*
```

---

### Post by pixrael on 2009-10-20
i dont know what im doing wrong
```
pixrael@setGoldenHost:~$ ls usr/local/bin/python*
ls: cannot access usr/local/bin/python*: No such file or directory

```

---

### Post by Bachstelze on 2009-10-20
> **pixrael said:**
> i dont know what im doing wrong
```
pixrael@setGoldenHost:~$ ls usr/local/bin/python*
ls: cannot access usr/local/bin/python*: No such file or directory

```

You forgot the leading / ;)

ls [COLOR="Red"]/[/COLOR]usr/local/bin/python*

---

### Post by pixrael on 2009-10-20
hehehe sorry

```
pixrael@setGoldenHost:~$ sudo ls /usr/local/bin/python*
/usr/local/bin/python3      /usr/local/bin/python3.1-config
/usr/local/bin/python3.1  /usr/local/bin/python3-config

```

---

### Post by Bachstelze on 2009-10-20
So you can just run Python 3.1 with the commands python3 or python3.1:

```
python3 --version
```

---

### Post by pixrael on 2009-10-20
uhhmm thanks, but if i want to intall the python3.1 -dev ? i need it to compile blender
how i download it?

cuz im having this error

```

Compiling ==> 'node.c'
source/blender/blenkernel/intern/node.c:31:20: error: Python.h: No such file or directory
scons: *** [/home/BlenderSVN/build/linux2/source/blender/blenkernel/intern/node.o] Error 1

```

---

### Post by pixrael on 2009-10-20
ok i download the python 3.1-dev from the web page [http://packages.debian.org/experimental/i386/python3.1-dev/download](http://packages.debian.org/experimental/i386/python3.1-dev/download) and trying to install see what happend

```

pixrael@setGoldenHost:~/Desktop$ sudo dpkg -i python3.1-dev_3.1.1-1_i386.deb 
(Reading database ... 115041 files and directories currently installed.)
Preparing to replace python3.1-dev 3.1.1-1 (using python3.1-dev_3.1.1-1_i386.deb) ...
Unpacking replacement python3.1-dev ...
dpkg: dependency problems prevent configuration of python3.1-dev:
 python3.1-dev depends on python3.1 (= 3.1.1-1); however:
  Package python3.1 is not installed.
 python3.1-dev depends on libpython3.1 (= 3.1.1-1); however:
  Package libpython3.1 is not installed.
dpkg: error processing python3.1-dev (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3.1-dev

```

so even when i use the python3 --version and it returns 3.1.1 it still can be used by other programs and applications... 

i dont know how to really install the python 3.1, any help?  maybe i must delete the last version of python the 2.5 will try that way

---

### Post by Bachstelze on 2009-10-20
Well, the fact that you installed Python 3 from source will make things a bit more complicated. Did you have any reason to not just do this?

```
sudo apt-get install python3
```

---

### Post by pixrael on 2009-10-20
for me doesnt work, works to u ?

```

pixrael@setGoldenHost:~/Desktop$ sudo apt-get install python3
[sudo] password for pixrael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package python3

```:confused:

---

### Post by Bachstelze on 2009-10-20
You're probably running an older Ubuntu release, then. What does this command output?

```
find /usr/local/ -name "Python.h"
```

---

### Post by pixrael on 2009-10-20
i dont know maybe it is an old version


```


pixrael@setGoldenHost:/home/BlenderSVN/blender$ find /usr/local/ -name "Python.h"
/usr/local/include/python3.1/Python.h
pixrael@setGoldenHost:/home/BlenderSVN/blender$ 


```

---

### Post by Bachstelze on 2009-10-20
Sorry, I forgot something else. ^^; What is the last command you run before the error happens?

---

### Post by pixrael on 2009-10-20
well first of all thanks for your time, 

and well the thing is im trying to upgrade the python to the 3.1 because to compile blender i need it the version 3.1 or high installing blender i use the command 

 ```
scons
```

and the error that shows is 
```

Compiling ==> 'node.c'
source/blender/blenkernel/intern/node.c:31:20: error: Python.h: No such file or directory
scons: *** [/home/BlenderSVN/build/linux2/source/blender/blenkernel/intern/node.o] Error 1
scons: building terminated because of errors.

```

so well the thing is i need to upgrade the python and maybe download the developers package of the python3.1 but is not that easy or maybe im that noob

---

