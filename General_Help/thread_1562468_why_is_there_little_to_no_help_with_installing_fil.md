---
title: "why is there little to no help with installing files and programs?"
date: 2010-08-27
forum: General Help
---

### Post by amaruq_atka on 2010-08-27
it takes me days sometimes to install programs because i have to read hundreds of pages of documentation and never come up with an answer. true a quick google search will tell me how to install a .bin file, but what about when i get errors? or it says it doesn't exist? permission denied even with sudo? or any other minute complication that no matter where i look the answer is always someone referencing something that does not work? some things install themselves while other involve a much complicated command line sequence of errors. dont get me wrong, I love the terminal, i even kinda find it a hobby to learn this stuff and know what do do when. if i could only learn and decode what its trying to tell me! or even how to install various types of files, or even files that have no extension. is there anything, anywhere that can help me? what to do when you run into random errors or even where to look for them? most of my problem is things telling me to install packages that dont even exist, and if they do its giving me the wrong name to be searching for anywhere.

---

### Post by wyliecoyoteuk on 2010-08-27
There is a very simple way to install programs.
It is called Synaptic package manager, and it offers thousands of programs.
If you are trying to install programs that are not in the repositories, then it will be hard, because these programs are not supported by Ubuntu.
You can add repositories that are not officially supported.
But if you are complaining because there are no .exe files, well that is why Linux is more secure than windows.

By default, any file or script that is downloaded in not executable. This is a simple protection mechanism.
Making the file executable is a conscious decision, and is not difficult.
However, installing using scripts (bin files ) is essentially risky.
Using .deb packages is far safer, and means that dependencies should be sorted automatically.

---

### Post by wojox on 2010-08-27
> **amaruq_atka said:**
>  is there anything, anywhere that can help me? what to do when you run into random errors or even where to look for them? 

When I have a problem I post here and receive help. Just explain what your doing and what error is being thrown. :p

---

### Post by Dragonbite on 2010-08-27
What are you trying to install?  You might find it is easily available in Ubuntu's package management system.

Unlike Windows where you have to go to Mozilla's site for Thunderbird, and Adobe's site for Flash and Google's site for Chrome Linux uses a centralized repository where these programs are tweaked specifically for Ubuntu and tested before being made available.

Ubuntu's package management system is available through a few different ways.  Don't worry, pick the one you prefer but they all are using the same system so changing it in one changes it in all.


One way is to use Synaptic, which Ubuntu has used for a long time and you can search through the available packages, update (refresh) the list of applications and install what you find.
System > Administration > Synaptic 

Another is Ubuntu Software Store, located at the bottom of the "Applications" menu selector.  It is made to be easier and less confusing to find and install applications.  Unlike Synaptic, when you do a search you get a more "high-up" view of programs and not necessarily the individual libraries (which are like .dll's) as you do in Synaptic.

The third is the command line. If you are comfortable with this then great, if not don't sweat it, you still have the two (gui) choices listed above.  Often you will get people answering with command-line code. This is because it is easier to describe as text is text, as opposed to "click here then here" and come to find they changed the button location between releases ;).

As always, feel free to ask.  Maybe people are on vacation, maybe they are sleeping, but usually questions will get answered eventually.

Oh, and welcome to Ubuntu. :)

---

### Post by Vaphell on 2010-08-27
first and foremost - stick to the repositories, maybe PPAs and maybe, maybe .deb files and you will do fine :) how often do you install something from .bin files? what's so necessary out there that you need to install stuff manually?

either way:
google is your friend, paste the error message verbatim and hope some people had similar problem. Usually they had. ubuntuforums ain't bad either.

permission denied/file not found and similar usually mean 'you don't own the file/directory' or 'it's not marked as an executable' or simply 'there is no such thing here, you kiddin' me?'
Also running too much stuff with sudo/gksudo can cause your config dirs/files (usually <dot><appname> ie .mozilla, .opera) to be acquired by root and you as an ordinary user can't access them anymore and the app fails.
to test these run ls -la <file/dir_in_question>. Learn to love 'user usergroup drwxrwxrwx' part, it tells you pretty much everything you need to know, chown and chmod commands to the rescue
90% of cases (if not more) belongs here.

