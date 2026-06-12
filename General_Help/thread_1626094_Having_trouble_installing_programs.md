---
title: "Having trouble installing programs"
date: 2010-11-19
forum: General Help
---

### Post by ingrown.potato on 2010-11-19
There are a few programs (such as lillypad) that are not listed in the software manager that I would love to install. I'm confused as how to do so. When i go on lillypad's website there is no direct extraction link, it just lets me save the source code and tells me to compile. I'm brand new to linux, I'mreally confused and need some getting off on the right track. Also, I downloaded amarok and tuxguitar, whcih both output no sound when I try and run them. Amarock wont play and of my mp3s and just skips to the end of this list, and tux guitar just runs though without outputting any sound. Any help wouild be greatly appreciated! Thank you for reading!

---

### Post by holiday on 2010-11-19
To build an application, you have to install dev-essential using apt-get.

Then download the application's source code into a directory you create for just this purpose. Change into that directory and type

$ ./configure

The console will spew lines, don't worry.

You may have to install other libraries if the application you're building is not Ubuntu-standard. That's easy to do. Find them through 

$ apt-get search whateverlib 

And install those libraries - but be sure to get the <library>-dev version.

When you've installed the libraries that configure asks for, when it completes without error, then go:

$ make

This will probably go perfectly. Again a stream of text that eventually stops and then you go

$ sudo make install

I think you can probably do it with just that, but I like extra suspense.

---

### Post by ingrown.potato on 2010-11-19
Thank you so much for responding! I went into root and typed "apt-get install dev-essential" and it said this: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dev-essential

Do I have to download anything prior to be able to locate dev-essential?

---

### Post by holiday on 2010-11-19
> **ingrown.potato said:**
> Thank you so much for responding! I went into root and typed "apt-get install dev-essential" and it said this: Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package dev-essential

Do I have to download anything prior to be able to locate dev-essential?

So sorry! It's build-essential

---

### Post by qamelian on 2010-11-19
It should be build-essential.

---

### Post by endotherm on 2010-11-19
I think your sound and amarok problems may be unrelated. I can't help with the sound, but have you installed any codecs for your system?

if not, I recommend you add the mediubuntu repositories per the instructions here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and install libdvdcss2, and either the w32codecs, or the w64codecs, depending on whether you have 32 or 64 bit ubuntu. 

then install the ubuntu-restricted-extras package from the repositories, either via software center/synaptic, or with this command```
sudo apt-get install ubuntu-restricted-extras
```. this will install a bunch of codecs with loaders (including an MP3 codec), adobe flash, openJDK, and a bunch of other handy interoperability components. 

if you are looking for good video players, Totem is nicely integrated, but if you have trouble with a file, smplayer or vlc are execelent fallback players. VLC uses its own codecs and plays most everything, but SMplayer has better picture and performance even at high res.  

good luck!

---

### Post by ingrown.potato on 2010-11-19
Ok, i installed build-essential, when I type "./configure" all i get is this error message : bash: ./configure: No such file or directory

---

### Post by ingrown.potato on 2010-11-19
> **endotherm said:**
> I think your sound and amarok problems may be unrelated. I can't help with the sound, but have you installed any codecs for your system?

if not, I recommend you add the mediubuntu repositories per the instructions here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
and install libdvdcss2, and either the w32codecs, or the w64codecs, depending on whether you have 32 or 64 bit ubuntu. 

then install the ubuntu-restricted-extras package from the repositories, either via software center/synaptic, or with this command```
sudo apt-get install ubuntu-restricted-extras
```. this will install a bunch of codecs with loaders (including an MP3 codec), adobe flash, openJDK, and a bunch of other handy interoperability components. 

if you are looking for good video players, Totem is nicely integrated, but if you have trouble with a file, smplayer or vlc are execelent fallback players. VLC uses its own codecs and plays most everything, but SMplayer has better picture and performance even at high res.  

good luck!

How do you install libdvdcss2? with apt-get?

---

### Post by endotherm on 2010-11-19
> **ingrown.potato said:**
> How do you install libdvdcss2? with apt-get?
as you scroll down the mediubuntu repo how to, you will see commands to add the repos, and add software-center integration (so you can install mediubuntu packages from the SC), followed by instructions for removing non-free components (which you will probably want to ignore), and finally instructions for installing the libdvdcss2 and the windows codecs. 


if you want to use software center, just search for both the packages I mentioned, or if you want to use apt-get,  you can follow the repo howto from top to bottom, skipping the parts about removing the non-free and installing packages individually, and you will get everything you need from mediubuntu.


