---
title: "How to update Gaim?"
date: 2006-03-30
forum: General Help
---

### Post by nominal on 2006-03-30
I wanna update my Gaim to the new beta release--which i just found out about, however, i can't. There is NOT a file for ubuntu linux, yet there is one for other types of linux. Can anyone tell me what i should do to d/l it and install?

---

### Post by xXx 0wn3d xXx on 2006-03-30
[QUOTE=nominal]I wanna update my Gaim to the new beta release--which i just found out about, however, i can't. There is NOT a file for ubuntu linux, yet there is one for other types of linux. Can anyone tell me what i should do to d/l it and install?[/QUOTE]
Just download the tar.gz file and then compile it. Simple as that :)

---

### Post by towsonu2003 on 2006-03-30
[QUOTE=nominal]I wanna update my Gaim to the new beta release--which i just found out about, however, i can't. There is NOT a file for ubuntu linux, yet there is one for other types of linux. Can anyone tell me what i should do to d/l it and install?[/QUOTE]
You've got 2 options (that I can think of) to get the newest version. I'm not sure if it's worth doing any of them for gaim, but: relativity of personal needs ;) Remove the existing gaim using synaptic and try one of the followings

1. If it has a rpm package, use alien to convert it to .deb and try installing it with dpkg. you will want to search the forum on how to use alien. to install the resulting .deb package, do sudo dpkg -i /path/to/package.deb (this may or may not work). 

2. compile from source (just hard).

---

### Post by nominal on 2006-03-30
errr how do i compile it (please don't yell!)

---

### Post by jawbreaker on 2006-03-30
[QUOTE=nominal]I wanna update my Gaim to the new beta release--which i just found out about, however, i can't. There is NOT a file for ubuntu linux, yet there is one for other types of linux. Can anyone tell me what i should do to d/l it and install?[/QUOTE]

You must have missed this post:
[HOWTO: Gaim 2.0 CVS - .deb inside]("http://ubuntuforums.org/showpost.php?p=556060&postcount=1")

Or you didn't search the forums. That was the first result with: gaim beta package

---

### Post by nominal on 2006-03-30
i checked out the link and i don't know how to use the info on the page....i put the code into the terminal but it says bash: cvs

Also i have the tar of game beta 3...and i dpkg it, now how do i compile?

---

### Post by jawbreaker on 2006-03-30
[QUOTE=nominal]i checked out the link and i don't know how to use the info on the page....i put the code into the terminal but it says bash: cvs

Also i have the tar of game beta 3...and i dpkg it, now how do i compile?[/QUOTE]

You don't have to compile anything. There is a precompiled package that link.

Use file-roller (or ark if you use KDE) to extract the DEB.
Or you can use the command line:
tar xfz gaim_2.0.0beta3.tar.gz

Then uninstall your old Gaim:
sudo apt-get --purge remove gaim

Then install the new DEB:
sudo dpkg -i gaim_2.0.0beta3-1_i386.deb

Now open synaptic and search for: gaim
You should see gaim version 2.0.0beta3-1 installed. Highlight it, go to the package menu and select: lock version
(this keeps the update-notifier from trying to update back to the old package)

That's it.

---

### Post by dunomous on 2006-04-07
> 
Then install the new DEB:
sudo dpkg -i gaim_2.0.0beta3-1_i386.deb


yeahh.....doesn't exist when I extracted it and used that command. I have no idea where the DEB is.

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=dunomous]yeahh.....doesn't exist when I extracted it and used that command. I have no idea where the DEB is.[/QUOTE]
it's possibly under ~/gaim_2.0.0beta3/ or similar.

you could also do ```
sudo updatedb
locate gaim_2.0.0beta3
```

sudo updatedb is not required if it was run prior to file creation (by, for example, a pre-configured cron job).

---

### Post by dunomous on 2006-04-07
yeah, when I did that, it gave me a split error though

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=dunomous]yeah, when I did that, it gave me a split error though[/QUOTE]
have no idea what a split error is, sorry :(

---

### Post by dunomous on 2006-04-07
```

user@name:~/Desktop$ sudo dpkg -i gaim-2.0.0beta3
dpkg-split: error reading gaim-2.0.0beta3: Is a directory
dpkg: error processing gaim-2.0.0beta3 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 gaim-2.0.0beta3

```

---

### Post by graigsmith on 2006-04-07
if you wanna start compiling things you will first need the build-essential package.

then you basically unzip the source package to a directory.

and navigate to it in the command prompt, and type

./configure

then you will be notified of missing libraries or whatever, they can usually be downloaded with synaptic.  if you dont get any errors after the ./configure, then you do 

make

and it should build it.  then after its done, you should be able to run it.
thats basically how you compile a program.  pretty easy.

---

### Post by dunomous on 2006-04-07
yes, just did that actually. Now I'm looking for something called GLIB?

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=dunomous]```

user@name:~/Desktop$ sudo dpkg -i gaim-2.0.0beta3
dpkg-split: error reading gaim-2.0.0beta3: Is a directory
dpkg: error processing gaim-2.0.0beta3 (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 gaim-2.0.0beta3

```[/QUOTE]
lol

