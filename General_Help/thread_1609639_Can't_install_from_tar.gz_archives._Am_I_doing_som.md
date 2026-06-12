---
title: "Can't install from tar.gz archives. Am I doing something wrong?"
date: 2010-10-30
forum: General Help
---

### Post by ivarn on 2010-10-30
Hey. I can't install things from archives.
Here's what I do.
I extract the archive and cd the terminal into the folder I just extracted.
(it has the configure and makeinstall files).
I type  ./configure, but the terminal says: no such file or directory.
This is very strange, cause I have tried this many different times with different games or apps.
So, what am I doing wrong?

---

### Post by papibe on 2010-10-30
Not all tars use the configure command. Some use make, others autogen.sh, etc. It really depends on what you're downloading. Luckily, usually there's a README or similar.

If you told us more details, may be more people would offer advice.

What tar are you unpacking?
Where did you get it from?
What are the contents of the unpacked dir?

Regards.

---

### Post by ivarn on 2010-10-30
Thanks.
Ok, I downloaded a few games from softpedia.com, and I followed the installation instruction file that came in the archive.
I extracted the the archive to my desktop, opened up the folder, opened the terminal in the folder and followed the guide.
It said:
./cinfigure
make
sudo make install
clean install.

Since it couldn't find ./configure I tried all the other examples you mentioned above, but no use since the only installation files there are the makefile.am and configure.in.
I really wish there was a program out there I could use to auto install things like this.

---

### Post by oldos2er on 2010-10-30
Need more info; name of programs, links to same? Have you looked at README or INSTALL, or in a possible docs folder?

---

### Post by ivarn on 2010-10-31
OK, as I said, yes I check the install file and the readme file.
Here's the links:
Skunks: [http://sourceforge.net/projects/skunks/files/skunks/1.0.0/skunks-1.0.0.tar.gz/download](http://sourceforge.net/projects/skunks/files/skunks/1.0.0/skunks-1.0.0.tar.gz/download)
Python Farm Game: [http://linux.softpedia.com/dyn-postdownload.php?p=59760&t=0&i=1](http://linux.softpedia.com/dyn-postdownload.php?p=59760&t=0&i=1)
Also, here's where I found the games: [http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/](http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/)

---

### Post by gandaran on 2010-10-31
post the full error details from the terminal, this would be the best way to check whats wrong!
do you have 'build-essential' installed?

---

### Post by realzippy on 2010-10-31
Installing skunks,open terminal:

```
wget http://sourceforge.net/projects/skunks/files/skunks/1.0.0/skunks-1.0.0.tar.gz
tar -zxvf skunks-1.0.0.tar.gz
cd skunks-1.0.0/
./inst-ode
./comp

```

to run game:
```
cd skunks-1.0.0/
./skunks cars/car1 tracks/track1
```

---

### Post by realzippy on 2010-10-31
Install pyFarmGame:

```

sudo apt-get install python-pygame
wget http://dl.dropbox.com/u/1425867/Python/PyFarmGame-Rev12.tar.gz
tar -zxvf PyFarmGame-Rev12.tar.gz

```
to start game:
```
cd PyFarmGame/
python pyFarmGame.py
```

---

### Post by ivarn on 2010-10-31
OK thanks. I think they were successfully installed but I can't run any of them for some odd reason. It says; no such file or directory.
Also, where did you get this info? I couldn't find it in the readme file.
These things are so frustrating and the only thing I prefer in windows.
There must be an easier way to do this.
I mean, you can't expect people to through all this just to install a simple game.
Sorry I don't mean to complain or anything, I'm just pointing out the obvious.
EDIT: The skunk folder came up on the desktop but for some reason the command to open the game didn't work.
And why is it installed on my desktop. I wanna install it the normal way.

---

### Post by realzippy on 2010-10-31
*And why is it installed on my desktop*
When you open a terminal,you are usually in your user's home directory.
When you run the commands given in #7,the "skunks" folder will be created also in your user's home directory (/home/yourusername/skunks),not in your user's Desktop (/home/yourusername/Desktop/skunks),so I guess your Skunks folder on your Desktop is made by earlier install attempts .Delete it.
To start the game,you have to navigate in the game's folder (*cd skunks-1.0.0/* or for pyfarm: *cd PyFarmGame/*) to run the game,otherwise
you get your "*no such file or directory*".
You can create a starter on the desktop so the game starts in 1 click.

*where did you get this info?*
The README file in the skunks folder:

1. Installation
ODE must be installed first; version 0.11.1 (which I used) is in
the directory "ODE". To install it, type:
**./inst-ode**
ODE will be installed in "ODE/local". Then type:
**./comp**

*I mean, you can't expect people to through all this just to install a simple game.*
Since those games are not pretty mainstream,nobody felt the need to write a short script that does the installation I guess;common,3 short commands   ;-) !
the Farmer game itself is a pythonscript you just have to run.
No "real" install,whatever this is.

---

### Post by ivarn on 2010-10-31
> **realzippy said:**
> *And why is it installed on my desktop*
When you open a terminal,you are usually in your user's home directory.
When you run the commands given in #7,the "skunks" folder will be created also in your user's home directory (/home/yourusername/skunks),not in your user's Desktop (/home/yourusername/Desktop/skunks),so I guess your Skunks folder on your Desktop is made by earlier install attempts .Delete it.
To start the game,you have to navigate in the game's folder (*cd skunks-1.0.0/* or for pyfarm: *cd PyFarmGame/*) to run the game,otherwise
you get your "*no such file or directory*".
You can create a starter on the desktop so the game starts in 1 click.

*where did you get this info?*
The README file in the skunks folder:

1. Installation
ODE must be installed first; version 0.11.1 (which I used) is in
the directory "ODE". To install it, type:
**./inst-ode**
ODE will be installed in "ODE/local". Then type:
**./comp**

*I mean, you can't expect people to through all this just to install a simple game.*
Since those games are not pretty mainstream,nobody felt the need to write a short script that does the installation I guess;common,3 short commands   ;-) !
the Farmer game itself is a pythonscript you just have to run.
No "real" install,whatever this is.

