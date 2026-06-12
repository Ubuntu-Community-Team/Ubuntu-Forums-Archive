---
title: "Need as much help as I can get"
date: 2012-04-14
forum: General Help
---

### Post by CinthiaG on 2012-04-14
Hi everyone. I'm brand new to Linux Ubuntu OS as I've never in my life used it before. It's currently the only OS I have on my computer and I'd love to keep it, the problem is I really have no idea what it is that I'm doing.

I was told this forum helps out a lot so I'm really crossing my fingers! 

There are a few things that I seem to not understand at all. I've Googled how to run a few things through the Terminal but I'm just copying and pasting. Is there a specific thread that can guide me through anything and everything I need to know?

Also, I've got this Wacom Bamboo tablet that I just can't figure out how to get to work properly using Ubuntu. I've downloaded a couple files: libwacom-0.4 and linux-3.3.2. My problem is, I don't know what to do with them after I've downloaded them. I've extracted them to my desktop and they're just sitting there. I've also been looking at various websites on how to install it but I get an error message in the Terminal everytime. If someone could guide me step by step, I'd really really be thankful!

I need as much help as I can get!! :(

---

### Post by agillator on 2012-04-14
To solve your 'real' problem, i.e. new to Linux, I would highly recommend a visit to the bookstore (or Amazon). I'm not going to recommend a specific book because everyone's needs and likes are different and there are a lot of excellent books out there. For a quick start, though, you might look at the 'Linux For Dummies'. You will probably want a more complete reference after that, though (also more expensive, sadly). 

Someone else will have to help you with your tablet, I know nothing about it. However, in general when you 'download' a file or files like that from someplace they will normally be some compressed format, most commonly what is called a 'tarred' file. It will be named something like xxxxx.tar.gz or xxxx.tar.bz2 or something else along that line. If so, then the first thing is to 'untar' the file. That would be done in a terminal with the command 'tar zxvf xxxxx.tar.gz' or 'tar jxvf xxxxx.tar.bz2', respectively, from the directory where the files are stored. One terminal command you need to become familiar and comfortable with is 'man', for example 'man tar'. That tells you much about a command or file and how to use it. 'man man' tells you how to use the man command. 

It is difficult to answer a very general question such as yours, so as you have specific questions ask them and you will get more specific, and probably more helpful, answers. Hopefully someone will be able to help you with the tablet installation, though.

---

### Post by dino99 on 2012-04-14
Welcome Cinthia

one day or an other, we all be noobs :) dont worry 

But to get precise answers, you need first to post precise questions; blah blah is useless.

which ubuntu ? which needs ? 32 or 64 bits installed ? which model hardware ?

Ubuntu comes with some applications installed by default, and you can find them either via scrolldown menus if using gnome-classic (installed via gnome-session-fallback package into synaptic) or via dash if using unity

you still have some usefull readings following the links below, and of course across the forums here.

---

### Post by oldfred on 2012-04-14
First link I found.

