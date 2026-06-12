---
title: "bash: ./configure: No such file or directory"
date: 2011-09-24
forum: General Help
---

### Post by Luxx on 2011-09-24
I am trying to compile WINE from a tarball and getting the following error:
bash: ./configure: No such file or directory

I would very much appreciate any help with this, but PLEASE DO NOT RESPOND WITH "What are you trying to install and why are you not using the repositories ?" I have seen this many times in various forums and it is very rude and non-helpful. But since that seems to be the standard "help" someone with this problem gets, here is the answer:

I am trying to  install a specific version of wine BECAUSE IT IS THE ONLY ONE THAT WORKS FOR A CERTAIN PROGRAM I WANT TO USE. I had installed it from the repositories in the first place and it automatically updated without my permission, much to my horror (envision recurring Microsoft nightmares).

I need version 1.3.26 and it updated to 1.3.28. Now if I try to install with apt-get I will get the 1.3.28 version which doesn't work for my program. I tried it. I tried different versions of the program...no dice.

I can't seem to change directories in terminal. It appears to be changing directories, but in the end it hasn't. I tried changing directories to the folder where I had the tarball and tried to unpack it using:

tar -xvf wine-1.3.26.tar.bz2

I got an error that the file didn't exist. It wouldn't do anything until I typed in the path where the file was stored:

tar -xvf /usr/local/src wine-1.3.26.tar.bz2

That seemed to unpack it, but I have no idea where it went. It is not in /usr/local/src.

When I type in ./configure I get the error:

bash: ./configure: No such file or directory

So I went to the directory, right-clicked and selected "Extract here." This resulted in a locked file I could not use. Then I tried the same thing after opening with 'gksudo nautilus' and making sure the  permissions would allow me to use it, and that the configure file was there. But when I typed in ./configure I STILL got the error:

bash: ./configure: No such file or directory

I can't figure out how to give the _**path and the command**_ by command line so it will work.

I have installed build-essential and a bunch of other things that are supposed to allow compiling from source and nothing has made a difference. Apparently everything is the current version. I have checked this error on this and several other forums and haven't found an actual solution.

I don't get why it is suddenly so hard to install from a tarball. It wasn't this hard before. Has there been some drastic change in the way things are installed since 10.04 (I'm now on 10.10)?

---

### Post by TeoBigusGeekus on 2011-09-24
```
/usr/local/src/configure
```

---

### Post by el_koraco on 2011-09-24
Then don't untar it into /usr/local/src, untar it to ~/src or something (you'll obviously gonna have to create the directory. Or first copy it to /usr/local/src, cd to /usr/local/src untar it there, cd to the untared directory and then run configure. If you run configure in just any directory, it's not gonna work, that's why you're getting the "no such file" error. 

Btw, you're usually not gonna get good responses by starting your thread with "don't tell me this and that".

---

### Post by Luxx on 2011-09-24
> **el_koraco said:**
> Then don't untar it into /usr/local/src, untar it to ~/src or something (you'll obviously gonna have to create the directory. Or first copy it to /usr/local/src, cd to /usr/local/src untar it there, cd to the untared directory and then run configure. If you run configure in just any directory, it's not gonna work, that's why you're getting the "no such file" error. 

Btw, you're usually not gonna get good responses by starting your thread with "don't tell me this and that".

Yeah, I know. I can't cd to the directory. When I change the directory in the terminal I get only the default directory. I still don't get why that is happening. I think that might be what the problem is for other users who have been asking the same question about this error.

....And yeah, I normally wouldn't start a thread that way, but given the fact that there were quite a few threads started all over the internet that got NOTHING but "why aren't you using repos" I figured I would probably get the same thing if I didn't specifically ask people to not do that.

---

### Post by Luxx on 2011-09-24
> **TeoBigusGeekus said:**
> ```
/usr/local/src/configure
```

Again:
bash: /usr/local/src/configure: No such file or directory

---

### Post by dave01945 on 2011-09-24
have you tried

```
cd /usr/local/src/wine-1.3.26
./configure
```

it would be best to use <TAB> completion to make sure their are no spelling errors

---

### Post by TeoBigusGeekus on 2011-09-24
^^^^ This.

---

### Post by CatKiller on 2011-09-25
The reason we ask "why aren't you using the repositories?" is because almost always the users that post here saying that they can't compile something have no idea what they're doing. They've seen instructions on the process of compiling and assume that that's what they have to do. It never occurs to them that there might be better solutions to their problem.

So why don't you simply use Synaptic to force and lock your version of the Wine package to the one runway you want to use?

---

### Post by el_koraco on 2011-09-25
> **Luxx said:**
> Yeah, I know. I can't cd to the directory. When I change the directory in the terminal I get only the default directory. I still don't get why that is happening. I think that might be what the problem is for other users who have been asking the same question about this error.


I've never heard of anyone having that error, 8nless you're trying to cd to a directory that doesn't exist. But, just in case, download the tarball, extract it to somewhere in your home directory, and run configure there.

---

### Post by Luxx on 2011-12-26
I had some kind of permissions problem, which fixed after some updates I had been ignoring. All is good now. Thanks for your help.

---

### Post by schietop on 2013-01-08
I happen to have ubuntu 12.10.

Trying to install gambas2 with  tar.bz2 file. I extracted it on my desktop in a folder called gambas.  Looked into the INSTALL file and said to use
 ./configure
make
sudo make install

But it keeps telling me: no such file or directory.

Terminal:

tomassio@tomassio-VGN-NS21Z-S:~/Desktop/gambas$ dir
acinclude.m4  gb.compress.bzlib2  gb.net    INSTALL
aclocal.m4    gb.compress.zlib      gb.net.curl    install-sh
app          gb.corba          gb.net.smtp    main
AUTHORS       gb.crypt          gb.opengl    Makefile.am
ChangeLog     gb.db.firebird      gb.pcre    Makefile.in
comp          gb.db.mysql      gb.pdf    missing
component.am  gb.db.odbc      gb.qt        NEWS
config.guess  gb.db.postgresql      gb.qte    README
config.h.in   gb.db.sqlite2      gb.qt.kde    README.svn-commit
config.sub    gb.db.sqlite3      gb.sdl    reconf
configure.ac  gb.desktop      gb.sdl.sound    reconf-all
COPYING       gb.gtk          gb.v4l    TEMPLATE
depcomp       gb.gtk.svg      gb.xml
examples      gb.image          help
tomassio@tomassio-VGN-NS21Z-S:~/Desktop/gambas$ ./configure
bash: ./configure: No such file or directory


I installed ubuntu 12.10 yesterday and using it for first time. I did do apt-get update and upgrade.
I am new to ubuntu, so be specific in ur answer;)

---

