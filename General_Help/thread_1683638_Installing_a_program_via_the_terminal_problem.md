---
title: "Installing a program via the terminal problem"
date: 2011-02-07
forum: General Help
---

### Post by Swerve1000 on 2011-02-07
Hi,

I am trying to install a voice recognition program called [CMU Sphinx]("http://cmusphinx.sourceforge.net/") on my Ubuntu 10.04.1 LTS Server Ed system.

I have been using this tutorial:
[http://www.speech.cs.cmu.edu/sphinx/tutorial.html#traintarball](http://www.speech.cs.cmu.edu/sphinx/tutorial.html#traintarball)

The installation tutorial says to use the following command:

> 
configure --prefix=`pwd`/build --with-sphinxbase=`pwd`/../sphinxbase


But when I run the command, I get the following output:

> 
:./configure: WARNING: Unrecognised options: --with- configure: error: expected an absolute directory name for --prefix: pwd/build 


I am thinking this maybe my lack of knowledge using terminal commands, and so was wondering if anyone could tel me where I'm going wrong.

Many thanks for any help with this, it's most appreciated :)

---

### Post by korleon on 2011-02-07
I'm fairly new to the command line as well, but here it goes..

> configure --prefix=`pwd`/build --with-sphinxbase=`pwd`/../sphinxbasethe last part is short hand for move up one level and then down to a location /sphinxbase.

Is it there and have you tried replacing the 

> `pwd`/../sphinxbase with the absolute path to sphinxbase?

for example:
> /parent_directory/sphinxbase 

---

### Post by Old *ix Geek on 2011-02-07
> **Swerve1000 said:**
> But when I run the command, I get the following output:> :./configure: WARNING: Unrecognised options: --with- configure: error: expected an absolute directory name for --prefix: pwd/build
Try running it by replacing **`pwd`/build** and **`pwd`/../sphinxbase** with the actual absolute path names. For example:
```
configure --prefix=**/DIRECTORY**/build --with-sphinxbase=**/DIRECTORY/SUBDIRECTORY**/sphinxbase
```

---

### Post by korleon on 2011-02-07
Thanks Old *ix Geek.  I defer you your expertise.

---

### Post by Swerve1000 on 2011-02-07
Thanks chaps!

I don't seem to have this 'build' directory.

Google seems to suggest installing the headers for my kernel?

Does that sound right?

---

### Post by korleon on 2011-02-07
Yes you can use uname -a and then search synaptic for the appropriate kernel headers.

---

### Post by wojox on 2011-02-07
Or just run this to install them:

```
sudo apt-get install linux-headers-$(uname -r)
```

---

