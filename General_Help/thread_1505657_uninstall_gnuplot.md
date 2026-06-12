---
title: "uninstall gnuplot"
date: 2010-06-09
forum: General Help
---

### Post by coyote_001 on 2010-06-09
Hello people... ):P

I have a problem with gnuplot and is driving me crazy.:confused:

A year ago I have installed gnuplot on my linux ubuntu 8.04. The gnuplot version I have is 
```
 
name@name:~$ gnuplot --version
gnuplot 4.2 patchlevel 2 

```

Now, in order to install the newest version of gnuplot I need to uninstall the old one and then install the gnuplot 4.4.0.

The way I installed the 4.2.2 version a year ago was with the 'make install' procedure.

Is there any way to uninstall the old gnuplot 4.2.2 and install the new gnuplot 4.4.0 ?

Thank you in advance, ;)
George.

---

### Post by anglican on 2010-06-09
> **coyote_001 said:**
> Hello people... ):P

I have a problem with gnuplot and is driving me crazy.:confused:

A year ago I have installed gnuplot on my linux ubuntu 8.04. The gnuplot version I have is 
```
 
name@name:~$ gnuplot --version
gnuplot 4.2 patchlevel 2 

```Now, in order to install the newest version of gnuplot I need to uninstall the old one and then install the gnuplot 4.4.0.

The way I installed the 4.2.2 version a year ago was with the 'make install' procedure.

Is there any way to uninstall the old gnuplot 4.2.2 and install the new gnuplot 4.4.0 ?

Thank you in advance, ;)
George.

sudo make uninstall

(Obviously in the gnuplot 4.2.2 source directory - assuming you haven't deleted it).

H

---

### Post by dino99 on 2010-06-09
goto synaptic and right click on the package to uninstall it, or install locate, then run it into a terminal:

locate gnuplot

then, sudo rm -f "/path/to/gnuplot* file" for each existing

not sure you need to do that anyway, as the new gnuplot will overwrite the previous (but thats the cleanest way)

---

### Post by coyote_001 on 2010-06-09
> **anglican said:**
> sudo make uninstall

(Obviously in the gnuplot 4.2.2 source directory - assuming you haven't deleted it).


I can't find gnuplot 4.2.2 in my source directory. I downloaded from [http://sourceforge.net/projects/gnuplot/files/]("http://sourceforge.net/projects/gnuplot/files/") the gnuplot 4.2.2 and I executed the 'make uninstall' command but with no results.


> **anglican said:**
> goto synaptic and right click on the package to uninstall it, or install locate, then run it into a terminal:

locate gnuplot

then, sudo rm -f "/path/to/gnuplot* file" for each existing

not sure you need to do that anyway, as the new gnuplot will overwrite the previous (but thats the cleanest way)


I installed gnuplot 4.2.2 with the 'make install' procedure and is not possible to uninstall the program from the synaptic package manager.

I enclose a text file with the results of the 'locate gnuplot' command. Not sure which files to delete.

---

### Post by SlidingHorn on 2010-06-09
you should be able to do it with apt:

```
sudo apt-get remove gnuplot
```

or if you need to get rid of all configuration info as well:

```
sudo apt-get remove --purge gnuplot
```

---

### Post by coyote_001 on 2010-06-09
> **SlidingHorn said:**
> you should be able to do it with apt:

```
sudo apt-get remove gnuplot
```

or if you need to get rid of all configuration info as well:

```
sudo apt-get remove --purge gnuplot
```

I can't do the removal through the 'apt-get remove' procedure. :sad:

As fas as I know :-k you can use this command when you want to remove a program which was installed by the synaptic package manager or by the command 'apt-get install'.

---

### Post by SlidingHorn on 2010-06-09
what's it give you when you try?

---

### Post by coyote_001 on 2010-06-09
> **SlidingHorn said:**
> what's it give you when you try?

It gives,
....
Package gnuplot is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 171 not upgraded.

---

### Post by anglican on 2010-06-10
> **coyote_001 said:**
> I can't find gnuplot 4.2.2 in my source directory. I downloaded from [http://sourceforge.net/projects/gnuplot/files/](http://sourceforge.net/projects/gnuplot/files/) the gnuplot 4.2.2 and I executed the 'make uninstall' command but with no results.




I installed gnuplot 4.2.2 with the 'make install' procedure and is not possible to uninstall the program from the synaptic package manager.

I enclose a text file with the results of the 'locate gnuplot' command. Not sure which files to delete.
"sudo make uninstall" is still the way I'd go with this. If you have reinstalled the source you will need to "./configure" and "make" before you can "sudo make uninstall" otherwise whenever make enters a directory it will find nothing to do.

All the answers that have referred to apt-get or any other package management tool **wont work** because gnuplot was not installed by a package management program. None of them will know anything about a package that has been installed by "make install". That is one of the reasons not to install software that way! The best way to remove a package installed by "make install" is "make uninstall". You can try and find all the files that were installed and delete them manually but you may not find them all and left over files may interfere with installing via the package management system so "sudo make uninstall" is by far the best approach.

> [SIZE=2]_The lesson here is that if you install by "./configure; make; sudo make install" do not delete the source directories which are your route to uninstalling._[/SIZE]

H

---

### Post by coyote_001 on 2010-06-10
> **anglican said:**
> The lesson here is that if you install by "./configure; make; sudo make install" do not delete the source directories which are your route to uninstalling.  


But still... :confused: Wouldn't be funny if someone using one of the best operating systems cannot uninstall a program ? I think yes..... ;)

Nevertheless, I think there is a solution and I'll wait for the user who knows the answer...

---

### Post by anglican on 2010-06-11
> **coyote_001 said:**
> But still... :confused: Wouldn't be funny if someone using one of the best operating systems cannot uninstall a program ? I think yes..... ;)

Nevertheless, I think there is a solution and I'll wait for the user who knows the answer...
"sudo make uninstall" **is** the answer... I doubt that anyone will be able to suggest anything else that actually works. It's the simple reverse of "sudo make install". Why don't you like this answer?

H

---

### Post by schwan on 2010-08-10
Hi guys,

seems that I am also running into the same problem. I have tried the make uninstall, and all the other suggestions here. I even did removed it from synpatic, however, it still seems to be on the system since i still can start gnuplot and since there are lots of files if i locate gnuplot. Can you please help me out or tell me a way how to update the 4.2 to 4.4?

Thanks a lot in advance,

Schwan

---