Ok? but I asked how I can install the games and when I followed the guides I just got a new folder on my desktop with the game files, so Im basically back to scratch.
But isn't there any programs I can use to automatically install the files where they belong on the system? I mean I know linux is just in its beginner phase but I bet 100s of people are dealing with these problems all the time, so why this complicated system that only experts, geeks and nerds can handle?
Linux is still better then windows on most things but when you have to be a geek to install a game... Sorry, I'm just frustrated over this.
What ubuntu and debian needs is a program that will automatically convert an archive file into a .deb installation file. Because installation is something everybody should be able to do quick and simple.

---

### Post by realzippy on 2010-10-31
**Can I have cookie**?
is harder to say (type) than
**./inst-ode**
,isn't it?And you have not to be a nerd,expert or geek to get cookies.
So?
Those 2 games just not have made their way into the ubuntu repositories...
BTW,why not installing a few games from the so called
"Software Center" 
which is made to make things easy for non-geeks.This is the program
you suggest ;-) 

When you run the commands exactly (you can copy&paste,"tab" for autocomplete)
it should not be possible that a folder is created on the Desktop,
unless your username is *Desktop*...

---

### Post by ivarn on 2010-10-31
True, but I couldn't find those games in synaptic so it was my only choice.
But the games are under the linux category which means they should work on ubuntu, right?
That is why I wish there was an easier way to install the games then from the terminal.
And no maybe you don't need to be an expert or a nerd to install these things but it's hard enough and it takes more time then what it would take in windows. And that's what I mean. If linux wants to beat windows, they MUST find an easier way.
I know there are many people every day getting frustrated over the way these archives and all works. You need to place one file there and one file there and do everything manually which takes forever if there's not an configure file included.
Linux needs a program that can sort out the files where they belong. Icons, execute files,  help files etc where they belong and at the same time mark the program as a package so you will find it in the synaptic program.
Now, this is possible to do if you have like forever of time, but most people don't, and things that will take forever will always end up being frustrating.
This is a serious issue Linux needs to work with.