as for your compliation, are you in the folder that contains the source code and makefile?
if not, use cd to navigate to that directory.

---

### Post by ingrown.potato on 2010-11-19
Yes, I was in a directory I made specifically for that program, that directory is /home/lillypond. I don't have a make file though, what is that? Also, when I type "man configure" it says there is no manual entry found. Is that a problem?

---

### Post by holiday on 2010-11-19
Do this
$ ls configure

Does anything come up?

If not do this:

$ find . -name configure

It may be in some subdirectory. Change into that directory and try again. 

If nothing comes up they you don't have the build package.

---

### Post by endotherm on 2010-11-19
> **ingrown.potato said:**
> Yes, I was in a directory I made specifically for that program, that directory is /home/lillypond. I don't have a make file though, what is that? Also, when I type "man configure" it says there is no manual entry found. Is that a problem?

my guess is you don;t have execute privledges within /home/lillypad
try this:
```
sudo chmod a+x ./*
```

then try ./configure

---

### Post by ingrown.potato on 2010-11-19
None of those work, still says i dont have configure and when I try and get the build package again it prints this " Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 158 not upgraded."

--------------

I tried the chmod, it didnt work either, still says no file or directory for configure

---

### Post by endotherm on 2010-11-19
> **ingrown.potato said:**
> None of those work, still says i dont have configure and when I try and get the build package again it prints this " Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 158 not upgraded."

--------------

I tried the chmod, it didnt work either, still says no file or directory for configure


please post back the output of:
```

pwd
ls -l

```

---

### Post by ingrown.potato on 2010-11-19
mike@ingrown:~/lilypond$ pwd 
/home/mike/lilypond
mike@ingrown:~/lilypond$ ls -l
total 23004
-rwxr-xr-x 1 mike mike 23522263 2010-11-19 19:47 lilypond-2.12.3-1.linux-x86.sh
-rwxr-xr-x 1 mike mike       37 2010-11-19 19:55 test.ly
mike@ingrown:~/lilypond$

---

### Post by endotherm on 2010-11-19
> **ingrown.potato said:**
> mike@ingrown:~/lilypond$ pwd 
/home/mike/lilypond
mike@ingrown:~/lilypond$ ls -l
total 23004
-rwxr-xr-x 1 mike mike 23522263 2010-11-19 19:47 lilypond-2.12.3-1.linux-x86.sh
-rwxr-xr-x 1 mike mike       37 2010-11-19 19:55 test.ly
mike@ingrown:~/lilypond$

ahh, they wrote an install script. thats nice of them.
try this
```

sudo ./lilypond-2.12.3-1.linux-x86.sh

```

that'll probably do it all.  if not, let us know.

---

### Post by ingrown.potato on 2010-11-20
This was my output:

mike@ingrown:~/Documents$ sudo ./lilypond-2.12.3-1.linux-x86.sh

lilypond installer for version 2.12.3 release 1.
Use --help for help


You are about to install LilyPond in /usr/local/lilypond
A script in /usr/local/bin will be created as a shortcut.

Press ^C to abort, or Enter to proceed.

Making /usr/local/lilypond
Creating script /usr/local/bin/lilypond
Creating script /usr/local/bin/lilypond-wrapper.python
Creating script /usr/local/bin/lilypond-wrapper.guile
Creating script /usr/local/bin/uninstall-lilypond
Untarring ./lilypond-2.12.3-1.linux-x86.sh
To uninstall lilypond, run

    /usr/local/bin/uninstall-lilypond

For license and warranty information, consult

    /usr/local/lilypond/license/README

Full documentation can be found at

    [http://lilypond.org/doc](http://lilypond.org/doc)

------

Looks like it worked, but I have no idea how to run it.

---

### Post by endotherm on 2010-11-20
based on [this]("http://lilypond.org/unix.html"), you want to run something like:
```

lilypond ~/lilypond/test.ly

```

no idea what the .ly files are for or do. my guess is you will have to formulate ly files for input, and when the process is done, the output will be in test.pdf.

---

### Post by ingrown.potato on 2010-11-20
How would I do that?

---

### Post by endotherm on 2010-11-20
> **ingrown.potato said:**
> How would I do that?
no idea man, never used it. I'd search around, and if you can;t find anything, then start a new thread on that topic. 

good luck

---

### Post by ingrown.potato on 2010-11-20
I didint need to formulate it, it just ran the .ly file. Finally got this thing somewhat working. Do you have any idea why my amarok isint playing? I installed ubuntu restricted areas, sitll nothing.

---

