---
title: "linux noob requires compilation help :)"
date: 2006-05-10
forum: General Help
---

### Post by reidy- on 2006-05-10
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... no
checking for prefix by checking for xmms... no
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH

I am a linux n00b and have just tried to compile my first program an mp3 player :)  and an the console when i executed the comand ./configure this came up ^^ now I have very little or no idea about what i said above (i was hoping you would give me a hand with that) but what kinda concernd me was that from the top two quieries:
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu

It isnt aware what version of linux I am running? unless the unknown is where it shoudl fill in the name of the CPU which would be possibly more worrying.

but any how what do i need to do to get my mp3 compiled and playing I take it gcc,cc,cl etc are file application extensions that are required to compile things where should I aquire these things and what to do with them 

thanks, Aaron

---

### Post by Omnios on 2006-05-10
This is a basic howto on compiling from source. 
[http://ubuntuforums.org/showthread.php?t=171822]("http://ubuntuforums.org/showthread.php?t=171822")

 Looks like you need build-essencial

---

### Post by matthewstory on 2006-05-10
Try installing the following and then doing it again:

sudo aptitude install make
sudo aptitude install bison
sudo aptitude intsall flex
sudo aptitude install gcc

or apt-get if you're more comfotable with it.

---

### Post by reidy- on 2006-05-10
That worked fine i need glib 1.2.2 now apperently I did a search through the forum but coudlnt find any how too's or much liek that you dont happen to know what to type in the console do you lol? although most people think spoon feeding people people what to do doesnt work i find it works perfectly I am now pretty apt at using the console mounting un mounting etc basically everything I have had a problem with :D

thanks, Aaron

---

### Post by matthewstory on 2006-05-10
you can search for it with synaptic in the GUI or do it the fast way and search for the package by name using aptitude or apt-cache:

sudo aptitude search <common name>

when you find the one you want:

sudo aptitude install <package name>

good luck

---