---

### Post by gandaran on 2010-11-01
> **ivarn said:**
> True, but I couldn't find those games in synaptic so it was my only choice.
But the games are under the linux category which means they should work on ubuntu, right?
That is why I wish there was an easier way to install the games then from the terminal.
And no maybe you don't need to be an expert or a nerd to install these things but it's hard enough and it takes more time then what it would take in windows. And that's what I mean. If linux wants to beat windows, they MUST find an easier way.
I know there are many people every day getting frustrated over the way these archives and all works. You need to place one file there and one file there and do everything manually which takes forever if there's not an configure file included.
Linux needs a program that can sort out the files where they belong. Icons, execute files,  help files etc where they belong and at the same time mark the program as a package so you will find it in the synaptic program.
Now, this is possible to do if you have like forever of time, but most people don't, and things that will take forever will always end up being frustrating.
This is a serious issue Linux needs to work with.
you should complain to the games developer and not linux, linux is a fully developed moderm OS and as you can see it works in many ways to fit everyones needs!
about that games you can install them any where you like in root file system or your user directory, move them and create a launcher icon in desktop or the applications menu, the whole thing is easy as long as you know what you are doing, learn how to use linux!
also if you want them packed in an installer get a .deb package builder and make you own .deb packages ready to install in one click, this is exactly what I do when I cant find a .deb package for the a application I want to install, the whole process is easy and no you don't have to be a geek to do all this.

---

### Post by ivarn on 2010-11-01
Dude, I'm saying this because it's true and I want linux to beat windows big time.
In windows, if a program doesn't have an installation file it's as easy as cake to place the program where it belongs anyway. Simply unzip it and move the folder to c:/program files and make a shortcut, and that's it. As I said; there are so many extra steps in linux because first of all you need gksudo to write to the system folders, and files are places in different locations.
In linux, this takes forever and most people will give up half way through.
That's why I'm saying Linux needs a program that will automatically sort the files where they belong. I'm not complaining just to be a **** here.
Ok, how hard is it for linux to make a program or for someone to make a script like that.
I mean, the files have their main directions. Icons in the icon folder, execute files in the bin folder and so on. So yea. 
The point here is to make it as user friendly as possible and make people wanna use linux instead of windows, right?
And no, complaining to all the game/app developers about this will make you sound like an idiot and you will end up wasting your time complaining anyway.
You see my point here.
EDIT: As you can see, I know how to do it but I'm talking about most people, everyday people, noobs and people with a busy schedule.
A process that takes 10 sec or less in windows shouldn't take longer time with linux.

---

### Post by matt_symes on 2010-11-01
Hi

> In windows, if a program doesn't have an installation file it's as easy  as cake to place the program where it belongs anyway. Simply unzip it  and move the folder to c:/program files and make a shortcut, and that's  it. As I said; there are so many extra steps in linux because first of  all you need gksudo to write to the system folders, and files are places  in different locations.

gksodo is one reason why linux's security model is much better than windows.

The steps are basically the same though to install or build software on the two platforms.
I think you are just more familiar with windows than linux at the moment and that is fair enough. You will become more familiar with time.
Ubuntu is incredibly easy to use if you stick to the GUI and use synaptic. 

Kind regards

---

### Post by realzippy on 2010-11-01
@ivarn

..as you noticed,synaptic and software-center **exist**.*Skunks*
and *pyfarm* (watching 1h a carrot icon growing..) will never make it in the repos.
If tons of games installable per 1 click in the gamesection of software-center is not enough for you and you prefer those alpha/beta games
you have to learn how to [unpack a .tar]("https://help.ubuntu.com/community/FileCompression") file in a folder you create/choose and how to start a simple python script(in the case of "pyfarmer").



WISH A MOD WOULD JUMP IN AND CLOSE THIS.
Original question is answered,thread is going nowhere.

---

