---
title: "Terminal: What else can I do with it?"
date: 2009-09-02
forum: General Help
---

### Post by SacValleyDweller on 2009-09-02
I've been walked through a few sudo comands in terminal, such as sudo apt-get install (if I recall that correctly), and changing the directory.

Im now want to know, in order to increase my self-sufficiency in Ubuntu and not have to rely solely on the friend that introduced me to the OS, what sort of things I can do in terminal? What are the most powerful/useful comands? What is the proper syntax to use these comands?

---

### Post by nothingspecial on 2009-09-02
Loads of stuff.

Try installing a few terminal apps and reading the man pages. A good way of doing this is using dvtm

```
sudo apt-get install dvtm
```

Then run it ```
dvtm
```

Press Ctrl+G then C. This will split your terminal into 2. Type ```
man dvtm
``` in the other window then have a play with dvtm with the instructions infront of you.

Some others to try

ffmpeg
cmus
rtorrent
feh
elinks

Then of course there is [[COLOR="Magenta"]bash scripting[/COLOR]]("http://tldp.org/LDP/abs/html/")

---

### Post by stumbleUpon on 2009-09-02
Using the terminal you can do anything in linux --- right from screwing up your system to making it run extremely well.

For a start look at chapter 5 in this book (Free PDF)

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Also see this thread to be warned of dangerous commands

[http://ubuntuforums.org/announcement.php?f=169](http://ubuntuforums.org/announcement.php?f=169)

If you dont know what a command is for just do
```
man command_name 
```
to get a summary of the command.

Google around to find more about using the terminal.

---

### Post by P4man on 2009-09-02
editing text (and configuration) files (nano)
mounting and umounting  drives (mount, umount)
viewing your hardware (lspci, lsusb)
changing permissions and ownership of files and folders (chmod, chown)
loading/unloading kernel modules (modprobe)
browse the internet with w3m lol !!

---

### Post by kerry_s on 2009-09-02
> **SacValleyDweller said:**
> I've been walked through a few sudo comands in terminal, such as sudo apt-get install (if I recall that correctly), and changing the directory.

Im now want to know, in order to increase my self-sufficiency in Ubuntu and not have to rely solely on the friend that introduced me to the OS, what sort of things I can do in terminal? What are the most powerful/useful comands? What is the proper syntax to use these comands?

you can do everything in the terminal, look around, edit files, even go on the web, check your mail, listen to music, etc...

to make life in the terminal easy, create "alias's" in your ~/.bashrc file.
that way you don't have to type out the whole command.

i just use a few basic 1's, here are the apt-get 1's:
```

alias u='sudo apt-get update;sudo apt-get upgrade'
alias s='apt-cache search'
alias i='sudo apt-get install --no-install-recommends'
alias r='sudo apt-get purge'
alias ?='dpkg -l | grep'
alias c='sudo apt-get clean'

```

for example, to update & upgrade i just press "u" & hit "enter" type my password & let it do its thing.

---

### Post by kjohri on 2009-09-02
Text-based command line interface is the fundamental interface to your system. A lot of Linux commands have many options; these are best given from the command line. To improve your comfort level with command line, try the sample shell programs and other commands given in the classic book, "The Unix Programming Environment" by Kernighan and Pike.

---

### Post by marshag63 on 2009-09-02
If you want a way to try some CLI things out without messing up your system, consider the INX live CD - an all CLI distro with tutorials.  Its a fantastic learning tool!  :)

Main Page:
[http://inx.maincontent.net/](http://inx.maincontent.net/)

Video Screencast:
[http://inx.maincontent.net/video.html](http://inx.maincontent.net/video.html)

MarshaG

---

### Post by wojox on 2009-09-02
What can't you do with it?

[http://www.debianhelp.co.uk/commands.htm](http://www.debianhelp.co.uk/commands.htm)

---

### Post by ecmatter on 2009-09-02
Command line file manager:

```

sudo apt-get install mc

```

Command line cd-ripper

```

sudo apt-get install cdparanoia

```

Do just about anything to an audio file:

```

sudo apt-get install sox

```

The alias I use the most:

```

alias ic='info coreutils'

```

---

### Post by exutable on 2009-09-02
This is basically like asking what can I do with my life?  Anything you want! Sure if you want to drive you might need to get a car first but you can do it!

---

### Post by philinux on 2009-09-02
> **SacValleyDweller said:**
> I've been walked through a few sudo comands in terminal, such as sudo apt-get install (if I recall that correctly), and changing the directory.

Im now want to know, in order to increase my self-sufficiency in Ubuntu and not have to rely solely on the friend that introduced me to the OS, what sort of things I can do in terminal? What are the most powerful/useful comands? What is the proper syntax to use these comands?

System>Help and Support>Scroll down to Advanced topics.

If you want to know more about a command use **man command** in the help search box

---

### Post by t0p on 2009-09-02
Although you can do file operations (copying, deleting, moving etc) in the graphic interface, and that might be the way you're used to doing things, it is often much faster and efficient to use the terminal.

For instance: Imagine you've downloaded a variety of files to your Desktop - videos (with suffix .mp4), music (suffix .mp3), textfiles, images - all sorts of stuff.  Now, you want to move all the mp3s to your Music folder.  But dragging and dropping/cutting and pasting all these files would take ages.  Well, one simple terminal command will do it all for you.

```
mv Desktop/*.mp3 Music/
```

This is just one very simple example.  You can do much more complex operations, using commands like *grep* and *sed* combined with *regular expressions* to search for certain files, strings, variables and more. Then you can put a series of commands into a textfile - a *shell script* - and automate all kinds of tasks. It's certainly not necessary to learn how to use these commands, but it's definitely useful.  I recommend learning as much as you can about the command line.  Google for "bash shell" and "bash commands".  It's very worthwhile.

---

### Post by winotree on 2009-09-02
I don't think I'm duplicating effort by posting this [http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)
It's a good, if not thorough breakdown of **apt** -- and one of my original bookmarks from (almost) two years ago when I began with Linux.   ;)

---

### Post by Esthellin on 2009-09-11
Command line vlc
nvlc or vlc -I ncurses

Instant messaging client
finch

Internet
w3m

And being able to start all other programs that I need without needing the pesky gnome-panel :D

---

### Post by ankspo71 on 2009-09-11
Hi, the first thing that amazed me was the terminal can be used to surf the web.

```
w3m www.google.com
```

That will open up the google homepage in the terminal. This could be useful if your browser breaks or something. [edit:] Woops, I see this was just mentioned.

Here is a list of basic Debian type commands with man pages.
[http://www.debianadmin.com/basic-linux-commands-with-man-pages.html](http://www.debianadmin.com/basic-linux-commands-with-man-pages.html)
I don't think this one link has been mentioned yet.

Also, as someone told me this week, if you want to learn more about a command, type "man <command>" in your terminal. For example:
```
man apt-get
```

You can also search for packages to download for apt-get and aptitude.
```
aptitude search firefox
```
(aptitude is an alternative to apt-get).

James

---

