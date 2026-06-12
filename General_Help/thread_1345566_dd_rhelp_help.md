---
title: "dd_rhelp help"
date: 2009-12-04
forum: General Help
---

### Post by chilihotorcold on 2009-12-04
Keeping a long story short, I've been here 
[http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html](http://www.ubuntugeek.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html)

trying to get this to work. I've followed this guide all the way to "Run the following commands". I try to run the command "sudo ./configure" but this is what it says

~/dd_rhelp-0.1.2$ sudo ./configure
sudo: ./configure: command not found
dontdownloadstuff@ubuntu:~/dd_rhelp-0.1.2$

Any help would be much appreciated!

---

### Post by chilihotorcold on 2009-12-04
Help PLZ!!

---

### Post by hal10000 on 2009-12-04
If you lookinto the INSTALL file that comes with the package, you can see that the installation process for newer versions is much easier than described on the site.

if you do not already have a **bin** directory in your home folder, then create it first:
```
mkdir ~/bin
```

then just copy the bash script from the directory where you unzipped the package to your ~/bin directory:
```
cp ~/dd_rhelp-0.1.2/dd_rhelp ~/bin
```

That's all. you can run the script by just typing **dd_rhelp** on a terminal window.

---

### Post by t0p on 2009-12-04
> **chilihotorcold said:**
>  I try to run the command "sudo ./configure" but this is what it says

~/dd_rhelp-0.1.2$ sudo ./configure
sudo: ./configure: command not found
dontdownloadstuff@ubuntu:~/dd_rhelp-0.1.2$


There are a couple of potential answers to this:

1.  You don't have installed on your computer all the software necessary to build software.  You need to install **build-essential**:

```
sudo apt-get install build-essential
```2.  Rather than using *sudo* with the configure command, you might need to use a temporary root shell.  Do this by typing into the terminal:

```
sudo -s
```This gives you a root shell (hence the '#' symbol in your bash prompt rather than the usual '$').  Now you don't need to prefix commands with *sudo*.  Just make sure you exit this shell (eg by using the command **exit** or by closing the terminal) when you've finished.

---

### Post by hal10000 on 2009-12-04
> There are a couple of potential answers to this

In this special case there is only one simple answer: Newer versions of this tool don't have a configure script, because the installation process has been simplified, see posting #3.

---

### Post by chilihotorcold on 2009-12-04
> **hal10000 said:**
> If you lookinto the INSTALL file that comes with the package, you can see that the installation process for newer versions is much easier than described on the site.

if you do not already have a **bin** directory in your home folder, then create it first:
```
mkdir ~/bin
```then just copy the bash script from the directory where you unzipped the package to your ~/bin directory:
```
cp ~/dd_rhelp-0.1.2/dd_rhelp ~/bin
```That's all. you can run the script by just typing **dd_rhelp** on a terminal window.

Thanks for replying!!
I ran both those commands and have mad a bin folder at my home folder. But trying to run dd_rhelp is still not working. Even after installing the essential

dontdownloadstuff@ubuntu:~$ dd_rhelp
dd_rhelp: command not found
dontdownloadstuff@ubuntu:~$ 



> **t0p said:**
> There are a couple of potential answers to this:

1.  You don't have installed on your computer all the software necessary to build software.  You need to install **build-essential**:

```
sudo apt-get install build-essential
```2.  Rather than using *sudo* with the configure command, you might need to use a temporary root shell.  Do this by typing into the terminal:

```
sudo -s
```This gives you a root shell (hence the '#' symbol in your bash prompt rather than the usual '$').  Now you don't need to prefix commands with *sudo*.  Just make sure you exit this shell (eg by using the command **exit** or by closing the terminal) when you've finished.

I didnt have the essential build installed and have done so now. But I cannot still run the configure command.

~/dd_rhelp-0.1.2$ sudo ./configure
sudo: ./configure: command not found
dontdownloadstuff@ubuntu:~/dd_rhelp-0.1.2$ 

How would the command look like in sudo -s?

---

### Post by cariboo on 2009-12-04
Why not just install ddrescue from the repositories?

---

### Post by chilihotorcold on 2009-12-04
I've read that dd_rhelp is more effective

---

### Post by chilihotorcold on 2009-12-04
After some playing around, I got it to work. But now my gparted isn't working. Any ideas?
I ran the command 

dd_rhelp /dev/sdb /dev/sda2 info

and got this

'/dev/sdb' is not readable.
dd_rhelp: error: Please specify a usable file as first argument.
dontdownloadstuff@ubuntu:~/dd_rhelp-0.1.2$ 

does that mean I cannot do it until I partion or format that drive or would I lose all the information if I did that?

---

### Post by chilihotorcold on 2009-12-04
bump

---

### Post by Some Penguin on 2009-12-04
> **chilihotorcold said:**
> After some playing around, I got it to work. But now my gparted isn't working. Any ideas?

"Isn't working" isn't useful.  Be more specific regarding what you did, what you expected to happen and what happened.

> 
I ran the command 

dd_rhelp /dev/sdb /dev/sda2 info

and got this

'/dev/sdb' is not readable.
dd_rhelp: error: Please specify a usable file as first argument.
dontdownloadstuff@ubuntu:~/dd_rhelp-0.1.2$ 

does that mean I cannot do it until I partion or format that drive or would I lose all the information if I did that?

'Not readable' would be consistent with a permissions problem.  Consider running that as root (via sudo), because an ordinary user may not have permission to read directly from /dev/sdb (which would pose obvious security issues, if it were allowed).

---

### Post by chilihotorcold on 2009-12-04
When I try to open gparted it shows its loading, but then just closes it self.

command not found while trying to run under sudo

---

### Post by chilihotorcold on 2009-12-04
bump

---