various files or even without extension - it doesn't matter what the names or extensions are, either file is marked as an executable or it's not. You can set jpeg as an executable if you want but it will simply fail when run.

installation from source (compressed tar.gz files usually) goes usually like that:
- decompress the archive
- check if you got build-essential package installed
- perform './configure, make, sudo make install' combo
if it fails at the 'make' step - read error (missing library? install it, something weird? paste the error into google)

---

### Post by amaruq_atka on 2010-08-27
ill be honest with you guys, i hate asking for help, i love giving all the help i can but when it comes to ubuntu, i have no idea what im doing. and it feels odd to me. all i really want is some sort of guide. but if you can help thats great. my issue is that the things want to install are not in the package manager. i need ksxldbg, for quanta plus, a program i want to use as a learning tool. now there are prerequisite to having that, something called libxml2-2.7.7 (because thats the newest) and i cant find it in package manager, somehow i found it and downloaded it, it has no file type gzip type in properties. and form here i dont know what do do. it says "an error occurred while extracting files" when i try to extract it. now im stuck.

---

### Post by oldos2er on 2010-08-27
> **amaruq_atka said:**
> all i really want is some sort of guide. but if you can help thats great. 

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

If you have questions about a specific program (and it sounds like you do), please provide a link to the program, and any relevant terminal output (commands and error msgs).

---

### Post by coffeecat on 2010-08-27
> **amaruq_atka said:**
> i need ksxldbg, for quanta plus, a program i want to use as a learning tool. now there are prerequisite to having that, something called libxml2-2.7.7

Quanta Plus is in the Ubuntu repository. kxsldbg (note the spelling) is listed as a recommended package, and that is in the repository as kxsldbg-kde3. And the version of libxml2 suitable for the version of kxsldbg in the repos is also there.

Simply open Synaptic, mark Quanta and kxsldbg for installation and the dependencies will be marked automatically. You are a few clicks away from installing Quanta Plus with all the dependencies taken care of for you - automatically. It is easier, far easier, than installing stuff in Windows.

---

### Post by gamblor01 on 2010-08-27
> **amaruq_atka said:**
> all i really want is some sort of guide. but if you can help thats great. 

As a general note, this is going to be very difficult to do.  There are so many various ways of installing stuff in Linux.  Just to name a few off the top of my head that would be relevant to Ubuntu (and other Debian-based distros) in particular:

1. tarballs

A tar file is simply an archive, though usually they are compressed and will therefore end in another extension.  ".gz" and ".bz2" are common.  Usually you have to extract the tar and then follow the instructions inside of the readme file.  The most common thing is that the code is C/C++ code and you have to compile it yourself:

```
$ ./configure
$ make
$ sudo make install
```Other times the tar may include a shell script that will install the program for you, a binary file which has to be executed -- you never really know.  It's always best to check the web site/readme for this program to see how it's done.

Compiling source code often requires a considerable amount of build utilities.  The most common ones are put into a package for you named build-essential.  I would highly recommend you install that before doing anything:

```
$ sudo apt-get install build-essential
```2. You can use something like synaptic, or apt (a command line tool).  For example, to install the tofrodos package (for converting files between Windows/Unix end-of-line characters) you can do use:

```
$ sudo apt-get install tofrodos
```3. You might download a .deb file directly in which case you can use dpkg:

```
$ sudo dpkg -i foo.deb
```etc. etc.  There are many different options when using Linux, which unfortunately confuses new users, and rightfully so.  After a while you just sort of get the hang of things and it becomes second nature.  Remember, you weren't an expert when you first started using Windows either.  If you want proof of that, just look at my mother-in-law...



