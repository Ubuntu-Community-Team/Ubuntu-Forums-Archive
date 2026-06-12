---
title: "compiling vs installing"
date: 2011-04-04
forum: General Help
---

### Post by roboticmehdi on 2011-04-04
Hello ubuntu users :) Im new, not only in ubuntu, but in the whole GNU/Linux world. I have been using windows vista before but trying to install windows 98 near to it i lost both of them and i wounded up using ubuntu. i wasnt intentional but im really glad that it happened. But trying to undesrtand it i also sometimes get angry at it :D i know how work with computer and i also know programming a little bit. I began programming in turbo pascal 7.0 then i learned others too. i also know a little bit assembly i guess :D So anyways, i want to ask general gustions about ubuntu and GNU/Linux when i have problems, of course evebosy can ask question but i would like this to be a little different. Please do not ask irrelevant questions until the current problem is solved. also please try to give full and meaningful answers. Remember i am a BEGINNER here. :P So here is my first question:

In windows the programs( also called applications) get into computer in two ways, you either download(or buy) a installer program which installs the program in "program files"(though not necessary) folder. OR you get( or write by yourself) a source code and compile it using the right compiler program and get an executable which you can run.

So how does it happen in ubuntu ??

---

### Post by Grenage on 2011-04-04
> **roboticmehdi said:**
> Hello ubuntu users :) Im new, not only in ubuntu, but in the whole GNU/Linux world. I have been using windows vista before but trying to install windows 98 near to it i lost both of them and i wounded up using ubuntu. i wasnt intentional but im really glad that it happened. But trying to undesrtand it i also sometimes get angry at it :D i know how work with computer and i also know programming a little bit. I began programming in turbo pascal 7.0 then i learned others too. i also know a little bit assembly i guess :D So anyways, i want to ask general gustions about ubuntu and GNU/Linux when i have problems, of course evebosy can ask question but i would like this to be a little different. Please do not ask irrelevant questions until the current problem is solved. also please try to give full and meaningful answers. Remember i am a BEGINNER here. :P So here is my first question:

In windows the programs( also called applications) get into computer in two ways, you either download(or buy) a installer program which installs the program in "program files"(though not necessary) folder. OR you get( or write by yourself) a source code and compile it using the right compiler program and get an executable which you can run.

So how does it happen in ubuntu ??

It can happen both ways; the package manager will download binaries for installation, but it's not uncommon to manually download and compile code.

It's a lot less common than it used to be, but it still happens.

---

### Post by Dupointx on 2011-04-04
> **roboticmehdi said:**
> 

In windows the programs( also called applications) get into computer in two ways, you either download(or buy) a installer program which installs the program in "program files"(though not necessary) folder. OR you get( or write by yourself) a source code and compile it using the right compiler program and get an executable which you can run.

So how does it happen in ubuntu ??

I'm not the most experienced user here, but I'll take a shot at answering your question.

In Ubuntu you usually install applications by using the repos. This is a collection of programs that are deemed 'usable on Ubuntu' by the developers (I think). There are a lot of ways to get programs from the repos. I'll list a few that Ubuntu uses just to elaborate: Software Center, Synaptic Package Manager, apt-get (command line), aptitude (command line).

You can also add applications to the repo list on your computer by adding PPAs (Personal Package Archives). This lets you install and keep updated (through Update Manager or command line) applications that may not be in the Ubuntu repos.

You can also install stand alone applications from websites (files that end with .deb -Debian software package). This is like downloading .exe or .msi files on Windows. Be sure to check that the files are useable on Ubuntu however (most are), Ubuntu and Debian are not the exact same thing.

As far as compiling your own code it's about the same as Windows except you have to make a file that is executable after compiling it. Then to run it just put ./ before the name (in command line).

Hope that answers your question :D

---

### Post by roboticmehdi on 2011-04-04
> **Grenage said:**
> It can happen both ways; the package manager will download binaries for installation, but it's not uncommon to manually download and compile code.