### Post by CharlesA on 2010-11-01
Leave the Windows vs Linux argument out of it. It has nothing to do with the topic.

From the looks of it, the OP needs to learn a bit more about unpacking tarballs and running software from them.

The archive manager makes it dead simple to open tarballs and extract their contents to a specified folder.

If this thread goes any more off topic it will be closed.

---

### Post by ivarn on 2010-11-01
How was it off topic?
I couldn't find the games in the software center so I had to install them the hard way and I asked for that, can still not install them.
So it's never been off-topic.
@matt_symes, I agree. gksudo makes it secure, and I'm still used to windows so that's probably why this frustrates me as much as it does.
But I still think we need a program that will automatically install .tar.gz archives as packages. So, ok how do I install the gz files.
THe thing is, these archives did have the makefile, configure file and install instructions, but they didn't work. As I said, the message I get in the terminal is No such file or directory. So what do I do?
You see now? the thread was never off topic. We really need a better way then the terminal to install things from archives.

---

### Post by CharlesA on 2010-11-01
The rant about installing software in Windows vs Linux was off topic.

Normally, when running a makefile or configure or whatever and it fails, it'll tell you what it failed on - not just exit with an error of "no such file or directory."

It helps to post the exact error message you get.

---

### Post by ivarn on 2010-11-01
ok as I said, when I extract the archive, I open the terminal and points it to the folder.
Then I type in ./configure (no such file or dir) then I tried make (same), and nothing seem to work. no such file or directory is the only error I get.
And I also tried with sudo but no luck.

---

### Post by CharlesA on 2010-11-01
can you copy paste the terminal output including the commands you used please.

Place them in [noparse]```

```[/noparse] tags please.

---

### Post by realzippy on 2010-11-01
[COLOR="Red"]Please look again at post #7 and #8[/COLOR]....[COLOR="Red"]No "./configure",no "make"[/COLOR]  (there are no makefiles!!!),[COLOR="Red"]just run those commands,line by line,do not extract anything before!!![/COLOR]and you can play the games,installed to your user's homefolder.

---

### Post by ivarn on 2010-11-01
You guys, please don't get mad but I think there was something wrong with the files or something in that archive. I downloaded another game and it worked.
I mean, I did the right steps but maybe the configure file was corrupted or something.

So ok, I need to place the files in the folders manually.
So where exactly do I move the files to?

Ok execute files /bin
icon files in /icons
other files in /share/programname or /local/programname ?
Something like that?
Please explain or guide me to a place where I can find it.
Thanks.

---

### Post by CharlesA on 2010-11-01
You haven't posted the output of whatever command you were running. That would help greatly.

Just copy/paste it from the terminal.

---

### Post by ivarn on 2010-11-01
ok I have deleted the archive but what I did was.
Extracted the archive and it had the configure and makefile.
So I opened the terminal in that folder (cd /home/ivarn/Desktop/skunks)
./configure - I got "no such file or directory".
make - I got "no makefile found" (I guess).

The weird thing is that these file were in the folder so "no such file" ???
Well, I tried a few other games and they worked.

---

### Post by realzippy on 2010-11-01
> **ivarn said:**
> ok I have deleted the archive but what I did was.
Extracted the archive and it had the configure and makefile.
So I opened the terminal in that folder (cd /home/ivarn/Desktop/skunks)
./configure - I got "no such file or directory".
make - I got "no makefile found" (I guess).

The weird thing is that these file were in the folder so "no such file" ???
Well, I tried a few other games and they worked.

