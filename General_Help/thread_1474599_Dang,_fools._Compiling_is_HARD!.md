---
title: "Dang, fools. Compiling is HARD!"
date: 2010-05-06
forum: General Help
---

### Post by Scooter_X on 2010-05-06
Well at least that's what I think. I've tried to read a few tutorials on how to compile and such, and just don't get it. So as I try to install a game from source (called Tremulous), I'm gonna' be asking some probably basic questions, hoping someone can fill in the gaps for me as I go so I understand better what's going on. I'd sure appreciate it.

First question: I've unzipped/untarred the package, now pretty much every tutorial tells me to run ./configure, but when I do it says: "./configure: no such file or directory"... what's this ./configure DO and why does it think it's a directory? BTW, I think I already had a Makefile when I started. Might that have something to do with it?

---

### Post by mick222 on 2010-05-06
Why not just install from software centre or synaptic.If your trying to install the beta you must have version 1.1 installed first

---

### Post by Craig_Dem on 2010-05-06
> **Scooter_X said:**
> Well at least that's what I think. I've tried to read a few tutorials on how to compile and such, and just don't get it. So as I try to install a game from source (called Tremulous), I'm gonna' be asking some probably basic questions, hoping someone can fill in the gaps for me as I go so I understand better what's going on. I'd sure appreciate it.

First question: I've unzipped/untarred the package, now pretty much every tutorial tells me to run ./configure, but when I do it says: "./configure: no such file or directory"... what's this ./configure DO and why does it think it's a directory? BTW, I think I already had a Makefile when I started. Might that have something to do with it?

After you unzip it, you need to use;

cd <unzipped folder>
Then ./configure

I play tremulous :). And can confirm it works.

---

### Post by 3rdalbum on 2010-05-06
> **Scooter_X said:**
> 
First question: I've unzipped/untarred the package, now pretty much every tutorial tells me to run ./configure, but when I do it says: "./configure: no such file or directory"... what's this ./configure DO and why does it think it's a directory? BTW, I think I already had a Makefile when I started. Might that have something to do with it?

./configure says "Run this program called 'configure' in the current directory". Obviously, your terminal is not opened to the directory that contains Tremulous' "configure" file and source code.

You can use the 'cd' command and some drag 'n' drop foo:

```
cd <drag the folder into the terminal>
./configure
```

Or you can install the "nautilus-open-terminal" package from Synaptic. When you next log in, you can right-click in a Nautilus window and choose "Open Terminal Here", which ensures that the terminal is already navigated to where you want it.

Compiling is easy as long as you know how to get dependencies from the repositories and navigate a terminal :-)

Also, another tip: You can run:

```
./configure --help
```

and it will tell you what options the configure script allows. You can sometimes enable extra bleeding-edge features this way.

---

### Post by jim_24601 on 2010-05-06
I suspect that you're trying to apply a general "compiling" tutorial to a specific project. You need the "./configure" step for projects that use GNU autoconf. While many, if not most, open-source projects on Linux use autoconf, not all of them do. It looks as if Tremulous is one that doesn't. Try just typing "make" in the top-level source directory, and see where that gets you.

---

### Post by cbecker78 on 2010-05-06
Getdeb.net is an excellent alternative to compiling programs from source, if they have what you are looking for.

But on to your issue...

Maybe I'm off base here, but the issue could also be that you have no compiler installed on your system.  
```
sudo apt-get update
sudo apt-get install build-essentials
``` will download several compilers for you if you haven't run that before.

I think the most common method is to navigate to the directory you have extracted to in a terminal (applictions ->accessories -> terminal [for gnome])

```
cd /path/to/extracted/directory
```then
```
./configure
make
makeinstall
```but I usually just find compiliation directions for the specific program on line and follow whatever commands they tell me to enter  b/c I don't really know to much about that sort of stuff.

You may also want to get

```
sudo apt-get checkinstall
```which will allow you to substitute "makeinstall" with "checkinstall" -this installs it as a debian package and should allows you to uninstall the program later. i.e.;

```
./configure
make
checkinstall
```

---

### Post by Timtro on 2010-05-06
Every program is a little different, so it's ALWAYS good policy to look at he README or INSTALL text files that come with the software. They will usually provide instructions, and yes, usually it's just './configure, make, make install'.