It's a lot less common than it used to be, but it still happens.
In windows you can twice clik on program icon and run it. Is it the same in ubuntu? im asking this because i wasnt successful in doing that yet.

---

### Post by Grenage on 2011-04-04
> **roboticmehdi said:**
> In windows you can twice clik on program icon and run it. Is it the same in ubuntu? im asking this because i wasnt successful in doing that yet.

If it's a deb package, yes; if it's source code, no.  Sometimes you'll download a bin file, and that usually needs to be made executable before you can click on it to run it.

Basically, they're not dissimilar - a package compiled for windows will install with a single click, as will one for Ubuntu/Debian.

---

### Post by roboticmehdi on 2011-04-04
> **Grenage said:**
> If it's a deb package, yes; if it's source code, no.  Sometimes you'll download a bin file, and that usually needs to be made executable before you can click on it to run it.

Basically, they're not dissimilar - a package compiled for windows will install with a single click, as will one for Ubuntu/Debian.
I wrote a simple "hello world" program saved it as mhd.c and compiled it using gcc -o mhd mhd.c but when i clikck it it doesnt run. why ?

---

### Post by Grenage on 2011-04-04
> **roboticmehdi said:**
> I wrote a simple "hello world" program saved it as mhd.c and compiled it using gcc -o mhd mhd.c but when i clikck it it doesnt run. why ?

I've not had much experience with C (or too much coding in general), but since your program probably doesn't have a GUI, you'll surely want to run it from a terminal?

---

### Post by Dupointx on 2011-04-04
> **roboticmehdi said:**
> I wrote a simple "hello world" program saved it as mhd.c and compiled it using gcc -o mhd mhd.c but when i clikck it it doesnt run. why ?

Navigate to the directory the file is in the terminal -> type "ls" -> if there is a file with the same name that is green then you have a file you can execute. If not then there's something not right with your compiling.

To run the executable file type "./ <file name>". 

I'm not sure about running it by clicking it in GUI. Have not tried that yet.

---

### Post by roboticmehdi on 2011-04-04
> **Grenage said:**
> I've not had much experience with C (or too much coding in general), but since your program probably doesn't have a GUI, you'll surely want to run it from a terminal?
GCC(GNU Compiler Collection) is a program right? where is its location ?

---

### Post by Grenage on 2011-04-04
> **roboticmehdi said:**
> GCC(GNU Compiler Collection) is a program right? where is its location ?

type:

```
which gcc
```

That said, the location you'll need is that of your compiled program, which will be wherever you compiled it.  As Dupointx pointed out, start off in that directory; if you compiled it in your home folder:

```
cd ~
./*compiledname*
```

---

### Post by QLee on 2011-04-04
[QUOTE=roboticmehdi]...So anyways, i want to ask general gustions about ubuntu and GNU/Linux when i have problems, of course evebosy can ask question but i would like this to be a little different. Please do not ask irrelevant questions until the current problem is solved. also please try to give full and meaningful answers. Remember i am a BEGINNER here. ...[/QUOTE]

Welcome to the forum. It usually easy for experienced users to spot a beginner and the Ubuntu Forums are noted for being friendly to new user questions.

I want to mention this to help you avoid being disappointed or possibly even angry. These forums are available to people all over the world and tend to be a fairly representative sample of the population, thus you will find all types of people with all kinds of answers and even personal agendas. Regardless of whatever conditions you try and impose on replies, people will choose to answer as they want to, there will be misunderstandings, misintrepretations of any problem being discussed, sometimes even downright malicious answers. Often there could be questions unrelated to the trouble you are trying to fix (...or sometimes questions that you may not see as relevent). It can be up to you to take the help and ignore the stuff that you don't like but avoid taking anything as a personal affront, if that happens a moderator will deal with it. 

I wrote that in your thread but other new users will read it too.