Dude,I marked the important things in post [#23]("http://ubuntuforums.org/showpost.php?p=10057227&postcount=23") [COLOR="Red"]red[/COLOR] for you.

---

### Post by ivarn on 2010-11-01
OK so back to my question from post #[**24**]("http://ubuntuforums.org/showpost.php?p=10057317&postcount=24").
Where do I move the files to?
Edit: ok this is how I think it is so is this the right ?
Execute files = /bin
Icon files = /share/icons
program files = /lib
Help files = /share

---

### Post by rhoparkour on 2010-11-01
Hey man, I want to help you, and please don't think I'm being hostile or anything, please read this.

Sorry for the all-caps, but I think this should be said, I'm not yelling, by the way, I just want to really emphasize:

FIRST OFF: BEFORE INSTALLING STUFF YOU JUST DOWNLOADED, READ AND UNDERSTAND THE README THAT COMES WITH YOUR PROGRAM, ANY SANE PERSON WILL INCLUDE A README FILE. README FILES ARE VERY IMPORTANT.

Second: When asking for help, it is always a good idea to post the exact output of what you did, as in this example...

```

rho@Schwarzschild:~$ ./configure
bash: ./configure: No such file or directory

```

By the way, I think this was what happened to you.

People want to put themselves in your shoes, so show them exactly what you see by posting code or even screenshots.

I'm sure this has been said countless times before, but it's important to know and will help to get your questions answered.

As for your questions, I don't think you need to move any files, since make and make install should compile and link any files needed for the game to run, this is what make is for! The reason you don't need to move files is that pretty much all the program needs to run is inside the tarball, so it can run in it's own directory if you don't mind not having shortcuts.

One tip, I like games too, but sometimes I don't want to install them because they are still in development, so I'll just compile (run ./configure and make) and make an alias so that I run them with a single command.

Please let me know if that was any help. Good luck.

---

### Post by ivarn on 2010-11-01
Thanks. I actually gave all the info of what I did and everything (after a few posts but still).
Off course it's important to give as much info as you can.
So the case was thing. I downloaded an archive with a makefile, conf file and a readme file. I followed the instructions but the terminal said; no such file or directory. Which is odd since the files are in the archive I just downloaded.
Also, this is info I already knew but I wasn't sure if I did something wrong since I got that message. But after I downloaded a few other games and installed them, I realized that there was probably something wrong with the files in the archive.
So that archive was pretty much useless.
So I followed the instructions from post #7 or what it was and downloaded the game from that command. This downloaded a folder to my desktop but as I said I still have to place the files in the correct folders in the system and I mentioned above.
And yes I agree with you that games with no good instructions and such aren't a good idea to install, but these games were from a famous download page (softpedia.com), so yea.
And so that is why I want to know where the files belong in the system because I have to install it manually. Also, I gave up this game since the files obviously doesn't work or anything but it's still a good thing to know for the future.

---

### Post by realzippy on 2010-11-01
[I]So that archive was pretty much useless.
So I followed the instructions from post #7 or what it was and downloaded the game from that command. This downloaded a folder to my desktop but....[/I]


```
wget http://sourceforge.net/projects/skunks/files/skunks/1.0.0/skunks-1.0.0.tar.gz
tar -zxvf skunks-1.0.0.tar.gz
cd skunks-1.0.0/
./inst-ode
./comp
```

,,does **not download to your Desktop**,when you open a terminal and type this,you are at your user's directory.Did you run
cd Desktop  ???

---

### Post by ivarn on 2010-11-01
I didn't run anything, just pasted in the command.
Then the command stopped at ./comp (after the ODE installation process), so I clicked enter. But seriously. I've been working with this for more then a day now so even if the game will work for me one day I will hate it because it took me forever to install.
I HATE COMPLICATED THINGS.
ANyway, thanx for all the help, guys.
I still wanna know where to sort the files as I have asked for over 9 000 times now.
So if you wanna help me out, please. Thanks again :)

---

### Post by realzippy on 2010-11-01
rhopakour gave you the answer:
*As for your questions, I don't think you need to move any files, since make and make install should compile and link any files needed for the game to run, this is what make is for! The reason you don't need to move files is that pretty much all the program needs to run is inside the tarball, so it can run in it's own directory if you don't mind not having shortcuts.*


............................

*Then the command stopped at ./comp (after the ODE installation process), so I clicked enter*
It can take a while.When it **stops**,there will be an error ?


...........................

what about [chromium]("http://www.reptilelabour.com/software/chromium/") b.s.u. (example for good linux integration and fun)?

