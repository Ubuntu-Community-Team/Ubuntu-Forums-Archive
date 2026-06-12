---
title: "Using CLI to run a program"
date: 2011-07-18
forum: General Help
---

### Post by felinoel on 2011-07-18
I found some outdated instructions issued by a company on how to install and run a program but have hit an error... x.x

```
michael@michael-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

The instructions specifically say to do this, why is there no rule to make target install?






[QUOTE="Original Post, has since been solved"]
[SIZE="1"]Ok so I want to use this Minecraft server that uses Hamachi to attach a password to it, but the Hamachi software available for Ubuntu is in beta so it only has a CLI function.

[https://secure.logmein.com/US/labs/](https://secure.logmein.com/US/labs/)

How do I run this? I also assume I would need to be able to find it too... 

I installed the .deb one.[/SIZE][/QUOTE]

---

### Post by Habitual on 2011-07-18
[http://ubuntuforums.org/search.php?searchid=82064189](http://ubuntuforums.org/search.php?searchid=82064189)

---

### Post by felinoel on 2011-07-18
> **Habitual said:**
> [http://ubuntuforums.org/search.php?searchid=82064189](http://ubuntuforums.org/search.php?searchid=82064189)

I tried searching already but the threads that looked like they were titled about what I was looking for didn't help me, plus I wouldn't know what the program is called to tell the CLI to run

---

### Post by bodhi.zazen on 2011-07-19
Not sure how that link helps either ???

At any rate see:

[http://ericlefevre.net/wordpress/2010/07/30/how-to-use-logmein-under-linux/](http://ericlefevre.net/wordpress/2010/07/30/how-to-use-logmein-under-linux/)

[http://www.makeuseof.com/tag/logmein-linux-access-logmein-computers-linux-computers/](http://www.makeuseof.com/tag/logmein-linux-access-logmein-computers-linux-computers/)

---

### Post by felinoel on 2011-07-19
> **bodhi.zazen said:**
> Not sure how that link helps either ???

At any rate see:

[http://ericlefevre.net/wordpress/2010/07/30/how-to-use-logmein-under-linux/](http://ericlefevre.net/wordpress/2010/07/30/how-to-use-logmein-under-linux/)

[http://www.makeuseof.com/tag/logmein-linux-access-logmein-computers-linux-computers/](http://www.makeuseof.com/tag/logmein-linux-access-logmein-computers-linux-computers/)

Thanks! But I found some outdated instructions issued by the company on how to install and run it but have hit an error... x.x

```
michael@michael-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.

```

The instructions specifically say to do this, why is there no rule to make target install?

[This guy is having the same issue...](http://ubuntuforums.org/showthread.php?t=1786537&highlight=rule+make+target+install)

---

### Post by bodhi.zazen on 2011-07-19
There are several things you need to install (compile) packages, and typically there is a README you should read.

Install build essential

Then typically you 

./configure
make
sudo make install

See : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

If you have problems with the installation it is usually due to dependencies. If you have problems beyond that you will need to contact the authors for support.

---

### Post by felinoel on 2011-07-19
> **bodhi.zazen said:**
> There are several things you need to install (compile) packages, and typically there is a README you should read.

Install build essential

Then typically you 

./configure
make
sudo make install

See : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

If you have problems with the installation it is usually due to dependencies. If you have problems beyond that you will need to contact the authors for support.```
michael@michael-laptop:~$ install build essential
install: cannot stat `build': No such file or directory

```?


I went and did what that link said to do and I still get that no rule to make target install stop message, maybe I missed a step?


I already emailed the company a day or two ago, awaiting response.

---

### Post by bodhi.zazen on 2011-07-19
> **felinoel said:**
> ```
michael@michael-laptop:~$ install build essential
install: cannot stat `build': No such file or directory

```?


I went and did what that link said to do and I still get that no rule to make target install stop message, maybe I missed a step?


I already emailed the company a day or two ago, awaiting response.

Read step 1 of the link I gave you : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by felinoel on 2011-07-19
> **bodhi.zazen said:**
> Read step 1 of the link I gave you : [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

I had done step one? I can try doing it again I guess?

---

### Post by powerpleb on 2011-07-19
> **felinoel said:**
> ```
michael@michael-laptop:~$ install build essential
```
```
sudo apt-get install build-essential checkinstall
```
Now spot the difference between what you typed and what the page told you to type. :P

---

### Post by felinoel on 2011-07-19
> **powerpleb said:**
> ```
sudo apt-get install build-essential checkinstall
```
Now spot the difference between what you typed and what the page told you to type. :P

I followed the page exactly, that was a response to what the person I quoted said, here is the log of me doing it again

```
michael@michael-laptop:~$ sudo make install
[sudo] password for michael: 
make: *** No rule to make target `install'.  Stop.
michael@michael-laptop:~$ sudo apt-get install build-essential checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
checkinstall is already the newest version.
The following packages were automatically installed and are no longer required:
  gwibber-service python-mako linux-headers-2.6.32-25 python-pycurl
  python-gtkspell python-egenix-mxdatetime python-egenix-mxtools
  linux-headers-2.6.32-25-generic python-indicate
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
michael@michael-laptop:~$ sudo apt-get install cvs subversion git-core mercurial 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cvs is already the newest version.
subversion is already the newest version.
git-core is already the newest version.
mercurial is already the newest version.
The following packages were automatically installed and are no longer required:
  gwibber-service python-mako linux-headers-2.6.32-25 python-pycurl
  python-gtkspell python-egenix-mxdatetime python-egenix-mxtools
  linux-headers-2.6.32-25-generic python-indicate
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
michael@michael-laptop:~$ sudo chown $USER /usr/local/src
michael@michael-laptop:~$ sudo chmod u+rwx /usr/local/src
michael@michael-laptop:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
michael@michael-laptop:~$ 

```

---

### Post by WorMzy on 2011-07-19
```
michael@michael-laptop:~$ sudo make install
```

Is the source code in your home folder? I'm guessing not. Despite this, you're running that command from your home folder (~). Use cd to move to the folder containing the source code.

Then, depending on what the developers have provided you, run

```
./configure
```
followed by
```
make
```

and then, and ONLY then, assuming you get no errors

run:
```
sudo make install
```

If you do get an error during the first two commands, post it here.

---

### Post by felinoel on 2011-07-19
> **WorMzy said:**
> ```
michael@michael-laptop:~$ sudo make install
```

Is the source code in your home folder? I'm guessing not. Despite this, you're running that command from your home folder (~). Use cd to move to the folder containing the source code.

Then, depending on what the developers have provided you, run

```
./configure
```
followed by
```
make
```

and then, and ONLY then, assuming you get no errors

run:
```
sudo make install
```

If you do get an error during the first two commands, post it here.
I noticed it was accessing from the home folder so I copied the files I downloaded from the site there just in case? Are the files not the source code? Should it install even though all I say is just install and not what to install?

---

### Post by felinoel on 2011-07-19
> **bodhi.zazen said:**
> typically there is a README you should read.

I found the elusive readme! o.o

---

### Post by felinoel on 2011-07-19
> **felinoel said:**
> I found the elusive readme! o.o

From this, coupled with some help from this thread, I think it is up and running, thanks all!

---

### Post by bodhi.zazen on 2011-07-19
Now you know why the call it README =)

---