To answer your other question, './configure' does a lot of things, but the main point is that it goes through a sort of checklist of things that you'll need in order to compile the program. Most programmers, rather than reinvent the wheel every time they want to do something, will use a library. If they do this, then the program will depend on that library. The main job of the configure script is to look for all of the dependencies and warn you if they're not there.

At the end, configure spits out a file that tells 'make' where everything is, and when you 'make' or 'make whatever', the make program will look at the makefile and know what it needs to do in order to build the program from the source code.

These steps are pretty standard, but not universal, so remember to check the documentation, at least the README. There are popular variants too, such as cmake. So you'll get to know them.

With some practice, you'll come to find that compiling things isn't so bad.

---

### Post by Scooter_X on 2010-05-06
Woa, thanks guys for all the replies, I've gotten a lot of information out of all this. I'm not gonna' go and comment on what everyone has said, but thanks to y'all because now I know what ./configure DOES and that generally I would follow the steps: ./configure, make, makeinstall. (is there a space between 'make' and 'install' right there?)

I've RE-downloaded the package and I'm starting over (ridiculous). When I untar the file that says: "tremulous-1.1.0-src" and open it up, I find some folders, some GPL stuff and a Makefile. I don't know why there's already a Makefile... Anyway, there's a lack of documentation that tells me what to do and where to run any ./configure make makeinstall, so I assume that the same place that contains the Makefile would be the place to start! I did, and nothing. Within that folder there's another called 'src' I open that, run ./configure and guess what? Nothing happens.

Because I already had a Makefile, I decided to just run 'make' and it looked like that part worked, then tried 'makeinstall' and got complaints about makeinstall: command not found.

---

### Post by WorMzy on 2010-05-06
Yes, there's a space between make and install, also you should use "sudo make install" rather than just "make install", as most programs will attempt to copy themselves into directories that only root has access to. :)

Pay attention to any errors that occur during ./configure, as these will tell you what unmet dependencies you have which will cause "make" to fail.

---

### Post by Scooter_X on 2010-05-06
Yea, that's the thing, ./configure doesn't DO anything. And there was already a makefile there when I started.

When I run:
sudo make install