[http://blog.jvc26.org/2012/02/02/wacom-bamboo-ubuntu-oneiric](http://blog.jvc26.org/2012/02/02/wacom-bamboo-ubuntu-oneiric)

I have seen multiple posts on different versions of bamboo devices.

I think using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search terms or use:
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

A bunch of links for newer users:
Thread on books:
[http://ubuntuforums.org/showthread.php?t=1874294](http://ubuntuforums.org/showthread.php?t=1874294)

Ubuntu Documentation:
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/11.04/index.html](https://help.ubuntu.com/11.04/index.html)

Suggestions on how to get your support questions answered as quickly as possible 
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

New to Ubuntu? Start here...  Also commands
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Beginners guide:
[http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485) (Newbie 101) 
[http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) (Newbie Terminal Intro)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885) (Terminal for Beginners) 
[http://www.solutionbeacon.com/CommonLinuxCommandsPocketGuide07.pdf](http://www.solutionbeacon.com/CommonLinuxCommandsPocketGuide07.pdf)

---

### Post by Favux on 2012-04-14
Hi CinthiaG,

Welcome to Ubuntu forums!

As mentioned we want to know which Release of Ubuntu you are using.  Example:  Oneiric 11.10.

We can also figure that out if you post the output of this command:
```
Xorg -version
```
Open a terminal and copy and paste the command and hit enter to run it.  Usually to post output you place it between code tags.  That's the # on the upper right of your forum post window.

Also we need to know the model of your Bamboo.  What is it?  It should be on the back of the tablet.  Also we can determine Vendor and Product ID by running this terminal command:
```
lsusb
```
and posting the output.
> I've downloaded a couple files: libwacom-0.4 and linux-3.3.2.
You shouldn't need to use either of these.  If your Bamboo tablet is a third generation BambooPT you don't need the 3.3 kernel, you use input-wacom instead.

---

### Post by CinthiaG on 2012-04-14
Thank you guys for the links and tips on the books. I didn't realize I was being so vague about all of it. To be more specific about the problems I am having, I do not understand how to install programs into the computer using the Terminal. That is mostly what I need help with, but I think the tip on reading the "for Dummies" book might be just what I need.


Under the System Settings>System Info, it says: 
> Ubuntu 11.10
OS type 32-bit


As for the type of Bamboo tablet I'm using, it's a 2 year old **Bamboo Fun and Pen model CTH-661**. Any direct links for this tablet's driver would be helpful [and maybe an explanation how to get it working :\].


Thank you guys for replying with what you could, I appreciate it.

---

### Post by MG&amp;TL on 2012-04-14
> **CinthiaG said:**
> Thank you guys for the links and tips on the books. I didn't realize I was being so vague about all of it. To be more specific about the problems I am having, I do not understand how to install programs into the computer using the Terminal. 

Why do you want to? There is a software centre for a reason...:) But, for whatever reason, if you need to, you can install software in Ubuntu with the following commands:

```
apt-cache search <search-term>
```

-searches packages for software, where <search term> is... a search term. 

```
sudo apt-get install <packagename>
```

-installs a package, where <packagename> is a package's name.

---

### Post by Favux on 2012-04-14
Alright, the Bamboo Fun and Pen model CTH-661 or:
```
Bamboo Comic Medium			stylus, eraser; touch, pad
   (CTH661/S1; Product ID = 0xd8)
```
That's a second generation BambooPT.

There are two Wacom drivers.  The kernel driver wacom.ko and the X driver xf86-input-wacom.  The kernel driver translates the raw usb data into stuff the X driver can use.  The Wacom X driver then uses the X Server to draw the stuff on your monitor.  Ubuntu calls xf86-input-wacom the xserver-xorg-input-wacom package.

Because your tablet has touch you need to update both drivers in Oneiric (11.10).  There are significant gesture improvements in xf86-input-wacom-0.14.0 over the default xf86-input-wacom version that comes with Oneiric.

So you need to do both part I. and part II. on the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  It looks intimidating but it is actually easy.  Just open up a terminal and copy and paste the commands one by one hitting enter after each one to run them.

---

### Post by roelforg on 2012-04-14
Good for beginners: [https://help.ubuntu.com/community/Beginners/BashScripting](https://help.ubuntu.com/community/Beginners/BashScripting)

And i thought 11.10 has wacom stuff preinstalled (my sys settings say so) and the fallback driver is very decent (really, it worked with my touchscreen immediatly).

---

### Post by CinthiaG on 2012-04-14
Favux, thank you for that! It's helped with my tablet actually working in the drawing programs. My only problem now is getting GIMP to recognize pen pressure and the eraser. I read through the process and copied and pasted everything but I noticed a few attempts came up with the word "Failure" and "Error". I'm not sure if that effected the outcome.


roelforg, I'm not sure if it did or not but when I tried to use my tablet last night, the pen's on-screen pointer went haywire. It wasn't working properly.

---

### Post by Favux on 2012-04-14
Great!  Nice job.  :)

Don't worry too much about the errors as long as the wacom.ko was built i.e. you could use the copy (cp) command.  And for xf86-input-wacom if the *sudo make install* command worked then it was built too.  You can always redo if there seems to be a problem.  It will get pretty quick once you've done it once or twice.

With Gimp you have to configure the extended input devices to get pressure.  A couple other applications have that as well such as Inkscape.

In Gimp go to:  Edit > Preferences > Input Devices > Configure Extended Input Devices... > in Device:  select your stylus and set Mode:  to Screen.  Do the same with your eraser.

If you start getting lines flying around after doing that install Aapo's Gimp PPA linked to in "Ubnutu Release Specific Notes" (near the top of the HOW TO).  It has Alexia Death's (Gimpe developer) patch to fix (turn off) the history buffer in Gimp.

---

### Post by agillator on 2012-04-14
Cinthia, looks like you have lots of good help on your tablet situation. I'll just try to give you a quick explanation of 'installation'. I'll be very basic because I don't know what you already know and don't know. Where I am too basic, please don't be insulted but understand what I am trying to do.

A file is a file. In one instance it may be a data file, in another the same file may be a program. The computer doesn't know the difference, and doesn't care until it tries to run (execute) it. At that time, if it contains computer commands in the proper format then it is a program. To see if a file is intended to be a program you check the permissions (part of the linux file system). The command (in a terminal) ls -l (that's el es dash el) will list all the visible files in the current directory along with information about each file. Part of the information is a list of 10 permissions in one string, something like -rwxrw-r. r means permission to read, w permission to write, x permission to execute. There are three categories of users with permissions. In order they are the user, the group and everyone else. When you 'install' a file you are simply putting that file somewhere the computer or user can find it and making sure the proper permissions are set. 

Many/most 'programs' are actually packages of executable files and files the executables depend on, like configuration files. Installation packages consist of those files and (normally) automatic ways of putting the files in the right places with the right permissions. Sometimes the installation package is as simple as a tarred (archived and compressed) group of files. Untarring in or to the proper location may be all that is necessary. Most often when the package is opened (untarred) there will be a README or INSTALL text file with instructions. 

To make installation even easier, many distributions have package systems to do the installation. In the case of Ubuntu, which is based on Debian, these are '.deb' packages. Assuming the program you are looking for is in one of the repositories as a package, there are several ways to install but the most common is the command 'sudo apt-get install <package name>'. When this command is done the program/package has been installed and a lot of other things completed such as adding an entry to the menus and so on. Another way is through the Ubuntu Software Center listed in the main menu. A third is to find what you want in the Synaptic Package Manager (System|Synaptic Package Manager) in the main menu and have Synaptic install it. Lots of options for you. Look at them all. They each have strengths and weaknesses. Synaptic or the Software Center are probably easiest for beginners although apt-get (or aptitude or dpkg) will be useful at times. Remember the 'man' instruction?

Good luck, have fun. Ask all the questions you need to. There is always someone with experience ready to help once they understand the question. One caveat - be as specific as you can in the title of the thread. There are a lot of threads, people scan the titles to see what they want to look into and may not find something very, very general something they think they have time for or interest in. A specific topic makes their decision easier. As far as I know you are not limited to one thread at a time, either.

---

