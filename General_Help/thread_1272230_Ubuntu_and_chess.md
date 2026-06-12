---
title: "Ubuntu and chess ??"
date: 2009-09-21
forum: General Help
---

### Post by steffenklug on 2009-09-21
Hi
I am getting really frustrated.
I try to install XBoard - error connecting to some gnuchess
I try to install gnuchess - not found
I try to install scid old versionn - did not work
I try to install scid version 4 - did not work
I installed sudo apt-get install build-essential => latest installed
I installed sudo apt-get install tk-dev tcl-dev => latest installed

What does it take to get a decent chess game going in Ubuntu??
The installed chess program can not store games
I tried to install Pychess and it looks exactly like the installed version, I do not know what the difference is.
Sorry for the venting

====
Well I have to go back to Windows

I tried to install Shredder Classic and it is supposed to be running in Java
(I have other installs like Jin that do run)
And nothing
no message no nothing
Here is my output;

:~/Documents/ShredderClassic3$ dir
Anleitung.pdf  images		META-INF		 sounds
books	       InstallJava	options			 UserManual.pdf
com	       LinShredder.jar	ShredderClassic3	 WM.pgn
engines        messages		ShredderClassic.desktop
:~/Documents/ShredderClassic3$ ShredderClassic3
bash: ShredderClassic3: command not found
:~/Documents/ShredderClassic3$ LinShredder.jar
bash: LinShredder.jar: command not found
:~/Documents/ShredderClassic3$ ShredderClassic3
bash: ShredderClassic3: command not found
:~/Documents/ShredderClassic3$ run ShredderClassic3
bash: run: command not found



scid msg:
configure: Makefile configuration program for Scid
    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.5
    Your operating system is: Linux 2.6.28-15-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.5 library: /usr/lib
    Location of Tk 8.5 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.

---

### Post by dias19 on 2009-11-25
Bump.

I have the exactly same problem with SCID.
 when i type ./configure it results

    Renaming "Makefile" to "Makefile.bak"
    Tcl/Tk version: 8.5
    Your operating system is: Linux 2.6.31-15-generic
    Location of "tcl.h": not found
    Location of "tk.h": not found
    Location of Tcl 8.5 library: /usr/lib
    Location of Tk 8.5 library: /usr/lib
    Location of X11 library: /usr/lib
    Checking if your system already has zlib installed: yes.
Not all settings could be determined!
The default Makefile was written.
You will need to edit it before you can compile Scid.


in the forum i read a reply about [that]("http://ubuntuforums.org/showthread.php?t=828556&page=2") where someone answered and his advice worked for the guy who created the thread (1+ year ago) but not for me.I still get the same result...

---

### Post by steven1664 on 2009-11-25
If you are using Ubuntu 9.10 just go to Applications>Ubuntu Software Center and under games there are a few choices for chess.  There is one 3D Chess game.  I am sure there are plenty available online just look for one here is a link for a few from sourceforge.net

[http://sourceforge.net/search/?type_of_search=soft&words=chess](http://sourceforge.net/search/?type_of_search=soft&words=chess)

---

### Post by StuartN on 2009-11-25
Yes, glChess is already installed and works well enough. xboard and scid are in the repositories - there are 51 chess-related packages.

---

### Post by dias19 on 2009-11-25
Any ideas about the SCID 4.0 installation.Because the old version (i think 3.6) is still in synaptic not the new one.The new one can only be installed if you compile the code.

---

### Post by Soul-Sing on 2009-11-25
please take a look at: [http://ubuntuforums.org/archive/index.php/t-1175019.html](http://ubuntuforums.org/archive/index.php/t-1175019.html)
mac4man howto works.

---

### Post by Johnsie on 2009-11-25
Boot into Windows, go to download.com and you will see hundreds of chess games that are dead easy to install. Hahaha, just kidding :-D

---

### Post by Soul-Sing on 2009-11-25
> **Johnsie said:**
> Boot into Windows, go to download.com and you will see hundreds of chess games that are dead easy to install. Hahaha, just kidding :-D

naah, ubuntu/linux comes with many outstanding chessgames. :)
almost the ultimate "linuxgame"....;) not only client-engine games also fisc-server (comp.) chessgames.

---

### Post by dias19 on 2009-11-25
thanks a lot leoquant i will seek to it.Actually its quite embarrassing because i was searching for almost an hour before posting and i didnt see that thread...

---

### Post by pwc on 2009-11-25
Hi, I just stumbled across this tread and think I can help. I've been using both Eboard and Scid with Ubuntu for eons, they are both great programs for study and play of chess. Both work great when set up correctly. I prefer Eboard over Xboard, it does much more. Eboard can be installed with Synaptic. There is no active development with Eboard(or Xboard). For the latest version of Scid, and well worth it, you must compile from binaries. Scid is being actively developed and continues to add more features and make improvements. 
It looks like steffenklug, the tread starter has dropped out. If so that's too bad, both these programs are top notch chess software. And dias19, it looks to me like your missing  Tcl-dev and Tk-dev, just check with Synaptic and install if missing. Then do the ./configure again. 

pwc

---

### Post by Soul-Sing on 2009-11-25
> Tcl-dev and Tk-dev, just check with Synaptic and install if missing.

hmm, thats what mc4man indeed suggests.....(post#6)
in jaunty these depend. are mentioned via synaptic: scid: preferences: depend.: Tcl-dev and Tk-dev (and other depend...) with an advice to install tex-chess.

---

### Post by Soul-Sing on 2009-11-26
By the way building scid from source needs:
1)
```
sudo apt-get install g++ tcl8.5 tcl8.5-dev tk8.5 tk8.5-dev libsnack2
libtk-img build-essential zlib1g-dev checkinstall
```
2) unpack the zip==>home
3) cd.....
4) execute in the terminal :
```
./configure
```
5)execute in the terminal :
```
sudo make install
```

---

### Post by cmcanulty on 2009-12-30
I am trying scid also, I loved it in windows. The scid homepage says it has engines to play against but I don't see this in the ubuntu version. I downloaded the linux scid but have no clue how to compile it. I really want a chess program that can be set to play at levels of from beg to advanced and I can't find any linux one that offers that. I am good at XP but a beginner at linux, thanks

---

### Post by bkratz on 2009-12-30
> **cmcanulty said:**
> I am trying scid also, I loved it in windows. The scid homepage says it has engines to play against but I don't see this in the ubuntu version. I downloaded the linux scid but have no clue how to compile it. I really want a chess program that can be set to play at levels of from beg to advanced and I can't find any linux one that offers that. I am good at XP but a beginner at linux, thanks

See post two of this mornings thread

[http://ubuntuforums.org/showthread.php?t=1366940&highlight=chess](http://ubuntuforums.org/showthread.php?t=1366940&highlight=chess)

---

### Post by gimcrack on 2009-12-30
brutalchess is my favorite chess board game. 3D & refection from the pieces off the marble glassy look chess board.

This is also in the repositories. If you have a good 3D video card to handle the 3D effects.

---

### Post by Hulky on 2010-08-18
To [leoquant]("http://ubuntuforums.org/member.php?u=155157")'s post:

I followed your instructions (thank you) and the terminal did its job without errors (I guess).

So where do I find the program now? How do I start it? I use desktop search - but there seems to be no application "scid".


When I am grown up I want to understand Linux :-)))

---