You can download it as .tar and compile it yourself (for training)...
and have the game in 1 directory (you can move it)
or simply type:

```
sudo apt-get install chromium-bsu
```

and you get it as you want;integrated,all files where they belong,start in Apps/games/chromium.You can do both also..

---

### Post by ivarn on 2010-11-01
Yea but we've been over this. the ./configure and make method didn't work in this case. also what if a game doesn't have a makefile nor a configure file?
Then I am forced to move them. But ok, i'm to tired for this shït.

---

### Post by rhoparkour on 2010-11-02
I see the problem, I have a few thoughts. Don't give up man, it's not complicated, just unfamiliar territory, if I get the game running, I'll post how.

---

### Post by rhoparkour on 2010-11-02
My advice would be to forget it for now man, I would say this game is either in early development OR the make files are badly made (I took a look at inst-ode, configure and make files for ode, there are a lot of unresolved dependencies and it would be time consuming to know what I am missing to compile, let alone what YOU are missing, since I have no access to your computer).

Unresolved dependencies are a pain to get through and I recommend waiting a bit to run  this game, until it is a bit more polished. The README is also not very illuminating, with no mention of what libraries you might need to compile or even common compile problems.

Just don't get discouraged man. So you ran into a bad program to compile from source, some bad luck. No worries, just don't think it's complicated, it's just not something you're used to.

With luck and a little work, you'll find this simple and you will be able to figure out this kind of thing; but the moment you predispose your mind into believing this is hard, you make the learning process into a painful and bad experience overall. It's all about attitude.

Good luck with future builds, just keep at it and don't bang your head against the wall!

P.S. For future builds: moving files around is probably not going to solve problems of this sort, as I said before, a well written and packaged program should have all it needs to run inside the tarball it came in, just running make should compile everything and get you going. If it doesn't have everything you need, the README file should mention it, these are called dependencies and it is usually not hard to solve this problem if the program has good install instructions.

Running make install will create and move files like you wanted to, but the reason this is left to make install it's that, manually, it is a lengthy process no sane person should ever endure.

P.P.S. Try building FreedroidRPG from source, it's easy and a great game. You should also look into Tremulous, a gem of open source gaming. Sourceforge.com is a great site to dig around for open source stuff as well.

---