I get:
make: *** No rule to make target `install'.  Stop.

What's that mean?

---

### Post by mb_webguy on 2010-05-06
Just out of curiosity, but why are you trying to compile Tremulous when it's in the repositories?  You can install it from the terminal with the command "sudo apt-get install tremulous".

---

### Post by xXREPOMANXx on 2010-05-06
Their are many compilers. It is not that hard when you get the hang of it. Try different compilers.

---

### Post by WorMzy on 2010-05-06
No, no, nononono. There's no need to reinstall just because make is throwing an error.

That error, to me, suggests that you're either a) not running the make command from within the right directory, or b) the makefile is malformed. In either case, installing via apt-get is the best solution in this scenario.

---

### Post by Scooter_X on 2010-05-06
> **mb_webguy said:**
> Just out of curiosity, but why are you trying to compile Tremulous when it's in the repositories?  You can install it from the terminal with the command "sudo apt-get install tremulous".

The point isn't so much to play the game, but to compile it from source. I want to figure out how to do that. What're the little things that I don't get that are hanging me up?

---

### Post by sgosnell on 2010-05-06
One of the 'little things' may be that you have to be in the proper directory in order to configure, compile, make, and install.  You have to have a proper makefile before you can make a package, and you must have made the package before you can install it.  I don't know if you have all the necessary packages already installed.  Have you installed build-essential?  

Is there a configure script in the current directory?  './configure' means "run the script named configure, in the current directory".  If there is no file with that name, then nothing will happen. You should see a lot of text flash by in the terminal if it does run.  Use Nautilus or 'ls' to see if it exists.  Also make sure it has the executable bit set.

---

### Post by dalee on 2010-05-06
Hi,

I don't have the Tremulous src files. But if you open the tarball, you should find various readme files. One of them will give you some guidance on how to install that program.

As has been pointed out, ./configure command isn't always needed. You may only need to
```
make
``` 
and then ```
sudo make install
```

But in any case look through the unpacked directory for readme files.

dalee

---

### Post by dalee on 2010-05-06
Hi,

Sorry, double tap.

dalee

---

### Post by Scooter_X on 2010-05-06
[QUOTE=sgosnell]
Is there a configure script in the current directory?  './configure' means "run the script named configure, in the current directory".  If there is no file with that name, then nothing will happen. You should see a lot of text flash by in the terminal if it does run.  Use Nautilus or 'ls' to see if it exists.  Also make sure it has the executable bit set.[/QUOTE]


Yea it turns out that there is NOT anything named configure in any of them directories. I went to another source package I had downloaded to try and compile myself, and there is one there, so that seems to be what's going on. I never realized that ./configure meant
 that it was running something that was in that very directory, I just figured it was a program somewhere on my hard drive that knew to configure the source files that were in the current directory.

[QUOTE=dalee]As has been pointed out, ./configure command isn't always needed.[/QUOTE]

That's what I seem to be finding out. Very slowly. Dang. ;)

---

### Post by 3rdalbum on 2010-05-07
What do the instructions provided with Tremulous say?

Tremulous might not use Make, it might use Jam or Scons instead. You need to read the README and INSTALL files inside the archive to see exactly how Tremulous is built.

---

### Post by longanduselessname on 2010-05-07
There is a command to run ./configure and output all failed dependencies to a file, instead of having it fail one after another...

Man I forget what it is though. But it is very useful.

Though my hate for compiling is why I am using ubuntu heh.

---

### Post by tgalati4 on 2010-05-07
If you want to compile something from scratch, try audacity, the sound editing program.  The version in the repositories is usually pretty old, and it compiles in Ubuntu.  Sometimes the newer version is craptastic and you want the simplicity of the older program.  This example includes several issues that you will run into when compiling any program.

[http://ubuntuforums.org/showthread.php?t=1349015&highlight=compile+audacity](http://ubuntuforums.org/showthread.php?t=1349015&highlight=compile+audacity)

[http://ubuntuforums.org/showthread.php?t=1169537&highlight=audacity](http://ubuntuforums.org/showthread.php?t=1169537&highlight=audacity)

---

### Post by Scooter_X on 2010-05-07
> **3rdalbum said:**
> What do the instructions provided with Tremulous say?

Tremulous might not use Make, it might use Jam or Scons instead. You need to read the README and INSTALL files inside the archive to see exactly how Tremulous is built.

There are no instructions. Serious! Here's my output in the file that I downloaded, then what's inside the -src folder. Maybe it does use Jam or Scons, but I wouldn't know how to tell.

```
user@computer:~/Downloads/tremulous$ ls
base       COPYING     tremded.x86                 tremulous.exe  tremulous.xpm
CC         GPL         tremulous-1.1.0-src         tremulous.ico
ChangeLog  manual.pdf  tremulous-1.1.0-src.tar.gz  tremulous.x86

user@computer:~/Downloads/tremulous$ cd tremulous-1.1.0-src

user@computer:~/Downloads/tremulous/tremulous-1.1.0-src$ ls
build  ChangeLog  cross-make-mingw.sh  Makefile  src
CC     COPYING    GPL                  misc      ui
user@computer:~/Downloads/tremulous/tremulous-1.1.0-src$ 

