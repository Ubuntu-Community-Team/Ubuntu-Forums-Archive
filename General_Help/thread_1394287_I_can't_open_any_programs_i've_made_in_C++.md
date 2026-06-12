---
title: "I can't open any programs i've made in C++?"
date: 2010-01-30
forum: General Help
---

### Post by 006ruler on 2010-01-30
O.K., so i'm prety much just a wanabe C++ programmer. When i was in Windows, i had absolutely no problem creating and running basic terminal C++ programs. I came to Ubuntu, and now I've got a big problem: I can't run any program that i make. I have tried making programs in Code::Blocks, CodeLight, MonoDevelop, and NetBeans. All 4 four are free IDE's from the ubuntu installer. I've created 4 programs, 1 on each, and they're all the EXACT same program. When i build it, they  build just fine and run. When i release and compile it so it becomes an .exe program, i can't open it. I find the thing, double click, and nothing happens. I rightclick and choose Run, and nothing happens. I made a basic Hello World program, and i couldn't even run that. Is there an extra thing im supposed to install to allow me to run .exe or something?

---

### Post by MelDJ on 2010-01-30
try compiling with gcc.
cd to the folder of your source code 
then 
```
gcc -o file.C -o output
```to run it ./output

---

### Post by jflaker on 2010-01-30
If you want to run a windows .exe, you need to install wine...

```
sudo apt-get install wine
```

---

### Post by 006ruler on 2010-01-30
what is gcc?

---

### Post by lisati on 2010-01-30
> **jflaker said:**
> If you want to run a windows .exe, you need to install wine...

```
sudo apt-get install wine
```
I think the OP is wanting to learn programming for Ubuntu
> **006ruler said:**
> what is gcc?
It's a C compiler. For C++, use the g++ compiler

If you have a C++ program, do something like this to compile it:
```
g++ test.cpp -o test
```
Then when you go to run it, type in:
```
./test
```
What the "./" at the start does is tell Ubuntu that the program you wish to run is in your current working directory. (replace "test" by whatever you call your program)

---

### Post by MelDJ on 2010-01-30
> **006ruler said:**
> what is gcc?

gnu c compiler. to compile c source code

lisati has given a more thorough explanation :)

---

### Post by jwbrase on 2010-01-30
> **006ruler said:**
> O.K., so i'm prety much just a wanabe C++ programmer. When i was in Windows, i had absolutely no problem creating and running basic terminal C++ programs. I came to Ubuntu, and now I've got a big problem: I can't run any program that i make. I have tried making programs in Code::Blocks, CodeLight, MonoDevelop, and NetBeans. All 4 four are free IDE's from the ubuntu installer. I've created 4 programs, 1 on each, and they're all the EXACT same program. When i build it, they  build just fine and run. When i release and compile it so it becomes an .exe program, i can't open it. I find the thing, double click, and nothing happens. I rightclick and choose Run, and nothing happens. I made a basic Hello World program, and i couldn't even run that. Is there an extra thing im supposed to install to allow me to run .exe or something?

If you're compiling them into Windows .exe format, then they will fail to run unless you have Wine installed (which allows you to run Windows programs). But I'm not sure if you're saying that because you're actually compiling them as .exe's or if you're calling Linux executables .exe's (they're a different format).

If you're compiling them as Linux executables, then there are a couple things you need to do that you don't seem to be doing: First, right click on the file and go to "Properties", and then click on the "Permissions" tab. Make sure "Allow executing file as program" is checked.

The next thing is that, unlike Windows, Linux does not automatically open up a terminal window for a terminal program if you double click on it in your file browser (I'm a bit annoyed with this myself and if anyone can tell me how to do that I'd be most obliged). You can however, do the following:

Go to Applications > Accesories > Terminal

Type:

```
cd /whatever/folder/the/program/is/in
./nameoftheprogram
```

As long as it's compiling correctly, the program should run. 

A bit of extra info, which is useful but not necessary:

