---
title: "Some general questions regarding ubuntu and linux"
date: 2011-11-19
forum: General Help
---

### Post by psyhprog on 2011-11-19
I'm not a new user to Ubuntu and the likes, but I haven't managed to get into it as much as I would like to. I have a few questions that I hope you can address for me:

[LIST=1][*]I know the basic commands of the console, but I'm by no means good, and I can't really do what a power user would do in terms of scripts. I know this is more of a linux question than an Ubuntu one, but nonetheless.[*]A few times I had to install drivers, and more often than not, they had to be done 'manually'. Problem is that I'm not a console power user, I have no idea how to get and compile the kernel, what to do with the drivers. Basically, other than copy-pasting some commands off of some page, I'm kinda stuck.[*]I also would like to know, or to learn, how to setup an Apache with PHP and MySQL server from start. How to make everything work, and ideally from console (not through the GUI, as I have a sense that is easier).[*]And one last thing, I'd like to know more about how to install some things yourself. (Getting the source, compiling it and all that is necessary).




[/LIST]

---

### Post by Telengard C64 on 2011-11-19
[list=1]
[*]Was there a question here? Did I miss it?
[*]Can't help you here. The only *driver* I've ever installed is for my nVidia card, and that's not so hard.
[*]Dunno.
[*]Compiling from source should almost never be necessary on Ubuntu. Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and find the package name of the program you want to install. Then enter **sudo apt-get install package-name**. Or else you could just use the graphical package manager like most people probably do.
[/LIST]

HTH

---

### Post by psyhprog on 2011-11-19
> **telengard c64 said:**
> [list=1]
[*]was there a question here? Did i miss it? **the question was if you can provide any useful resources for becoming a terminal power-user.**
[*]can't help you here. The only *driver* i've ever installed is for my nvidia card, and that's not so hard. **yea, i know about nvidia.** but what about the alsa ones?
[*]dunno.
[*]compiling from source should almost never be necessary on ubuntu. Go to [http://packages.ubuntu.com](http://packages.ubuntu.com) and find the package name of the program you want to install. Then enter **sudo apt-get install package-name**. Or else you could just use the graphical package manager like most people probably do. **yes, but what if i want to, or some programs like clamav (only has source) or even php. What do i do then?**
[/list]

hth
 a

---

### Post by Telengard C64 on 2011-11-19
> **psyhprog said:**
> the question was if you can provide any useful resources for becoming a terminal power-user.

See [this post on KFN](http://kubuntuforums.net/forums/index.php?topic=3104843.msg186737#msg186737). Skip down to the section titled *Command line documentation*. Beyond man pages and info documentation, try some of these web sites:

[list]
[*][UsingTheTerminal - Community Ubuntu Documentation](https://help.ubuntu.com/community/UsingTheTerminal)
[*][GNU Manuals](http://www.gnu.org/manual/manual.html) for the multitude of GNU programs common to Linux systems
[*][Basic UNIX commands](http://doors.stanford.edu/~sr/computing/basic-unix.html)
[*][More UNIX Commands](http://doors.stanford.edu/~sr/computing/more-unix.html)
[*][LINUX: Rute User&#8217;s Tutorial and Exposition by Paul Sheer](http://rute.2038bug.com/) teaches Linux command line from the perspective of a former MS-DOS user
[*][The Linux Users' Guide by Larry Greenfield](http://www.ibiblio.org/pub/Linux/docs/linux-doc-project/users-guide/!INDEX.html)
[*][The Linux Tutorial by James Mohr](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224)
[*][LinuxCommand.org: Learning the shell.](http://www.linuxcommand.org/learning_the_shell.php)
[*][An A-Z Index of the Bash command line for Linux.](http://ss64.com/bash/)
[*][Bash by example, Part 1](http://www.ibm.com/developerworks/linux/library/l-bash/index.html)
[*][Learn Linux, 101: The Linux command line](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-1/index.html)
[*][Learn Linux, 101: File and directory management](http://www.ibm.com/developerworks/linux/library/l-lpic1-v3-103-3/index.html)
[*][Linux Files and Command Reference](http://www.comptechdoc.org/os/linux/commands/)
[*][Agustin's Linux manual - Volume 2 - System Administration](http://www.comptechdoc.org/os/linux/manual2/aboutauthor.html)
[*][BashGuide BashPitfalls BashFAQ - Greg's Wiki](http://mywiki.wooledge.org/)
[*][Bash Guide for Beginners](http://tille.garrels.be/training/bash/)
[*][Learn UNIX in 10 minutes](http://freeengineer.org/learnUNIXin10minutes.html)
[*][http://freeos.com/guides/lsst/index.html](http://freeos.com/guides/lsst/index.html)
[*][GNU/Linux Tools Summary](http://www.karakas-online.de/gnu-linux-tools-summary/)
[*][Linux.ie :: The Beginners Linux Guide](http://www.linux.ie/newusers/beginners-linux-guide/)
[*][Linux Classes and Training.  Free Linux Lessons.](http://lowfatlinux.com/)
[*][Main Page - Linux Shell Scripting Tutorial - A Beginner's handbook](http://bash.cyberciti.biz/guide/Main_Page)
[/list]

HTH :)

> yes, but what if i want to, or some programs like clamav (only has source) or even php. What do i do then?

Eh? The **clamav** and **php5** packages have been available in the Ubuntu repositories since at least 8.04 Hardy Heron.

[http://packages.ubuntu.com/search?keywords=clamav&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=clamav&searchon=names&suite=all&section=all)

[http://packages.ubuntu.com/search?keywords=php5&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=php5&searchon=names&suite=all&section=all)

_**edit**_
While I don't understand why you'd want to compile clamav and php5 from source, I suppose you may have your own reasons. If so then please read [CompilingSoftware - Community Ubuntu Documentation](https://help.ubuntu.com/community/CompilingSoftware).

 Before you go to all that trouble, please consider that an Ubuntu package probably already exists for any Linux program you can think of. If not in [the Ubuntu repos](http://packages.ubuntu.com), then possibly in [the PPAs](https://launchpad.net/ubuntu/+ppas). Many programs also have pre-compiled binaries for Ubuntu available on their websites.

It really is almost never necessary to compile from source on Ubuntu. Unless you are a developer, or learning to become one, I can't recommend it.

---

### Post by psyhprog on 2011-11-19
Thanks for the answer, and as for installing Apache, I'm having some trouble installing it. I downloaded the source and extracted it. I first did a sudo ./configure PREFIX=/webserv/apache (set the directory to install apache) and after that make and make install both with sudo. It took about 5 minutes, lots of scrolling text, and all that, no errors at the end, no interrupted executions and in the end the /webserv/apache directory is empty and the installed files are nowhere to be seen.

I fixed it. You had to run sudo ./configure --prefix=/putprefixhere/...

---

### Post by Telengard C64 on 2011-11-19
> **psyhprog said:**
> Thanks for the answer, and as for installing Apache, I'm having some trouble installing it.

Maybe this will help?

[ApacheMySQLPHP - Community Ubuntu Documentation](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by devinwhite717 on 2012-03-17
Ubuntu is good for new and experienced users

---