One thing that may help is that you can search the repositories using apt-cache.  Generally you'll want to leave off the version number, so for example, try this search (note it will give you quite a few results!):

```

$ apt-cache search libxml2
```When I run this search on my system I see this package:

```
libxml2 - GNOME XML library".  
```So to install that package you could just use:

```
sudo apt-get install libxml2
```Ok, so back to what you really want...I googled ksxldbg and it looks like it's a KDE debugger for web development.  Looking at their page I see they release .tar.bz2 files.  So here is what I would recommend to get the build essentials, extract, compile, and install.  Start by opening and terminal, and then cd in the directory where you downloaded the file.  Obviously, the stuff in parenthesis are my comments so don't type that stuff.


```

$ sudo apt-get install build-essential     (go through the prompts to install it)
$ dpkg -l | grep libxml2                   (this will confirm if you already have it installed, and what version)
$ bunzip2 kdewebdev-3.5.8.tar.bz2          (decompress)
$ tar -xf kdewebdev-3.5.8.tar              (untar)
$ cd kdewebdev-3.5.8/                      (self-explanatory!)
$ ./configure                              (checks pre-reqs on your system)
$ make                                     (uses info in the Makefile to actually compile the C++ code for your architecture)
$ sudo make install                        (installs the code!!)

```I didn't check to see where they install by default but it's usually somewhere in /usr/local/bin.  If you want to change the install path, pass in the --prefix option to configure.  For example, I could change the install directory to be in my home directory by doing this:

```

$ ./configure --prefix=/home/myuser/programs/quantaplus

```Good luck to you.

---

### Post by amaruq_atka on 2010-08-27
you guys are awesome! i want to be like you some day. got the kxsldbg in, but now its asking for cervisia from [http://www.kde.org/apps/cervisia](http://www.kde.org/apps/cervisia), but i already have that installed according the the package manager.

---

### Post by gamblor01 on 2010-08-28
> **amaruq_atka said:**
> you guys are awesome! i want to be like you some day. got the kxsldbg in, but now its asking for cervisia from [http://www.kde.org/apps/cervisia](http://www.kde.org/apps/cervisia), but i already have that installed according the the package manager.

So what exactly did you do to "get the kxsldbg in" ??  Did you extract the source code and compile it as I mentioned previously?  If so, what is the exact error message when you launch the binary?  You may have cervisia installed, but maybe it's looking for a different version or something.  Please post:

1. The output when you attempt to run the kxsldbg command.

2. The output of the command:  dpkg -l | grep cervisia



We'll go from there...


**EDIT:**  Sorry I didn't check this previously but you might have an easier time if you just use apt to install kxsldbg for you.  I just did an "apt-cache search kxsldbg" and it finds it in the repository.  So maybe you should just delete anything you compiled manually and just run:

```

sudo apt-get install kxsldbg cervisia

```

Actually just running "apt-get install kxsldbg" is probably sufficient.  It will automatically find any dependencies and download those for you.  If you already have some of the packages, it will figure that out too.


The advantages to installing a pre-compiled binary through the package manager:

1. it resolves dependencies automatically
2. requires less knowledge
3. requires less time (you don't have to compile the source yourself)
4. will provide updates through the update manager when they are available. 



The advantages to installing through source:

1. Pre-compiled binaries may not be available for your architecture.  This is unlikely if you're running an x86 processor but applies quite often for those running on powerPC, SPARC, etc.  Sometimes you may actually find that 32-bit binaries are available but not 64-bit.  :(
2. When you compile the code yourself, you can modify it.  For example, you can enhance it to perform some new function for yourself, or apply a patch that isn't yet available in a binary version.




In any case, I suggest you just use apt to install what you need.  Sorry, but yesterday I did an apt-cache search for quantaplus, but never ran a search for kxsldbg.  It turns out it's in the repo though.  I would highly recommend you just use that version.

In general I always install the pre-compiled binaries (when available) unless there is some specific reason that I need to compile the code myself.

---

