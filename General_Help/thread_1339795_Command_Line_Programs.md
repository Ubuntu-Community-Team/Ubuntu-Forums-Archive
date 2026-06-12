---
title: "Command Line Programs"
date: 2009-11-27
forum: General Help
---

### Post by dyess002 on 2009-11-27
Is there a way to tell what command line programs are installed on your PC?
I have installed programs and didn't get to try them right away and I have forgot about what I have an what it does.
Also I have installed programs on here that should show up in my menu but it doesn't. I have looked in Main Menu but they are not there. But they show up in a search but I can't find a Exe file to start the program up.
I have programs on here that I have forgotten about because I couldn't get it to work or couldn't find it after I installed.


Thanks
David Dyess

---

### Post by lisati on 2009-11-27
First hint: don't go looking specifically for an "EXE" file - these are usually designed for MS-DOS or Windows, and won't run on Ubuntu without help.
Second hint: some program names are the same as the package name.

---

### Post by shaggy999 on 2009-11-28
You might want to look into the package 'apt-file'. I find it really useful when I install a package but can't seem to locate the appropriate program. After running an initial update you can type 'apt-file show *package_name*' and it shows all the files installed on your system related to the package and their locations. Then you can look through the file list to locate the program you need to execute.

---

### Post by dyess002 on 2009-11-28
> **lisati said:**
> First hint: don't go looking specifically for an "EXE" file - these are usually designed for MS-DOS or Windows, and won't run on Ubuntu without help.
Second hint: some program names are the same as the package name.



lisati 
I was using the EXE as an illustration for the file the you would double click to get it to run.
I didn't make myself clear.
I would like to get Icons on all of my software that I have installed. and the command line tools you can't put icons on them so I would like to find out where to see a list of installed command line tools so I can go back and learn about them. If I don't see them every now and again I will forget about them nor will I learn how to use them.

Thanks lisati
David Dyess

---

### Post by dyess002 on 2009-11-28
> **shaggy999 said:**
> You might want to look into the package 'apt-file'. I find it really useful when I install a package but can't seem to locate the appropriate program. After running an initial update you can type 'apt-file show *package_name*' and it shows all the files installed on your system related to the package and their locations. Then you can look through the file list to locate the program you need to execute.


Ok on the command line programs how would I find the command that I should use to get it running?

thanks
David Dyess

---

### Post by shaggy999 on 2009-11-28
To install apt-file just:

```
sudo apt-get install apt-file
```

then apt-file needs to be updated so:

```
sudo apt-file update
```

Then let's say you installed something like the 'secure-delete' package. To see what files it installed you type:

```
apt-file show secure-delete
```

and you get output like this:

```
secure-delete: /usr/bin/sfill
secure-delete: /usr/bin/smem
secure-delete: /usr/bin/srm
secure-delete: /usr/bin/sswap
secure-delete: /usr/share/doc/secure-delete/README.Debian
secure-delete: /usr/share/doc/secure-delete/README.gz
secure-delete: /usr/share/doc/secure-delete/TODO
secure-delete: /usr/share/doc/secure-delete/changelog.Debian.gz
secure-delete: /usr/share/doc/secure-delete/changelog.gz
secure-delete: /usr/share/doc/secure-delete/copyright
secure-delete: /usr/share/doc/secure-delete/secure_delete.doc.gz
secure-delete: /usr/share/doc/secure-delete/usenix6-gutmann.doc.gz
secure-delete: /usr/share/man/man1/sfill.1.gz
secure-delete: /usr/share/man/man1/smem.1.gz
secure-delete: /usr/share/man/man1/srm.1.gz
secure-delete: /usr/share/man/man1/sswap.1.gz
```

Clearly in this example there are 4 binaries installed with this package: sfill, smem, srm, and sswap. To learn how to use these programs you use the man pages:

ex:
```
man sfill
```


There really isn't a "list of commandline programs". There is no distinction between a commandline and a gui program and when you install a package the package manager makes no distinction between packages that have programs and packages that merely contain data. A good starting point is to find out what *packages* you have installed on your system, which you can do using this command:

```
dpkg --get-selections
```

---

### Post by dyess002 on 2009-11-28
Wow
Thanks [shaggy999]("http://ubuntuforums.org/member.php?u=319156")
That was a lot to chew on. I will start learning Right away
I didn't know about the man thing.

---

### Post by TracyO on 2010-02-07
Hey Dyess,

Did you figure out how to open non-menu programs from the command line?  That's what I'm trying to get.  

Thanks!

---

### Post by dyess002 on 2010-02-15
Sometimes you can just type the name of the program in the Terminal, if that doesn't work you have to go to the Man Doc.

---

