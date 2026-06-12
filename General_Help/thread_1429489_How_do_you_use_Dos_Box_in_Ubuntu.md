---
title: "How do you use Dos Box in Ubuntu?"
date: 2010-03-14
forum: General Help
---

### Post by szaemon on 2010-03-14
I just installed Dosbox from Synaptic and I downloaded a game from Abandonia... now what?

Where does Dos Box actually sit on the computer. I know I have to make a C:Drive and other stuff like that, but where do I do it?

Thanks any help offered.

---

### Post by vanadium on 2010-03-14
You start dosbox from the command line terminal, typing "dosbox".

The dosbox terminal appears. The command "intro" will get you started.

A dos command, for example, a game, can be directly run from the bash command line as:

dosbox /home/vanadium/.dosbox/PCMAN/PCMAN.EXE

With the option -exit, you will quit dosbox when exiting the program:

dosbox /home/vanadium/.dosbox/PCMAN/PCMAN.EXE -exit

---

### Post by szaemon on 2010-03-14
Thanks for offering some guidance Vanadium. Unfortunately, intro does not show how to install games.

I understand how to start the game in dosbox.What I don't get is how to put the game into someplace that dosbox can see it. The game is sitting in my download folder in a .zip file. Where do I unpack in so that dosbox can run it? I've tried extracting the game to different locations, but none of that seems to make any difference. When I type dir in dosbox, that game is not in the directory list.

Do you know what I mean?

Thanks Again for any help offered,
szaemon

---

### Post by bpalone on 2010-03-14
Maybe this will help.  I put it together for the kid a while back.

---

### Post by rCXer on 2010-03-14
It depends on the game you are trying to install :)

Your game folder should have a installer executable in it e.g. "setup.exe" or "install.exe"  Just copy it to your dosbox c folder and run the installer.

For example if your dosbox c folder is "/home/username/c/" and your game is in a folder called "game"
* Copy the "game" folder into "/home/username/c/".
* Start dosbox
* Mount and navigate to your game folder...
```

mount c "/home/username/c/"
c:
cd game

```
* Install it using the installer...
```
install.exe
```
or
```
setup.exe
```

Installing games is more complicated if it is divided into multiple disk images.

---

### Post by colobix on 2010-03-14
Sub question;
How do I enable arraw keys in dosbox?
Because when I play a game I have to use the mouse which can be frustrating from time to time.

---

### Post by rCXer on 2010-03-14
> **colobix said:**
> Sub question;
How do I enable arraw keys in dosbox?
Because when I play a game I have to use the mouse which can be frustrating from time to time.

This is a bug in dosbox 0.72, the one you probably have.  It is fixed in dosbox 0.73.  You can get the newer version from [PlayDeb](http://www.playdeb.net/updates/ubuntu/9.04/?q=dosbox) or the [karmic repositories](http://packages.ubuntu.com/karmic/dosbox).

---

### Post by colobix on 2010-03-14
> **rCXer said:**
> This is a bug in dosbox 0.72, the one you probably have.  It is fixed in dosbox 0.73.  You can get the newer version from [PlayDeb](http://www.playdeb.net/updates/ubuntu/9.04/?q=dosbox) or the [karmic repositories](http://packages.ubuntu.com/karmic/dosbox).
No I tried getdeb but it doesn't exists anymore. The website exists but not for apps downloading. And the 2nd link was website about something weird with lots of packages. I tried them all but none of them worked.
ONe of them asked for libstdc++6 which I already have installed.
I Have no idea what that thing was but that website looked kinda geeky and scary to be honest and I don't wanna install things frm it. Don't wanna mess up things you know.

---

### Post by szaemon on 2010-03-15
Thanks bpalone, the guide looks good. Unfortunately it starts explaining at a point 1 step beyond where I am. My game is still in the download folder in a .zip file and I don't know what to do with it from there.

> **rCXer said:**
> ~if your dosbox c folder is...

rCXer, thanks this is closer to what my trouble is. How and where do you make this C folder? How do I get Dosbox to see it? And how do you get the games inside of it?

I tried mount c ~/home. Dosbox tells me that the home directory does not exist. I dir and of course just the basic dos files are there. I have to make c and point dos towards it, but I don't know how to do that.

That's my trouble.

Please teach me.
Thanks szaemon

---

### Post by bpalone on 2010-03-15
Create a directory to hold your games, such as DOS_GAMES or OLD_GAMES.  I would keep it in /home to be easier to find.  Then extract your game into it.

Then as it says in the guide, mount c ~/dosfiles, replacing dosfiles with the directory you just created.

I think that will get you going.

---

### Post by jocko on 2010-03-15
> **szaemon said:**
> I tried mount c ~/home. Dosbox tells me that the home directory does not exist. I dir and of course just the basic dos files are there. I have to make c and point dos towards it, but I don't know how to do that.

"~/" is your home folder (/home/username), so "~/home" is a folder named "home" in your home directory (/home/username/home).
Try with a folder that actually exists.

---

### Post by rCXer on 2010-03-15
> **colobix said:**
> No I tried getdeb but it doesn't exists anymore. The website exists but not for apps downloading. And the 2nd link was website about something weird with lots of packages. I tried them all but none of them worked.
ONe of them asked for libstdc++6 which I already have installed.
I Have no idea what that thing was but that website looked kinda geeky and scary to be honest and I don't wanna install things frm it. Don't wanna mess up things you know.

Did you try [this one](http://www.playdeb.net/updates/ubuntu/9.04/?q=dosbox)?

---

### Post by szaemon on 2010-03-16
Thanks for the help folks. My error was that I wasn't changing to c: I was trying to stat the games at z: ... It should be a crime to be this ignorant of computers...

---