do the following ```
cd gaim-2.0.0beta3
sudo dpkg -i gaim-2.0.0beta3.deb
``` supposing that gaim-2.0.0beta3.deb is the correct name of the .deb file. 

1st will navigate you to the directory gaim-2.0.0beta3, second will install file gaim-2.0.0beta3.deb under that gaim-2.0.0beta3 directory. lol again :) 

assuming that what I say will work, that's cute ;) no offense ;)

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=dunomous]yes, just did that actually. Now I'm looking for something called GLIB?[/QUOTE]
sudo apt-get install libglib2.0-dev
should do it for compiling (unless there are other dependencies). no deb files under .tar.gz as per [http://ubuntuforums.org/showpost.php?p=900669&postcount=15](http://ubuntuforums.org/showpost.php?p=900669&postcount=15) ?

---

### Post by dunomous on 2006-04-07
hmmm, greeaaaat

```

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.configure: error:
*** GTK+ 2.0 is required to build Gaim; please make sure you have the GTK+
*** development headers installed. The latest version of GTK+ is
*** always available at http://www.gtk.org/.

```

However, upon checking my package manager, it is installed, I suppose just not some key components. Or at least I think it's using 2.0.

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=dunomous]hmmm, greeaaaat

```

checking for GTK+ - version >= 2.0.0... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GTK+ is incorrectly installed.configure: error:
*** GTK+ 2.0 is required to build Gaim; please make sure you have the GTK+
*** development headers installed. The latest version of GTK+ is
*** always available at http://www.gtk.org/.

```

However, upon checking my package manager, it is installed, I suppose just not some key components. Or at least I think it's using 2.0.[/QUOTE]
sudo apt-get install libgtk2.0-dev

---

### Post by towsonu2003 on 2006-04-07
didn't this one say .deb file was in link s/he gave? [http://ubuntuforums.org/showpost.php?p=877467&postcount=5](http://ubuntuforums.org/showpost.php?p=877467&postcount=5)

---

### Post by dunomous on 2006-04-07
I take it `lib' means library?

And that link is for the second beta, not the third, if I'm not mistaken.

---

### Post by towsonu2003 on 2006-04-07
[QUOTE=dunomous]I take it `lib' means library?
[/quote]
yes. and -dev means the development libraries / headers (for compilation).
[QUOTE=dunomous] 
And that link is for the second beta, not the third, if I'm not mistaken.[/QUOTE]
oh, okay. having dial up, I just didn't check it... (slow)

you can use checkinstall when you are going to install the finished binary: ```
sudo apt-get install checkinstall
```
it creates a .deb and installs it using dpkg (so you can easily remove it when the time comes tru synaptic). so during compilation, what was once: 
./configure
make
sudo make install

becomes:
./configure
make
sudo make checkinstall

you will need to remove the previous gaim beforehand though tru synaptic/apt-get.

---

### Post by dunomous on 2006-04-07
hmm, well, see once I configured, then typed make, all that went fine. Now opening the file is a problem. Meaning, how...do I open the new one? apparently I'll have to change the commands on all the icon launches



-edit-

oops, wait, before you reply, I accidently deleted my folder. sigh...sad. one sec.

---

### Post by dunomous on 2006-04-07
ok, yeah. can't open it : /

---

### Post by graigsmith on 2006-04-07
it should be under one of the directories that is in the source folder.

---

### Post by graigsmith on 2006-04-07
actually i just compiled it, it compiled it as "Gaim Instant Messenger"

---

### Post by dunomous on 2006-04-07
compile by using the `make' command correct? becuase that compiles correctly, but I get errors on `make install'.

****This is after typing `make' a second time.*****

```

Making install in doc
make[1]: Entering directory `/home/thomas/gaim-2.0.0beta3/doc'
make[2]: Entering directory `/home/thomas/gaim-2.0.0beta3/doc'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/man/man1" || mkdir -p -- . "/usr/local/man/man1"
mkdir: cannot create directory `/usr/local/man': File exists
make[2]: *** [install-man1] Error 1
make[2]: Leaving directory `/home/thomas/gaim-2.0.0beta3/doc'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/thomas/gaim-2.0.0beta3/doc'
make: *** [install-recursive] Error 1

```

---

### Post by dunomous on 2006-04-07
I suppose I'm just confused on where to put the folder?

---