If you want to be able to type "nameoftheprogram" instead of "./nameoftheprogram" to run it, you can go to "View -> Show Hidden Files" in Nautilus, and then go to /home/yourusername and open ".profile" with a text editor, and add ```
PATH=".:$PATH"
``` at the end of the file.

Alternatively you can open ".profile" by executing the following commands in the terminal:

```
cd ~
gedit .profile
```

"~" is shorthand for /home/yourusername.

---

### Post by 006ruler on 2010-01-30
YAY!! I can now run it. But really, no double click to run? Thats just stupid.
So now that i have that done...
If i were to have made a website at webs.com and i posted this file as a download file, would windows users be able to download this and run it like normal?

---

### Post by jwbrase on 2010-01-30
> **006ruler said:**
> YAY!! I can now run it. But really, no double click to run? Thats just stupid.
So now that i have that done...
If i were to have made a website at webs.com and i posted this file as a download file, would windows users be able to download this and run it like normal?

Well, when you double click it, it runs, but it doesn't open a terminal window, so it prints its output, but has nowhere to print to, so you don't see the output. I agree, it's stupid, but I haven't found a way to get it to automatically open a terminal window. Then again, as I recall, even though Windows automatically opens a terminal window, that window closes again as soon as the program is done, so for something like "Hello World", it's just going to open the window, put "Hello World" in the window, and then close the window again, probably before you have a chance to read "Hello World".

As for your question: No, windows users would not be able to run it unless you compiled it for Windows. The executable types are different. Linux executables won't run on Windows, and Windows executables won't run on Linux without Wine.

---

### Post by pbrane on 2010-01-30
Console programs will run when you double click them. And they write their output to stdout. You just can't see it. I'm not sure that it's a stupid idea to not open a terminal when double clicking a console app in GNU/Linux, it seems more stupid to open a terminal for half a second to run the program, you can't see the output that way either. If you want an IDE to learn C/C++ in try out Anjuta. It's in the repos too. I use gedit, emacs and gdb to write, debug and run apps I write. I would suggest that you learn to use gcc/g++ directly and also learn how to use the autoconf tools to create a configure script and makefile. You can generate all this stuff in Anjuta as well as various application types.

---

### Post by 006ruler on 2010-02-01
So i can now make a program and run it, but it only works in Ubuntu. I'm using ubuntu and most of the rest of the population are using Windows. Is there any way to create a program with the same text as the original program, but compile it in a way that lets Windows users open the program?
e.g. create a windows program that runs on Windows, but not on Ubuntu?


Also, im just wondering- how far can Wine go?
If i want to play Shin Megumi Tensei, a Windows mmo, could i use Wine to download and play it on Ubuntu?

---

### Post by howlingmadhowie on 2010-02-01
i'm playing dragon age on wine atm, and it runs fine.

being serious for a second, no of course windows executables don't run on glibc/linux/SOME_ARCHITECTURE, just like executables for mac/ppc don't run on the ps3. glibc on gnu systems and whatever_its_called on windows are not binary compatible, and the system calls even less so.

in fact this is not quite true. if you compile a java program and make a .jar of it and then rename the .jar to .exe, it should run on all computers which have a jvm installed (provided you execute it using the jvm). the same goes for python/perl/whatever. 

if i remember correctly, .exe under windows just means "execute me". it could be a binary file, it could be an installer archive, it could be a php-script---there's no way to know unless you look more closely. unix programmers could be equally braindead, but they usually use the suffix to tell you what sort of file it is (.sh is a shell script, for example).

good luck with C++.

---

### Post by Vaphell on 2010-02-01
c++ is not platform agnostic - it means your program needs to be compiled for a specific OS. If you want to support both linux and windows it means that you need to compile it 2 times. Most of the time you can reuse your code, but be warned that sometimes you may need to write platform specific chunks.

instead of testing your apps via wine, install virtualbox to run windows in virtual machine - you get native windows environment.

---

### Post by 006ruler on 2010-02-01
is dragon age a full mmo?
And im sorry to ask this, how would i specify for an mmo to install into wine?
<--- this guy has NO idea how to use wine. sorry, im very new to Ubuntu.