For new users the best advice is to stick with the "official" repositories (repos) for software, that software has been checked as safe and is easiest for a new user to install. This link to the wiki page for repositories might help you to understand.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
There can be some danger in installing a program from an untrusted site and you should probably become more comfortable with Ubuntu before you start to compile your own.

---

### Post by roboticmehdi on 2011-04-04
> **Grenage said:**
> type:

```
which gcc
```

That said, the location you'll need is that of your compiled program, which will be wherever you compiled it.  As Dupointx pointed out, start off in that directory; if you compiled it in your home folder:

```
cd ~
./*compiledname*
```
and what about /usr/include  ? doesnt that belong to gcc?

---

### Post by 3Miro on 2011-04-04
Programs in Unix/Linux are usually split into logical components. /usr/bin contains executable, /usr/lib contain shared libraries (i.e. the Linux version of .dll), while /usr/include contains headers for many programing languages. This is in contrast with Windows, where each program has its own folder and keeps all of its components in one place. The Linux was is better when programs share components across, as it is usually the case with FOSS software. Proprietary software that dominates windows doesn't like sharing.

In every Linux distribution, it is recommended to install programs from the repository. Most distributions are binary providing pre-compiled packages, while some give you only source code (which then gets compiled in a semi-automated manner). Ubuntu and Fedora (and most others) are a binary distribution, Gentoo and Lunar are source distributions.

Under any distribution, you can download additional source code and compile it. This can be done for testing latest features of software, beta releases that have not made it into the repository yet, or more obscured programs that are not "popular" enough to be included. However, adding software outside the repository is not recommended, unless you know what you are doing.

