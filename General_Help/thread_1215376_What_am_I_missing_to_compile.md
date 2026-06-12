---
title: "What am I missing to compile?"
date: 2009-07-17
forum: General Help
---

### Post by s3a on 2009-07-17
I'm following this guide ([http://fredbrunel.com/journal/2004/03/stow/](http://fredbrunel.com/journal/2004/03/stow/)). If you've never heard of stow before, assume the whole stow and prefix business means sudo make install since both commands give me the same error. I did sudo apt-get install build-essential. Other than this, I do not know what I am missing nor do I understand the output of the command I entered. The following is what's going on in my terminal window:

[I]ubuntu@ubuntu:~$ cd /home/ubuntu/Desktop/backintime-0.9.26/gnome
ubuntu@ubuntu:~/Desktop/backintime-0.9.26/gnome$ ./configure
All OK. Now run:
    make
    sudo make install
ubuntu@ubuntu:~/Desktop/backintime-0.9.26/gnome$ make
make: Nothing to be done for `all'.
ubuntu@ubuntu:~/Desktop/backintime-0.9.26/gnome$ sudo make install prefix=/usr/local/stow/backintime-0.9.26
#install python
install -d /usr/share/backintime/gnome
install --mode=644 *.py /usr/share/backintime/gnome
install --mode=644 *.glade /usr/share/backintime/gnome
#install plugin
install -d /usr/share/backintime/plugins
install --mode=644 ../plugins/gnome*.py /usr/share/backintime/plugins
#install copyright file
install -d /usr/share/doc/backintime-gnome
install --mode=644 ../common/debian_specific/copyright /usr/share/doc/backintime-gnome
#install man file(s)
install -d /usr/share/man/man1
install --mode=644 man/C/*.gz /usr/share/man/man1
#install application
install -d /usr/bin
install backintime-gnome /usr/bin
#install .desktop file(s)
install -d /usr/share/applications
install --mode=644 *.desktop /usr/share/applications
#install gnome-help file(s)
install -d /usr/share/gnome/help/backintime/C/figures
install --mode=644 docbook/C/*.xml /usr/share/gnome/help/backintime/C
install --mode=644 docbook/C/figures/*.png /usr/share/gnome/help/backintime/C/figures
install -d /usr/share/omf/backintime
install --mode=644 docbook/C/*.omf /usr/share/omf/backintime
ubuntu@ubuntu:~/Desktop/backintime-0.9.26/gnome$[/I]

As you might have noticed, I am running a Live CD in order to prevent myself from ruining things while I'm learning ;)

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by mcduck on 2009-07-17
I don't see any error there, seems like the install completed succesfully.

---

### Post by s3a on 2009-07-24
Sorry for the late update but it only works when I cd to the source directory. Otherwise it gives an error.

deniz@debian:~$ cd Desktop/backintime-0.9.26
deniz@debian:~/Desktop/backintime-0.9.26$ cd gnome
deniz@debian:~/Desktop/backintime-0.9.26/gnome$ ./configure
All OK. Now run:
    make
    sudo make install
deniz@debian:~/Desktop/backintime-0.9.26/gnome$ make
make: Nothing to be done for `all'.
deniz@debian:~/Desktop/backintime-0.9.26/gnome$ sudo make install prefix=/usr/local/stow/backintime-0.9.26
#install python
install -d /usr/share/backintime/gnome
install --mode=644 *.py /usr/share/backintime/gnome
install --mode=644 *.glade /usr/share/backintime/gnome
#install plugin
install -d /usr/share/backintime/plugins
install --mode=644 ../plugins/gnome*.py /usr/share/backintime/plugins
#install copyright file
install -d /usr/share/doc/backintime-gnome
install --mode=644 ../common/debian_specific/copyright /usr/share/doc/backintime-gnome
#install man file(s)
install -d /usr/share/man/man1
install --mode=644 man/C/*.gz /usr/share/man/man1
#install application
install -d /usr/bin
install backintime-gnome /usr/bin
#install .desktop file(s)
install -d /usr/share/applications
install --mode=644 *.desktop /usr/share/applications
#install gnome-help file(s)
install -d /usr/share/gnome/help/backintime/C/figures
install --mode=644 docbook/C/*.xml /usr/share/gnome/help/backintime/C
install --mode=644 docbook/C/figures/*.png /usr/share/gnome/help/backintime/C/figures
install -d /usr/share/omf/backintime
install --mode=644 docbook/C/*.omf /usr/share/omf/backintime
deniz@debian:~/Desktop/backintime-0.9.26/gnome$ cd
deniz@debian:~$ cd /usr/local/stow
deniz@debian:/usr/local/stow$ stow backintime-0.9.26
deniz@debian:/usr/local/stow$ backintime-gnome
Traceback (most recent call last):
  File "/usr/share/backintime/gnome/app.py", line 42, in <module>
    import backintime
ImportError: No module named backintime
deniz@debian:/usr/local/stow$ 

I had to make the /usr/local/stow/backintime-0.9.26 manually with the mkdir command. Right before I got the error it seemed as if I had everything working succesfully however when I check the /usr/local/stow/backintime-0.9.26 directory, there is nothing in there! In addition to this the /usr/bin directory has backintime-gnome installed each time I attempt this! What am I doing wrong?

---

### Post by nikhilk on 2009-07-24
> **s3a said:**
> I had to make the /usr/local/stow/backintime-0.9.26 manually with the mkdir command. Right before I got the error it seemed as if I had everything working succesfully however when I check the /usr/local/stow/backintime-0.9.26 directory, there is nothing in there! In addition to this the /usr/bin directory has backintime-gnome installed each time I attempt this! What am I doing wrong?

I think the --prefix option should be supplied to ./configure. See if running
```
./configure --prefix=/usr/local/stow/backintime-0.9.26
```
and then make and make install gives you the desired results.

---

