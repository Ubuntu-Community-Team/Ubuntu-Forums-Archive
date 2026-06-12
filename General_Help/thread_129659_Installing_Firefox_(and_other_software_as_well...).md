---
title: "Installing Firefox (and other software as well...)"
date: 2006-02-14
forum: General Help
---

### Post by Pedestrian A on 2006-02-14
Hi,

I've found an article on[ installing Firefox (1.5) in Ubuntu's official Wiki]("https://wiki.ubuntu.com/FirefoxNewVersion") but I've gotta get a few things cleared first. First, what's libstdc++5? Do I have it or not? And installing Firefox involves basically commands, right? I'm supposed to use Terminal for all of these, no? Also, how do I install software on Ubuntu/Linux? Does it involve using Terminal too? I've read release notes of software like Firefox and it says extract the tarball somewhere... huh? Does it mean replace the old software files with the new one? Where is the files for my software placed anyway? Do I have access to them? Please and thank you...

Pedestrian A.
- I'm so confused, I'm not even sure what I'm tryin to find out...

---

### Post by mattheweast on 2006-02-14
[QUOTE=Pedestrian A]Hi,

I've found an article on[ installing Firefox (1.5) in Ubuntu's official Wiki]("https://wiki.ubuntu.com/FirefoxNewVersion") but I've gotta get a few things cleared first. First, what's libstdc++5? Do I have it or not?[/quote]

Try installing it, and you'll find out if you have it or not.

> 
And installing Firefox involves basically commands, right? I'm supposed to use Terminal for all of these, no?

yes, enter each command in a terminal

> 
 Also, how do I install software on Ubuntu/Linux? Does it involve using Terminal too?

