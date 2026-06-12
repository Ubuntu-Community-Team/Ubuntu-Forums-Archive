---
title: "How do I install a program with extension .tgz?"
date: 2010-10-15
forum: General Help
---

### Post by Coco999 on 2010-10-15
I wanted to try my hand at programming in an easy way, so I installed from the Ubuntu Software Center Basic-256. But it is more than 3 years old and does not fit to a book I downloaded. I got from Sourceforge the latest version which is a .tgz file. How do I install it?

---

### Post by Woody1987 on 2010-10-15
.tgz is an archive like zip or rar. Right click on the file and select 'Extract Here'. I should warn you that installing software not in the software centre can be tricky and will not always work without some advanced knowledge. Looking at the basic website, the software despite being 3 years old isn't that behind compared to the latest. I strongly recommend getting the software centre version.

---

### Post by Coco999 on 2010-10-15
Thank you Woody. Perhaps I could use the old version as supplied (0.9.2), but I downloaded the book So You Want to Learn to
Program? by James M. Reneau, M.S. and several points don't fit at all. In addition the old version may have some bugs. In my first trials several times it froze and I had to close it and then reopen again. So I may rephrase mu question as: How do I get a reliable new version and how do I install it?

By the way, the new version is 0.9.6.42, so a lot of water has gone under the bridge.

---

### Post by Woody1987 on 2010-10-15
I have found a later version (9.6.32) in deb form. It comes from Debian but should work fine. [http://packages.debian.org/sid/basic256](http://packages.debian.org/sid/basic256) At the bottom, choose your architecture and download. I tried installing the 64bit version and it worked fine.

---

### Post by Coco999 on 2010-10-15
I've downloaded basic256_0.9.6.32-1_i386.deb that ought to be better than what I have. But again, I don't know how to install it. Please help me.

---

### Post by VCoolio on 2010-10-15
A .deb file you can just (double)click and it will open with an installer program. Or in a terminal do 'sudo dpkg -i file.deb'. Debs are ok, your package manager will know about them (as oppposed to manually compiling and installing source packages like in .tar.gz).

---

### Post by garvinrick4 on 2010-10-15
{  }  ```
Suppose you have a source file name src.tar.gz, what you do initially is that you need to extract the source files and then in the terminal&#8230;. 
navigate to the folder where the source file is extracted using the cd commands&#8230;.. and then 
type the following&#8230; 

./configure 

make 

sudo make install 

clean install 

lets see what each one of them does&#8230; 

./configure&#8230;.. checks whether the required dependencies are available on your system or not&#8230;.. if not an error is reported&#8230;. 

make...... compiles the source code and make install is used to install the program in to the location 

if it asks for an installation location it is recommended to install all the source to /usr/src 

clean install...... removes any temporary files created in the installation process of the source and thats it your source file in installed in your system. 

```

---

### Post by Coco999 on 2010-10-15
Thank you. But I failed on both intents.

1. I clicked on the file (once was enough) and an installer appeared, but could not finish. It gave me a warning in red letters:

> Error: Dependency is not satisfiable: libsqlite3-0 (>= 3.7.2)

Which I don't understand.

2. On a terminal I got the following:

```
coco@coco-desktop:~/Escritorio$ do 'sudo dpkg -i basic256_0.9.6.32-1_i386.deb
bash: syntax error near unexpected token `do'
coco@coco-desktop:~/Escritorio$ 
```

Again I don't know what to do.

---

### Post by Coco999 on 2010-10-15
garvinrick4

Thank you, but I failed again. I extracted the file and placed it into Escritorio. This is what I got:


```
coco@coco-desktop:~/Escritorio/basic256_0.9.6.42$ ./configure 
bash: ./configure: No such file or directory
coco@coco-desktop:~/Escritorio/basic256_0.9.6.42$ 
coco@coco-desktop:~/Escritorio/basic256_0.9.6.42$ make 
make: *** No rule to make target `/usr/share/qt4/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
coco@coco-desktop:~/Escritorio/basic256_0.9.6.42$ 
coco@coco-desktop:~/Escritorio/basic256_0.9.6.42$ sudo make install 
[sudo] password for coco: 
make: *** No rule to make target `/usr/share/qt4/mkspecs/linux-g++/qmake.conf', needed by `Makefile'.  Stop.
coco@coco-desktop:~/Escritorio/basic256_0.9.6.42$ 
```

I don't know what to do now.

---

### Post by VCoolio on 2010-10-16
> **Coco999 said:**
> Thank you. But I failed on both intents.

1. I clicked on the file (once was enough) and an installer appeared, but could not finish. It gave me a warning in red letters:


Which I don't understand.
It means it needs that package as dependency. If you're on maverick, install libsqlite3-0. It needs version 3.7.2 or higher, and maverick has that. If you have an older ubuntu, you need to find a .deb or a repository (on launchpad.net for instance) to install it.

> 
2. On a terminal I got the following:

```
coco@coco-desktop:~/Escritorio$ do 'sudo dpkg -i basic256_0.9.6.32-1_i386.deb
bash: syntax error near unexpected token `do'
coco@coco-desktop:~/Escritorio$ 
```

Again I don't know what to do.

Don't do 'do sudo etc' but 'sudo dpkg -i file.deb'. But it will give you the same dependency error as clicking the .deb does.

---

### Post by Coco999 on 2010-10-16
> **VCoolio said:**
> It means it needs that package as dependency. If you're on maverick, install libsqlite3-0. It needs version 3.7.2 or higher, and maverick has that. If you have an older ubuntu, you need to find a .deb or a repository (on launchpad.net for instance) to install it.



Don't do 'do sudo etc' but 'sudo dpkg -i file.deb'. But it will give you the same dependency error as clicking the .deb does.

Thank you, but I have not maverick. My Ubuntu is 10.4.

I've downloaded from Launchpad.net the file libsqlite3-0_3.7.2-1_i386.deb (372.1 KiB) How do I install it? Or better, how do I upgrade to 10.10?

---

### Post by d5xtgr on 2010-10-16
That one you should be able to double-click and have it install, unless it in turn depends on another package.

To upgrade, go to System/ Admin/ Update Manager/ Settings / Show new distros and set it to normal.  Then follow the prompts to upgrade to 10.10.

---

### Post by thuntley on 2010-10-16
Maybe I'm a little late to the game here, but I believe that .tgz is a Slackware package which is a bit different from a standard archive file.  See the link below.
[http://slacksite.com/slackware/packages.html](http://slacksite.com/slackware/packages.html)

---

