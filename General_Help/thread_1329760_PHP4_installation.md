---
title: "PHP4 installation"
date: 2009-11-17
forum: General Help
---

### Post by Yarui on 2009-11-17
I am currently in a web development class and the server we have to submit assignments on is using PHP4.  Doing all my PHP work on the school's VPN has been unbearably slow so I would like to install PHP4 on my own computer to speed things up.  The only problem is that the Karmic repositories only have PHP5. What repositories do I need to add to install PHP4 instead? Does anyone have any good links to guides on PHP4 installation?

---

### Post by fluffman86 on 2009-11-17
You'll probably need to compile php4 yourself.  Check out the php website for more.

Don't worry, it won't be too hard.  A few tips: you'll need to 

sudo apt-get install build-essential

which will give you gcc, g++, etc.
and probably

sudo apt-get build-dep php5

which will build the dependencies of php automatically, so you only have to compile php4 itself.

---

### Post by Yarui on 2009-11-17
I have been looking around for PHP4 downloads and have had no luck so far.  Everything I find that talks about PHP4 is too old to be helpful, and everything else I can find is PHP5.

---

### Post by hjeffg on 2009-12-28
> **Yarui said:**
> I have been looking around for PHP4 downloads and have had no luck so far. Everything I find that talks about PHP4 is too old to be helpful, and everything else I can find is PHP5.
 
 
Did you ever get an answer to this?  I am also looking for how to install php4 on karmic.

---

### Post by chenxiaolong on 2009-12-28
Here's how you can install PHP4 in Ubuntu:

1. Install dependencies for PHP4.

```
sudo apt-get install build-essential flex bison libicu-dev libxml2-dev
```

2. Download PHP4 Source.

```
wget http://www.php.net/get/php-4.4.9.tar.gz/from/this/mirror
```

3. Configure [COLOR="SeaGreen"]Makefile[/COLOR] for compilation.

```
./configure --with-mysql
```

You can find more compile options by running:

```
./configure --help
```

4. Compile it.

```
make
```

5. Install it.

```
sudo make install
```

---

### Post by lewisforlife on 2009-12-28
PHP4 code will run fine if you have PHP5 installed.  All code is backwards compatible, so install PHP5 on your system.  Run your PHP4 code that you are learning in class on your PHP5 system.  And submit your PHP files to your teacher just as you do normally.  There is no way your teacher can know that you are using PHP5 at home and you should have no issues.

---