so just so i understand you correctly, there is no way to compile a C++ program into a non-ubuntu configuration? it will always compile into Ubuntu?

Sorry, i have no clue. I just know that even though Ubuntu is amazing, it doesn't advertise, so chances of finding others who use Ubuntu are dangerously slim.

---

### Post by howlingmadhowie on 2010-02-01
> **006ruler said:**
> is dragon age a full mmo?
And im sorry to ask this, how would i specify for an mmo to install into wine?
<--- this guy has NO idea how to use wine. sorry, im very new to Ubuntu.

so just so i understand you correctly, there is no way to compile a C++ program into a non-ubuntu configuration? it will always compile into Ubuntu?

Sorry, i have no clue. I just know that even though Ubuntu is amazing, it doesn't advertise, so chances of finding others who use Ubuntu are dangerously slim.

i'm afraid i don't know what an mmo is. dragon age is a multi-player rpg.

basically, yes you probably could compile C++ program text into a non-glibc/linux executable, but it would be a lot of work and would involve having lots of different versions of libraries on the computer and manually specifying linking behaviour and other stuff. in other words: no fun at all. 

if you want platform agnostic software with a gui, the best way to go is java bytecode atm. of course, what you compile to this byte code doesn't really bother the jvm, so you can write jruby, jython, scala, javafx, etc. code and then compile it down to java bytecode. so you don't have to write in the java language (which may come as a relief).

another possibility would be to use the modern qt libraries for C++, which are said to produce fairly platform independent code for guis, but i'm afraid i know very little about that.

---

### Post by 006ruler on 2010-02-01
Massive Multiplayer Online Role Playing Game

mmo is short for mmorpg
so can i install megaten?

---

### Post by Vaphell on 2010-02-01
if you plan on writing linux/win apps, you need windows either way to test your apps against it, don't count on wine to be 100% compatible. You take your working ubuntu code and compile it in windows to produce window specific executable file. If it works, you share it with win users.

i have found this regarding developing for windows on linux: [http://www.linuxjournal.com/article/7128](http://www.linuxjournal.com/article/7128)

---

### Post by howlingmadhowie on 2010-02-01
oh, and to install stuff into wine, first install wine using synaptic (though it may be worth using [this ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")to get the most recent version) and configure the wine environment a bit (set windows version and other stuff). then stick the disk in the drive, open it and right-click the autorun.exe and select "run with wine" (or whatever it is in english, or whatever your system language is). probably best to check [here]("http://appdb.winehq.org/") first, to see if it will run or not.

---

### Post by 006ruler on 2010-02-01
Megaten is a game that is downloaded from the internet, not from a disk. It's a free, 1.5 gig mmorpg. Heres the website:

[http://megaten.aeriagames.com/download](http://megaten.aeriagames.com/download)

How would i get that put into Wine?

---

### Post by Vaphell on 2010-02-01
when you have wine installed, double clicking may run it using wine, right click on exe should have 'open with wine' option or goto terminal window and run ```
wine name_of_the_file.exe
```. This should start the installer and from here install process is like in windows (though the setup window is uglier ;))

3rd option is probably the best when something doesn't work, as you get error message spewed out which very often is not visible when using gui.

---

### Post by 006ruler on 2010-02-02
PLEASE dont tell me i just ruined my system again...
I got wine, downloaded the installer, started it by right clicking it and selecting run with wine, and it started up just like it should. I then minimized it to continue with what i was doing, and OH CRAP!!! the little installer box just dissipeared. now when i open the .exe with wine, nothing happens. jack... squat. oops. What did i do?

---

### Post by 006ruler on 2010-02-02
OK, got it. the problem was that the thing i was trying to open was actually the unfinished installation of the game. oops.
time to wait for 4 hours. if it works, many profuse thanks to all of you, for both the original problem (unable to open an exe) and the waaaaaaaaayyyy wayward other topic, getting a windows game onto ubuntu.

---