### Post by realzippy on 2010-11-02
@rhoparkour
You have not read the thread,have you?
What happens when installing the game like the readme says (see post #7,or #31 aso)?
Here it works without problems.

---

### Post by matei_v on 2010-11-02
The game is in early development and I don't have much time to develop it, but Open Dynamics Engine isn't. The README file says this: > The program uses the "SDL" library, available at [www.libsdl.org](www.libsdl.org), which is distributed under the GNU LGPL license,version 2 ([www.gnu.org](www.gnu.org)) and the "Open Dynamics Engine" (ODE), available at [www.ode.org](www.ode.org).  ... so the only "dependencies" are SDL ( [http://www.libsdl.org](http://www.libsdl.org) ) and ODE ( [http://www.ode.org](http://www.ode.org) . ODE is included in the archive (I din't change anything in it) for convenience and SDL is included in almost all distributions (I think). What I wanted was a simple 3D game that runs on a Pentium 2 without a 3D accelerator and has as few dependencies as possible. There is no makefile because the program is small and doesn't need one and everything (including ODE) "installs" in one directory because I like to keep things nicely ordered. This way, it's also easy to remove.  For Ubuntu users, I would like to point out the following phrase from README: > **An executable file already compiled for Linux, Pentium II processor and 640x480 resolution, with gcc 4.1.1, is available. If you want to try it, skip the installation and go straight to 2.**  The executable is statically linked with ODE and SDL (runtime) should be included even in Ubuntu. Also, some basic knowledge about navigating through directories is needed, but it shouldn't be hard, because the command "cd" works the same as in DOS/Window$.

---

### Post by ivarn on 2010-11-02
Thank you so much guys.
I gonna close this thread now.
@[rhoparkour]("http://ubuntuforums.org/member.php?u=1116446") you're absolutely right.
The game doesn't work and I Have no idea why they upload **** that doesn't work.

---

### Post by matei_v on 2010-11-03
I understand that you're new to GNU/Linux and that you sometimes get frustrated; so was I at the beginning. However, I tried a version of Ubuntu once and noticed that none of the tools needed to compile programs from source was installed by default. Even gcc, which was included on the CD, had to be installed manually (I even had to create a symlink to it) ... which reminds me: check whether you have the file **/usr/bin/g++**; if it's missing, type this:  >  ln -s `find /usr/bin -name 'g++*'` /usr/bin/g++   I tested the game on Fedora and FreeBSD and it worked without any problem. I don't have time to test it on every version of every distribution. If anyone encountered problems during compilation, some error messages would be more useful.

---

### Post by rhoparkour on 2010-11-03
As a follow-up on what matei_v said, reading the output of your installation attempts usually tells you what you are missing to compile the thing. Nevertheless, in my case I was missing too much stuff to even bother, and I've compiled my share of packages...

---

### Post by realzippy on 2010-11-03
> **rhoparkour said:**
> As a follow-up on what matei_v said, reading the output of your installation attempts usually tells you what you are missing to compile the thing. Nevertheless, in my case I was missing too much stuff to even bother, and I've compiled my share of packages...


That has been said x times in this thread.
*You* not seem to have read it and *Ivarn* either is
obstinate,unable to read or just a
troll.

---

### Post by matei_v on 2010-11-03
Enough already, I just installed Ubuntu 5.04 (this is what I have), installed gcc manually and created 2 symlinks: > ln -s /usr/bin/gcc-3.3 /usr/bin/gcc > ln -s /usr/bin/g++-3.3 /usr/bin/g++ Then I installed SDL-devel and SDL (I had some *.rpm packages for SuSE, which worked) and encountered absolutely no problems when I compiled the game. Any questions? (In my opinion, it's better than Stunts played in Dosbox, but it's just a matter of personal taste).

---

### Post by ivarn on 2010-11-04
> **realzippy said:**
> That has been said x times in this thread.
*You* not seem to have read it and *Ivarn* either is
obstinate,unable to read or just a
troll.
It has been said 10 times yes but as I have been saying, that wasn't the case.
The files in the archive was obviously broken since installing programs from source works all the time, but not this one time. I have no idea why the terminal couldn't read the ./configure file nor the makefile.
I have said this like 10 times and I can't find a solution other then just give up the whole thing as I said earlier (on the last page).

---

### Post by mc4man on 2010-11-04
> I have no idea why the terminal couldn't read the ./configure file nor the makefile.
There is no configure, make or even 'install' on skunks - only on ode and that can be handled by the included script - inst-ode
(or you can configure, make and install ode manually if you so choose.

If you follow the process from start to finish the only thing that happens as far as skunks is the included binary - 'skunks' is replaced by the compiled one. (that's what comp does, compiles a binary

skunks is not 'installed' - it is run from the skunks-1.0.0 dir.

All this is made very clear in the readme, inc some changes one may wish to make to comp before running.

Or just run skunks as supplied - nothing to do at all

Ex.
```
mkdir skunk && cd skunk && \
wget http://sourceforge.net/projects/skunks/files/skunks/1.0.0/skunks-1.0.0.tar.gz
```
```
tar -zxvf skunks-1.0.0.tar.gz && \
cd skunks-1.0.0
```

At this point you just run skunks from the above prompt w/ as an example
```
./skunks cars/car1 tracks/track1
```
Or look in readme for other car/ track/ combos

Or from same prompt  run the ode script to configure make and install ode
```
./inst-ode
```

followed by this which compiles skunks and r**eplaces the supplied binary with a new one**. (again the readme suggests some changes before running, both to comp and some src/ files
```
./comp
```

At this point, -  your done - the previous binary, 'skunks', will have been re-compiled and replaced with a new one which is run from the prompt like above.

---

