---
title: "Cinelerra installation"
date: 2009-10-16
forum: General Help
---

### Post by EmmGeeImage on 2009-10-16
OK< I'm totally comfused on how to "install" those "TAR.bZ2" files. I have seen many things, tried many things... yet I do not have the program installed.

Basically, I need to know like a 2 year old.....As from what I saw, so do many others. SO, plase let us know in ENGLISH and like a 2 year old.

I currretly have the "tar.bz2" file on my desktop. 

I can open it and unzip to see the contents. So far, not one thing clicked on worked to install. I then tried termainal, which told me to "sudo apt get" and "CD desktop." I copied the stuff EXACT, and then inserted the folder locale and name. (see below)

------------------------------------------------------ 

sudo apt-get install build-essential
cd Desktop
cinelerra-4.1-ubu_9.04.tar.bz2
cd program_directory/
./configure
make
sudo make install

-----------------------------------------------------

mikel@MikelProd:~$ all:
bash: all:: command not found
mikel@MikelProd:~$ $(MAKE) -f build/Makefile.cinelerra
bash: MAKE: command not found
bash: -f: command not found
mikel@MikelProd:~$ 
mikel@MikelProd:~$ install:
bash: install:: command not found
mikel@MikelProd:~$ $(MAKE) -f build/Makefile.cinelerra install
bash: MAKE: command not found
bash: -f: command not found
mikel@MikelProd:~$ 
mikel@MikelProd:~$ clean:
bash: clean:: command not found
mikel@MikelProd:~$ $(MAKE) -f build/Makefile.cinelerra clean
bash: MAKE: command not found
bash: -f: command not found
mikel@MikelProd:~$ 
mikel@MikelProd:~$ rebuild:
bash: rebuild:: command not found
mikel@MikelProd:~$ $(MAKE) -C guicast clean
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ $(MAKE) -C cinelerra clean
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ $(MAKE) -C plugins clean
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ $(MAKE) -C guicast
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ $(MAKE) -C cinelerra
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ $(MAKE) -C plugins
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ 
mikel@MikelProd:~$ rebuild_install:
bash: rebuild_install:: command not found
mikel@MikelProd:~$ $(MAKE) -C cinelerra install
bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ $(MAKE) -C plugins install
]bash: MAKE: command not found
bash: -C: command not found
mikel@MikelProd:~$ ]cd Desktop
bash: ]cd: command not found
mikel@MikelProd:~$ tar xjf cinelerra-4.1-ubu_9.04.tar.bz2
tar: cinelerra-4.1-ubu_9.04.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
mikel@MikelProd:~$ cd program_directory/
bash: cd: program_directory/: No such file or directory
mikel@MikelProd:~$ ./configure
bash: ./configure: No such file or directory
mikel@MikelProd:~$ make
make: *** No targets specified and no makefile found.  Stop.
mikel@MikelProd:~$ sudo make install
make: *** No rule to make target `install'.  Stop.
mikel@MikelProd:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
mikel@MikelProd:~$ cd Desktop
mikel@MikelProd:~/Desktop$ cinelerra-4.1-ubu_9.04.tar.bz2
bash: cinelerra-4.1-ubu_9.04.tar.bz2: command not found
mikel@MikelProd:~/Desktop$ cd program_directory/
bash: cd: program_directory/: No such file or directory
mikel@MikelProd:~/Desktop$ ./configure
bash: ./configure: No such file or directory
mikel@MikelProd:~/Desktop$ make
make: *** No targets specified and no makefile found.  Stop.
mikel@MikelProd:~/Desktop$ sudo make install
mikel@MikelProd:~/Desktop$ 



As youcansee, it did not work... makes no difference if it is repoz or not... it didn't work. 

I and others need to know literally every step of the way to get this and other "Tar.bz2" programs to work successfully, everytime. Let us know what to type, where the folder/file name goes, etc. maybe I'm not doing something correctly.

Yes, I know it's just a Zipped file, like a ".RAR" and ".zip" would be to windows.

If it matters, I'm on 9.04, on a PC.

---

### Post by gdonwallace on 2009-10-16
Thats the down side to using tarballs (tar.bz files)  They generally do not have any "install programs".  In some tarballs, you just uncompress it into a directory and there is a file that will run the program, when you do an ls, look for the file name in green, it is the executable.  Copy the contents of the uncompressed file into what ever directory you want (I use /opt/<prog name/), create a shortcut on your desktop pointing to the executable and your set.

Some tarballs have .rpm files.  As Ubuntu is a debian based OS, you have to convert these to .deb files and then install them.  That is a little more complicated, but can be done in a few easy steps.

Follow this howto on converting .rpms to .deb and it will walk you through installling the program.  

The advantage of installing .deb files is that they appear in synaptic package manager, so that later you can use synaptic to check for updates or remove the program you decide that you don't need it.

---

### Post by aysiu on 2009-10-16
How about adding the proper repositories and then installing it the proper way (through package management)?

Here are the repositories for Cinelerra:
[http://cinelerra.org/getting_cinelerra.php#ubuntu](http://cinelerra.org/getting_cinelerra.php#ubuntu)

You can add them by going to System > Administration > Software Sources > Third-Party > Add

If the words *repositories* and *package manager* mean nothing to you, you need to read this:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by EmmGeeImage on 2009-10-16
The repoz stuff worked. However, that isn't answering the question.

There could be other things that we users cannot find in repoz and update manager, Synaptic manager that we need. How are we to find how to install those programs as  "tar.bz2"?

Sure it worked for this installation, to get the link, but it doesn't solve the question that I and many others have on installing steps of these "tar.bz2" files.

That is where we all need the help.



In both DOS and WIndows, it is easy to tell the PC to do something:

"Run Drive letter/Directory/xxoo.exe"  



The steps are simple. Tell it what to do, where to go, etc. 

Now you all understand? It's not as easy for us who converted, to understand what to type in to install the newer programs, that are not WINE based or older Linux based on linux systems nowdays.

I also want to know why "TAR.BZ2 installation" was changed to "Cinelerra Installation" as the title... since it's only the example of what I am talking about.

---

### Post by EmmGeeImage on 2009-10-16
If the other's have "RE: Tar.bz2 Installation" as the original title of the thread you are reading and they are responding to, why did the managers of this forum change it? It has very little to do with Cinelerra, but everything to do with how to install "tar.bz2" files, to make them work.

PLease note that I never asked how to install "Cinelerra," but did ask how to install "tar.bz2" files.

ALso note that "cinelerra" was not in the tags.

---

### Post by ajgreeny on 2009-10-16
The difficulty is, as has been said by another poster in this thread, there is not one single answer to this question, and therefore it can not be answered in the manner you want.  Do a google or forum search for "how to install anything on ubuntu"  There is a web page or pages answering just that, but I do not know of it exactly, so can't post an address.

---

### Post by aysiu on 2009-10-16
There are two reasons I retitled the thread:

1A. You appear to be trying to install Cinelerra, and the best way to install it is not with a .tar.bz2.

1B. Generally speaking, it is always best to use the package manager to install software. It is only on very rare occasions that something is not in some kind of repository, and if it is, you take those on a case-by-case basis.

2. There is no standard way to install a .tar.bz2, because a .tar.bz2 is just a compressed file. Until you decompress (or unzip) the file, you have no idea what's in it. It could be source code. It could be a precompiled binary. It could be a .bin wizard installer.

---

### Post by EmmGeeImage on 2009-10-16
Package manager could not find some of the software I need, so that does not help, when the "BZ2" file is available. In fact, someone once asked on this site about VLC, windows version or the BZ2 file. Seemed that he thought it wasjust easier to do the windows file. I don't blame him. Windows is streaks easier... however, ubuntu and linux has it's strengths... just not in installs and ways to install. 

I may just go back to wndows permanently. at least I know there are easier ways to install, without complications.

What the example showed was the 9.04 file to install the program, not source code.

Still no word on who or why the title was changed from ""tar.bz2 installation" to what it is now. I am 3000%, out of 100% sure I did not change it. Would be nice to know who did and why. I'm glad that in the USA, we have Chinese Communists, who don't like things the way they are... and have carte blache to just decapitate things, at will... as in the title header of this thread

---

### Post by aysiu on 2009-10-16
> **EmmGeeImage said:**
> 
Still no word on who or why the title was changed from ""tar.bz2 installation" to what it is now. I am 3000%, out of 100% sure I did not change it. Would be nice to know who did and why. I changed the title, and I just explained why.

I'm not convinced there are hoards of programs people want to install but that aren't available either through a repository a .deb file. If you are in a unique situation (three or more programs you need are not available to install easily), then, yes, it might make sense for you to go back to Windows.

The vast majority of Linux programs can be installed through the package manager.

And, as I said before, it still doesn't matter if you just want to know generally how to install .tar.bz2 files--there is no general way to do it. It is a non-standard installation method, and it also not recommended except in extreme cases.

Since you appear to not actually want support for installing Cinelerra, I'm closing this thread. If you need support on a real issue, then ask for it, and you'll get it.

---

### Post by bodhi.zazen on 2009-10-16
> **EmmGeeImage said:**
> Package manager could not find some of the software I need, so that does not help, when the "BZ2" file is available. In fact, someone once asked on this site about VLC, windows version or the BZ2 file. Seemed that he thought it wasjust easier to do the windows file. I don't blame him. Windows is streaks easier... however, ubuntu and linux has it's strengths... just not in installs and ways to install. 

I may just go back to wndows permanently. at least I know there are easier ways to install, without complications.

What the example showed was the 9.04 file to install the program, not source code.

Still no word on who or why the title was changed from ""tar.bz2 installation" to what it is now. I am 3000%, out of 100% sure I did not change it. Would be nice to know who did and why. I'm glad that in the USA, we have Chinese Communists, who don't like things the way they are... and have carte blache to just decapitate things, at will... as in the title header of this thread

I am posting to this now closed thread for informational purposes only.

To install applications you are best off using the Ubuntu repositories.

See : [InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware") 

The repositories are quite large. so you may simply need to enable "Universe"

See : [Repositories/Ubuntu - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu") 

If you are installing software outside the repositories , get directions from the hompe page or web site.

Extract the archive (.tar.bz , .tar.gz, etc) and read the README

Some archives, firefox for example, distribut binaries. Others distribute source code.

If you are building from source code you will more then likely have to install a number of "dependencies" , you will need to find the dependencies yourself, which is why most people user the repositories (apt-get / synaptic will resolve dependencies for you, automagically).

[CompilingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/CompilingSoftware") 

If you have a specific question about a specific package , please start a new thread.

Once you get the hang on it, it is not *that* hard to compile applications yourself, but when you do you are "on your own". If you want support, use the repositories.

---