No, the best way to install software on Ubuntu is by using the package managers. Read [http://help.ubuntu.com/starterguide/C/ch02.html](http://help.ubuntu.com/starterguide/C/ch02.html) for more information.

> I've read release notes of software like Firefox and it says extract the tarball somewhere... huh? Does it mean replace the old software files with the new one? Where is the files for my software placed anyway? Do I have access to them? Please and thank you...

This applies to the cases when you DON'T use the package managers. It's not recommended you install software like this. If you want a version of software which is not available in the package managers, you have to start using the terminal, but in reality, you don't actually NEED to do this: the software available in the package managers is sufficient, secure and stable.

I'd advise you to stick with the version of firefox that comes already installed on Ubuntu. In a couple of months, a new version of Ubuntu (including new firefox) will be available, and you can upgrade to that.

Matt

---

### Post by mirshafie on 2006-02-14
First, "Where is the files for my software placed anyway? Do I have access to them?". The files for you're software can go to a few different directories. Please check [Linux Command: A guided tour](http://www.linuxcommand.org/lts0040.php) for some info about how files in Linux are organized. You have access to them of course, but for many of them you need to be root to execute or to write to them. From a terminal emulator, you can type 'sudo' followed by the command you want to do as root. sudo = superuser do, it will promt you for the root password. In Ubuntu the root password is your user password.

Ubuntu uses [dpkg](http://en.wikipedia.org/wiki/Dpkg) as a package manager. [APT](http://en.wikipedia.org/wiki/Advanced_Packaging_Tool) is a frontend to dpkg; what it does is basically to download packages that are precompiled for the Ubuntu Linux [kernel](http://en.wikipedia.org/wiki/Kernel_%28computer_science%29) from the Ubuntu repositories, and then install them. Synaptic is a graphical user interface for APT that comes with Ubuntu. You can start it from the System menu in Gnome.

Then you just need to search for the programs you want, in this case libstdc++5, mark it for installation and Apply. APT/Synaptic will do the rest.

If you want to use APT from the command line, like I do since i think it's easier, you can type:
[indent]
'sudo apt-get install <the programs you want to install>'
'sudo apt-get remove <the programs you want to remove>
'apt-cache search <the programs/descriptions you want to search for>'
[/indent]
in the terminal.

APT downloads packages from the repositories that you have entered in you're sources.list. The default sources.list that comes with Ubuntu contains only absolutely free software and no version upgrades - which means really nice software such as mp3 support, mplayer and some amaroK engines is not there.  So, i think most people will want to add more entries to their sources.list. You can do so by opening it in a text editor such as gedit. I use nano.
[indent] sudo nano /etc/apt/sources.list

Note: the linux shell supports auto completion. Hit TAB (located to the left of Q) for auto completion. Neat, huh?
[/indent]
If there's a repository you don't want in the sources.list, you can "comment" it out by adding a # in the beginning of that line. Lines that start with # are ignored, they're used to add comments to configuration files. I've commented out the DVD repository for example, since i think it is annoying and useless.
You can generate your own sources.list easily by visiting the [Ubuntu Source-o-Matic](http://www.ubuntulinux.nl/source-o-matic). After you've edited your sources.list, you need to uptade APT's index, and then you will be ready to use the new repositories.
[indent] sudo apt-get update
[/indent]

I don't want to confuse you even more, you don't HAVE to know the following right now. But it's good if you learn it when you're ready:
A **tarball** is a compressed package of files, often containing source code and information on how to compile a program. For some reason, many Ubuntu people tell new users to avoid installing software by their own, but I'm sure most users will sooner or later come across software they want to install that are not in their distro's repository, so I'm going to give you a quick introduction on how to compile and install software on your own. It is NOT as hard as it seems, you will learn after you've done it a couple of times.

First download the tarball. There are two common kinds of tarballs, some are compressed with gzip and their extension are .tar.gz, some are compressed with bzip2 and their extension are .tar.bz2.

You extract them with the following commands:
[indent]
'tar -xvzf <filename>' for tar.gz files.
'tar -xvjf <filename>' for tar.bz2 files.

The x switch tells tar to extract, f tells tar to use a file as input, v means verbose and is optional (it will give you info on what tar is doing). The z and j switches tell tar to extract tar.gz or tar.bz2-files, as you can see from the example above.
[/indent]

A new directory will have been created, usually with a similar name to to the tarball. If you used the v switch you can see what the name of the directory is, if not, type 'ls' ("ls = list") in the terminal to get a listing of directories, and find it. Then type 'cd <directory_name>' ("cd = change directory") to go to the new directory. There are usually a README-file and an INSTALL-file there that you can read by typing 'nano README' or 'nano INSTALL'. They may contain important information about dependencies and how to install the software. (Dependencies are other software that the software relies on. APT downloads those automatically.)

You need to configure the source code for your system, usually by running a script called configure. Type './configure' when in the extracted directory.
If everything goes well - i.e. if you have the dependencies installed, the configure script will produce a make file. Run it by typing 'make'. It will compile the source code. Then install the software by typing 'sudo make install'.
[indent]**Summary:**
cd <directory>
./configure
make
make install
[/indent]

As you might have figured ot by now, one confusing part of this is to have all the right dependencies. Another thing is that it can be tricky to uninstall the software if you don't know what you're doing - they don't come with uninstallers. One way to make it easier to uninstall the software is to use checkinstall ('sudo apt-get install checkinstall'), and run it instead of 'make install'. It will generate a deb package for you (debs are precompiled packages, like the ones APT downloads from the Ubuntu repositories). You can then uninstall the software with Synaptic or 'sudo dpkg -r <deb-file>'.

You need some tools for compile packages, like c and c++ compilers. Do
[indent]
sudo apt-get install libtool make gcc g++
[/indent]
to install some of the most important tools.

I hope you found this info useful. As mattheweast wrote, you will probably never be forced to compile software from source, but to know how to do it will enable you to get new software faster.

---

### Post by Pedestrian A on 2006-02-17
Ok,

Maybe I'm not gonna upgrade Firefox as there's some disadvantages to that too. So I'll wait for it in an Ubuntu update/upgrade but I still think it'll be good to learn how to install software manually in Ubuntu too. So, any good software for Ubuntu I might wanna try? Thanks.

Pedestrian A.
- sorry, mirshafie, I haven't finish reading your post, my connection was down for a day and your post is really long... but I'll read it. ;)

---

### Post by aysiu on 2006-02-17
You may want to check out the second link of my signature.

---

### Post by nanotube on 2006-02-17
try also the section at the bottom of the page in my signature. i have a list of packages i have installed that i have found useful, if you want to take a look.

as to firefox, the version that comes with ubuntu by default is noticeably slower than the freshest 1.5 - but if you are not feeling up to installing stuff with command line, you are probably better off staying with the default version for the time being...

---