If you want to make your own programs (or compile someone else's), under Ubuntu you should install "build-essentials" (look it up in Synaptic Package Manager). Build essentials will give you C/C++ compiler with necessary extra libraries and so on.

---

### Post by roboticmehdi on 2011-04-04
> **3Miro said:**
> Programs in Unix/Linux are usually split into logical components. /usr/bin contains executable, /usr/lib contain shared libraries (i.e. the Linux version of .dll), while /usr/include contains headers for many programing languages. This is in contrast with Windows, where each program has its own folder and keeps all of its components in one place. The Linux was is better when programs share components across, as it is usually the case with FOSS software. Proprietary software that dominates windows doesn't like sharing.

In every Linux distribution, it is recommended to install programs from the repository. Most distributions are binary providing pre-compiled packages, while some give you only source code (which then gets compiled in a semi-automated manner). Ubuntu and Fedora (and most others) are a binary distribution, Gentoo and Lunar are source distributions.

Under any distribution, you can download additional source code and compile it. This can be done for testing latest features of software, beta releases that have not made it into the repository yet, or more obscured programs that are not "popular" enough to be included. However, adding software outside the repository is not recommended, unless you know what you are doing.

If you want to make your own programs (or compile someone else's), under Ubuntu you should install "build-essentials" (look it up in Synaptic Package Manager). Build essentials will give you C/C++ compiler with necessary extra libraries and so on.
what if two different applications have files that are different but have same names. if they are put into same folder would'nt there be a conflict?

---

### Post by 3Miro on 2011-04-04
> **roboticmehdi said:**
> what if two different applications have files that are different but have same names. if they are put into same folder would'nt there be a conflict?

Yes, this would cause a problem. That is why we install things from a repository, all programs in the official repository are compiled so that no such conflicts arise. Additional repositories/programs should respect that as well, although, if you use "unofficial" repositories the conflicts are indeed possible. "Unofficial" repos should be avoided anyway, those are no different than going to a random web-page and downloading a program, you don't know what you are getting since there is no control.

If proprietary software is to be installed on a Linux machine, then it should behave like in windows i.e. put all of its stuff in one place so that it doesn't conflict with the rest of the system. Proprietary software should stay out of the repository. A good example for that is Matlab, it installs just like on Windows.

---

### Post by QLee on 2011-04-04
[QUOTE=roboticmehdi]what if two different applications have files that are different but have same names. if they are put into same folder would'nt there be a conflict?[/QUOTE]
Naturally there would be, however, you will find a difficulty pasting a file into a directory which already contains one of that same name.

---

### Post by roboticmehdi on 2011-04-04
> **3Miro said:**
> Yes, this would cause a problem. That is why we install things from a repository, all programs in the official repository are compiled so that no such conflicts arise. Additional repositories/programs should respect that as well, although, if you use "unofficial" repositories the conflicts are indeed possible. "Unofficial" repos should be avoided anyway, those are no different than going to a random web-page and downloading a program, you don't know what you are getting since there is no control.

If proprietary software is to be installed on a Linux machine, then it should behave like in windows i.e. put all of its stuff in one place so that it doesn't conflict with the rest of the system. Proprietary software should stay out of the repository. A good example for that is Matlab, it installs just like on Windows.
why doesnt windows and gnu/linux operating systems do not support each others executables? i know that it is possible with emulators but they are much slower than original programs.

---

### Post by Dupointx on 2011-04-04
> **roboticmehdi said:**
> why doesnt windows and gnu/linux operating systems do not support each others executables? i know that it is possible with emulators but they are much slower than original programs.

Short answer: Windows API is proprietary and can't be fully replicated on Linux.

Long Answer: Linux users can use WINE (Wine Is Not a Emulator) to run .exe files on Linux. WINE attempts to do stuff like Windows API and use Windows dll's. Sometimes it works, but a lot of the times it does not. When it works you get the full program and same as on Windows with no performance loss (or sometimes faster because of Linux). Most of the time however it's somewhere in-between. Program may not work right or something is just not the same.

---

### Post by 3Miro on 2011-04-04
> **roboticmehdi said:**
> why doesnt windows and gnu/linux operating systems do not support each others executables? i know that it is possible with emulators but they are much slower than original programs.

Linux and Windows have a different API, the way programs request resources from the kernel for example. With good documentation, it is possible to make it so that executable a compatible across. Look at FreeBSD and Linux, FreeBSD can run Linux executable (that is in fact the only way to get flash working on FreeBSD). While it is true that BSD kernel and Linux are more alike than different, there is still quite a bit of work to implement someone else's API.

MS is not interested in making software compatible with other people's software. You can look at MS Office for Mac and Windows and see plenty of issues between those and it is MS in both cases. Also, look at the wine project that is trying to create a layer of compatibility so that windows apps run under Linux, the hardest part of wine is to reverse engineer the Windows API (which is different from reverse engineering code). Nobody should have to do that as all API should be well documented, however, windows one can hardly have any worse documentation.

Basically: on GNU/Linux side, people are doing the best they can, while MS is no interested in making things any easier ... why would they. If Linux can flawlessly run Windows executables, this would be a huge blow to MS, and unfortunately they are not stupid enough to so directly empower their competitors.

On Windows side: MS really has nothing to gain from running Linux executables. They do, however, make improvements in other areas. For example, I was surprised to see that Windows 7 now supports natively NFS, which is the Unix Network File System protocol used on many servers.

---

### Post by roboticmehdi on 2011-04-04
> **3Miro said:**
> Linux and Windows have a different API, the way programs request resources from the kernel for example. With good documentation, it is possible to make it so that executable a compatible across. Look at FreeBSD and Linux, FreeBSD can run Linux executable (that is in fact the only way to get flash working on FreeBSD). While it is true that BSD kernel and Linux are more alike than different, there is still quite a bit of work to implement someone else's API.

MS is not interested in making software compatible with other people's software. You can look at MS Office for Mac and Windows and see plenty of issues between those and it is MS in both cases. Also, look at the wine project that is trying to create a layer of compatibility so that windows apps run under Linux, the hardest part of wine is to reverse engineer the Windows API (which is different from reverse engineering code). Nobody should have to do that as all API should be well documented, however, windows one can hardly have any worse documentation.

Basically: on GNU/Linux side, people are doing the best they can, while MS is no interested in making things any easier ... why would they. If Linux can flawlessly run Windows executables, this would be a huge blow to MS, and unfortunately they are not stupid enough to so directly empower their competitors.

On Windows side: MS really has nothing to gain from running Linux executables. They do, however, make improvements in other areas. For example, I was surprised to see that Windows 7 now supports natively NFS, which is the Unix Network File System protocol used on many servers.
I'm looking for a very fast 2D graphics library. What would you suggest? I want to run applications that open by clicking on them and they are going to be 2D  :D Dont want too complex functions, just create a windows and function like putpixel, draw line etc...

---

### Post by 3Miro on 2011-04-04
> **roboticmehdi said:**
> I'm looking for a very fast 2D graphics library. What would you suggest? I want to run applications that open by clicking on them and they are going to be 2D  :D Dont want too complex functions, just create a windows and function like putpixel, draw line etc...

Simple Display Library = SDL.

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

[http://www.sdltutorials.com/sdl-tutorial-tic-tac-toe/](http://www.sdltutorials.com/sdl-tutorial-tic-tac-toe/)

Don't install SLD stuff from those sited, just look at the code. To install SLD under Ubuntu, go to Synaptic Package Manager and look for libsdl1.2-dev, then install it.

---

### Post by roboticmehdi on 2011-04-04
> **3Miro said:**
> Simple Display Library = SDL.

[http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)

[http://www.sdltutorials.com/sdl-tutorial-tic-tac-toe/](http://www.sdltutorials.com/sdl-tutorial-tic-tac-toe/)

Don't install SLD stuff from those sited, just look at the code. To install SLD under Ubuntu, go to Synaptic Package Manager and look for libsdl1.2-dev, then install it.
It is not what i was looking for. It doesnt even have simple functions that i want like putpixel and drawline. The only functions i need are:

0. initiate fullscreen mode or windows at certain resolution
1. putting some text on screen
2. keyboard and mouse inputs
3. double buffer
4. putting pixel at certain point at certain color
5. drawing line between certain point at cerait color
6. timing

and thats all i need.

---

### Post by 3Miro on 2011-04-04
> **roboticmehdi said:**
> 
0. initiate fullscreen mode or windows at certain resolution
1. putting some text on screen
2. keyboard and mouse inputs
3. double buffer
4. putting pixel at certain point at certain color
5. drawing line between certain point at cerait color
6. timing


With SDL, I have done: 0, 2, 3, 4, 6. I have not tried the others, I think text is tricky due to fonts and such.

I have done all but double-buffer with QT (long time ago). QT, however, is not simple. It is the foundation of the KDE environment.

Gnome (Ubuntu) and most other Desktop Environments use GTK. GTK is also complex, I have not coded in it, but it is at least as functional as QT (although different).

Other than that, I have only heard of XUL, which is the basis for Firefox. I have no idea what XUL can and cannot do.

---

### Post by roboticmehdi on 2011-04-09
> **3Miro said:**
> With SDL, I have done: 0, 2, 3, 4, 6. I have not tried the others, I think text is tricky due to fonts and such.

I have done all but double-buffer with QT (long time ago). QT, however, is not simple. It is the foundation of the KDE environment.

Gnome (Ubuntu) and most other Desktop Environments use GTK. GTK is also complex, I have not coded in it, but it is at least as functional as QT (although different).

Other than that, I have only heard of XUL, which is the basis for Firefox. I have no idea what XUL can and cannot do.
I want to get started with opengl. Can someone help me with getting started? How to download, install and a 3D "hello world" for opengl (which is usually a rotating triangle or pyramid with different vertex colors) using gcc. I want screen to be fullscreen and either 640x400 or 1280x800(my screens default) resolution.

---

### Post by roboticmehdi on 2011-04-10
hey doesnt anybody know about opengl:(

---