```> **tgalati4 said:**
> If you want to compile something from scratch, try audacity, the sound  editing program.  The version in the repositories is usually pretty old,  and it compiles in Ubuntu.  Sometimes the newer version is craptastic  and you want the simplicity of the older program.  This example includes  several issues that you will run into when compiling any program.

[http://ubuntuforums.org/showthread.p...mpile+audacity]("http://ubuntuforums.org/showthread.php?t=1349015&highlight=compile+audacity")

[http://ubuntuforums.org/showthread.p...light=audacity]("http://ubuntuforums.org/showthread.php?t=1169537&highlight=audacity")

Yeah, I'm gonna' try that. And others to see if this one is just a goofed-up exception or something... Thanks for the links.

---

### Post by nothingspecial on 2010-05-07
There is a build file, some times you have to ./build instead of ./configure or ./make. (The developer could call it banana if (s)he wished.

Also, have you looked at the manual.pdf?

---

### Post by Scooter_X on 2010-05-07
> **nothingspecial said:**
> There is a build file, some times you have to ./build instead of ./configure or ./make. (The developer could call it banana if (s)he wished.

Also, have you looked at the manual.pdf?

Sorry, should've posted a screenshot. build is a directory. And yeah, the manual is just instructions for playing the game.

---

### Post by Seventh Reign on 2010-05-07
This is why so many people think compiling from source and ,Installing Apps in Linux in general, is hard.  Actually doing it is super easy, but there are too many different WAYS of doing, and not all ways work on all applications.

I'm definitely not saying Window's .exes are better.  They're not.  But atleast (for the most part) that is your main way of installing a windows app. 

I couldnt name all the different methods of installing Linux Apps.  

If we want GNU/Linux to compete with Windows and Mac, then a unified installer is the #1 Priority.

---

### Post by bredman on 2010-05-07
If there are no instructions, then the authors have probably put everything into a script file with a name so obvious that they didn't think it was worth describing.

To see all the executable scripts in the current directory and below, put this command into the terminal (be careful with spaces)
find . -type f -executable -print

Note that the . after the find means the current directory, but I see above that you have learned this the hard way...

The other parameters mean: Find only files, not directories; find only executable files; print out the names of the files.

Hopefully this will show you a script with a name which is blindingly obvious.

---

### Post by Scooter_X on 2010-05-07
> **Seventh Reign said:**
> 
If we want GNU/Linux to compete with Windows and Mac, then a unified installer is the #1 Priority.

I think Linux is competing OK, but I see what you mean. For Linux to  really come out into the open and bite Microsoft's head off, the unified  installer like you mentioned is definitely needed.

> **bredman said:**
> 
If there are no instructions, then the authors have probably put  everything into a script file with a name so obvious that they didn't  think it was worth describing.

To see all the executable scripts in the current directory and below,  put this command into the terminal (be careful with spaces)
find . -type f -executable -print

Note that the . after the find means the current directory, but I see  above that you have learned this the hard way...

The other parameters mean: Find only files, not directories; find only  executable files; print out the names of the files.

Hopefully this will show you a script with a name which is blindingly  obvious.     

That's a great idea, thanks for that code. I'll try that as soon as I get back home to my computer.

---

### Post by tgalati4 on 2010-05-07
The other thing to consider is you need to duplicate the build environment for the app that you are interested in.

For instance, tremulous has been around a long time and probably compiles OK from Dapper to Lucid.  Banshee on the other hand relies on Mono and the latest version only compiles on a recent release of Ubuntu, such as Karmic.  If you want to compile Banshee for Dapper Drake, then you have to compile Mono for Dapper.  I don't think Mono even exists for Dapper.

This is known as "Depencency File Hell".  You want to compile a certain package on a certain linux distro.  You also need all of the current libraries that the package is compiled against.  Some of these libraries are quite difficult to find or compile because they rely on other frameworks, languages, toolkits, etc.  

So for tremulous, do some searching to find out who the lead developer is and find out what the current build environment is.  Then either find a machine and try to duplicate that exact build environment, or make modifications to your current distro so it looks similar to the developer's build environment.

If tremulous is being developed using Karmic and you are trying to build it on a Hardy system, you will certainly run into problems.

./configure is a script that examines your build environment and sets build environment variables that are appropriate to compile the package.  It's a good system and it does a pretty good job pointing out what parts of your build environment are missing.  But it does miss some situations.  So you get a successful configuration, but you still get compile errors because of mismatched libraries, or a missing widget kit, etc.

It amazes me that any of this stuff works at all.

---

### Post by WinterRain on 2010-05-07
I understand if you want to learn how to compile, but if you just want tremulous, just download it from the ubuntu software center. Click to install.

---

### Post by sgosnell on 2010-05-08
I can't tell for sure from your screenshot, but I don't think you're in the source directory.  You probably need to cd tremulous-1.1.0-src, if that's a directory.  I also see the tar.gz file, have you extracted that?  There is no source code at all in the directory you're in, so compiling there is simply impossible.

---

### Post by ramjet_1953 on 2010-05-08
This script on the Tremulous website might make things easier for you.

[http://tremulous.net/forum/index.php?topic=10664.0](http://tremulous.net/forum/index.php?topic=10664.0)

Regards,
Roger :p

---

### Post by Timtro on 2010-05-17
> **WorMzy said:**
> Yes, there's a space between make and install, also you should use "sudo make install" rather than just "make install", as most programs will....

I STRONGLY recommend using checkinstall instead of sudo make install. Checkinstall (sudo apt-get install checkinstall) will make a .deb package that can be removed cleanly from synaptic. I don't like to simply trust that 'make uninstall' will do it's job as advertised.

---

