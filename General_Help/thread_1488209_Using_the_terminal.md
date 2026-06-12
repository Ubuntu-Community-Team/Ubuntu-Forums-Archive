---
title: "Using the terminal"
date: 2010-05-19
forum: General Help
---

### Post by pr0t3g3 on 2010-05-19
What command can I use to start a program in the terminal? 
What command is appropriate for applying patches to that or other programs?
  
Example: what command is appropriate to applying a 3.5 version patch to the 3.0 version of firefox


Edit: What are some useful commands for the terminal?
Are there any extremely helpful commands that you can think of off hand that are a big help?

---

### Post by ubunterooster on 2010-05-19
What command can I use to start a program in the terminal?[COLOR=Blue]Usually you type the name of the program: epiphany-browser, firefox, thunderbird, exaile....
[/COLOR]

---

### Post by pr0t3g3 on 2010-05-19
> **ubunterooster said:**
> What command can I use to start a program in the terminal?[COLOR=Blue]Usually you type the name of the program: epiphany-browser, firefox, thunderbird, exaile....
[/COLOR]
Very cute but it doesnt launch the program itself ;D!

---

### Post by ubudog on 2010-05-19
So if you type "firefox" into a blank terminal, it won't start?

---

### Post by Aped on 2010-05-19
Is this a remote session or are you physically at your computer? 

Physically at computer: Typing 'firefox' (or 'firefox&' to place the process in the background) should do the trick. 

Remote connection via SSH: Add the -X flag to your command to allow GUI use. ex: `ssh -X <ip/servername>`

To update: Assuming it's in the repositories (pretty much guaranteed with anything of Firefox popularity) just use: `sudo apt-get update` and then `sudo apt-get upgrade` and EVERY piece of software that is on your machine (and which is also in the repositories) will be updated to its most recent version. 

If you're physically at your computer and can't get things to open via command line, kindly copy and paste any error messages your machine gives you when you try.

---

### Post by pr0t3g3 on 2010-05-19
> **ubudog said:**
> So if you type "firefox" into a blank terminal, it won't start?
nah it just show's info on it.... Let me ask this though: If I wanted to remove a program or a previous patch (downgrade to a previous version) can I do that via the terminal? If so What would be a good command for it?

---

### Post by dakkar9999 on 2010-05-19
I just learned something!  BTW, you can't close the terminal without killing the program.  Why is that?

---

### Post by 3rdalbum on 2010-05-19
> **dakkar9999 said:**
> I just learned something!  BTW, you can't close the terminal without killing the program.  Why is that?

Because the program is launched as a child process of Bash. You close one program and its child processes die too.

---

### Post by pr0t3g3 on 2010-05-19
> **3rdalbum said:**
> Because the program is launched as a child process of Bash. You close one program and its child processes die too. and what may I ask is bash?

---

### Post by ryan858 on 2010-05-20
Type **man bash** into terminal

In fact, you can use **man** for pretty much anything related to linux in general. 99% of the commands and programs on your machine will have a man page (man stands for manual).

A short description of *bash*; it's a shell. A shell is what you use to process commands and stuff, basically.

You might try **man sh** as well.


And when all else fails, Google will prevail! Just google ***what is a shell in linux***.

---

### Post by ryan858 on 2010-05-20
> **3rdalbum said:**
> Because the program is launched as a child process of Bash. You close one program and its child processes die too.
I think there is a way to launch a program from a terminal without it being created as a child process... Anyone know how?

---

### Post by Oblivion_4 on 2010-05-20
> **ryan858 said:**
> I think there is a way to launch a program from a terminal without it being created as a child process... Anyone know how?

As one of the previous posters already stated you add the & symbol after any command which makes the process you create with that command become a child of the gnome instead of bash. For example firefox& or evolution&

---

### Post by ubudog on 2010-05-20
Say you typed ```
firefox
``` into a terminal.  If you close the terminal, both windows will close.  But if you type ```
firefox &
``` and you close the terminal, the firefox window will stay open, and the terminal window will close.

EDIT: Whoops, too late. :)

---

### Post by ubudog on 2010-05-20
If you want to remove a program type ```
sudo apt-get remove programname
```

---

### Post by kleskjr on 2010-05-20
> **ryan858 said:**
> I think there is a way to launch a program from a terminal without it being created as a child process... Anyone know how?

[COLOR="DarkOrange"]nohup firefox[/COLOR]

---

### Post by pr0t3g3 on 2010-05-20
> **kleskjr said:**
> [COLOR=DarkOrange]nohup firefox[/COLOR] I can startup firefox that way?  how does that work?

---

### Post by pr0t3g3 on 2010-05-20
> **ubudog said:**
> Say you typed ```
firefox
``` into a terminal.  If you close the terminal, both windows will close.  But if you type ```
firefox &
``` and you close the terminal, the firefox window will stay open, and the terminal window will close.

EDIT: Whoops, too late. :)
DO'H  ....DX I read that just now.. .I went to sleep before you edited obviously ... well now I know ^_^;

---

### Post by ubunterooster on 2010-05-20
Enter that in the terminal

Edit: post#17 intersected mine

---

### Post by pr0t3g3 on 2010-05-20
I did. However I have to leave soon for freshman orientation at Ivytech ;D. hey by the way ... I don't mean to go off topic but; why does the battery deplete so much faster on ubuntu than win xp?  honestly I had 3 backup batteries they are all brand new since about 5 days ago and worked fine until I loaded ubuntu, leading me to believe its the perp.... what gives?  I have 3 hours worth and it depletes in about 20 min..... what the heck o.O?!

---

### Post by ubunterooster on 2010-05-20
Add to panel: "CPU frequency monitor" I use it to keep my desktop using little power as well as the laptops I've helped with.

Edit: go to system>administration> Hardware drivers. See if there are any that are not installed; the opensource ones are often less efficient

---

### Post by lovinglinux on 2010-05-20
> **pr0t3g3 said:**
> Ex. what command is appropriate to applying a 3.5 version patch to the 3.0 version of firefox

See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by pr0t3g3 on 2010-05-20
I seriously need a solution lfor battery life T_T    I have about 20 min of power max for a BRAND new battery that has about 3-5 hours .... I know the batteries can't be faulty however as I used them to load my now treasured linux os ubuntu

---

### Post by pr0t3g3 on 2010-05-20
> **lovinglinux said:**
> See the [[COLOR=Sienna]**Installing Other Versions**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html") section of [Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567").
that was merely an example.... I'd like to know how to add and remove patches.... via terminal or otherwise

---

### Post by lovinglinux on 2010-05-20
> **pr0t3g3 said:**
> that was merely an example.... I'd like to know how to add and remove patches.... via terminal or otherwise

```
sudo apt-get update
sudo apt-get upgrade
```

This will download the lists of current available versions and the second will download and install.

---

### Post by pr0t3g3 on 2010-05-20
> **lovinglinux said:**
> ```
sudo apt-get update
sudo apt-get upgrade
```This will download the lists of current available versions and the second will download and install.>.< Was I not phrasing it properly?  No... er, I mean thank you for the link; thats actually quite helpful.  What I meant to say is.. How might I go about removing patches from most programs... is it different for individual programs; or is there a method to finding and removing patches to solve compatibility issues?

---

### Post by ubunterooster on 2010-05-20
[IMG]http://www.easyfreesmileys.com/smileys/free-confused-smileys-304.gif[/IMG]is that even possible?

---

### Post by pr0t3g3 on 2010-05-20
> **ubunterooster said:**
> [IMG]http://www.easyfreesmileys.com/smileys/free-confused-smileys-304.gif[/IMG]is that even possible?
.... which is what I'm asking -_-;

---

### Post by ryan858 on 2010-05-20
Technically, no... You have to actually install an earlier version. You're probably gonna have to download the actual deb and install it with ```
 sudo dpkg -i *<package> *
```

---

### Post by ubunterooster on 2010-05-20
You have to uninstall the current version. Also double clicking on .debs will start the installer just as good as if you entered the command line way to start it.

---

### Post by ryan858 on 2010-05-20
Yeah, he's right, clicking is easier, I forgot about that (I'm a command person). And yes, remove the old one first (new one in this case).

---

### Post by pr0t3g3 on 2010-05-21
I can find a thread on .debs in the forum correct?  I don't want to waste anyone elses time or my own if it's here I'll just search for it.. .however... If there is a site outside ubuntu please tell me.. for *me* searching is always harder than it should be T_T

---

### Post by ubudog on 2010-05-21
Yes, there should be plenty of articles on .debs here.

---

### Post by pr0t3g3 on 2010-05-21
> **ubudog said:**
> Yes, there should be plenty of articles on .debs here.


XD link me ;P

---

### Post by akakingess on 2010-05-21
Try [this]("https://help.ubuntu.com/search.html?cof=FORID%3A9&cx=004599128559784038176%3Avj_p0xo-nng&ie=UTF-8&q=deb+files&sa=Search") and you have several tutorials to choose from. By the way, I just did a search within Ubuntu Heip which has a link at the top of the forum. A very good resource that I have used almost as much as the 'man' pages.

---

### Post by ubudog on 2010-05-21
Yeah Ubuntu Help is also a very good resource.  [http://help.ubuntu.com]("http://help.ubuntu.com")

---

### Post by pr0t3g3 on 2010-05-22
Thank you, although I feel I need to add something here.  Don't get me wrong;  I got the answer to my question, still, I feel somethings missing. I'll refer back to here even if I have to revive this thread; Easier than starting a new one I guess.

---

### Post by ubudog on 2010-05-22
I'll be here.

---

### Post by pr0t3g3 on 2010-05-24
I was fooling with the terminal and accidentally/stupidly installed a, er, well, *something* by the name of ***[COLOR=Red]god[/COLOR]***[COLOR=Red][COLOR=Blue]  Sudo apt-get install god.[/COLOR][/COLOR] oops? How would I remove something like that;  It doesn't seem to be a program.. no.. more like a function... I don't really mind if it's not harmful but still I added it, I might as well know what it is.  I tried searching for it but came up with nothing.  Does anyone know what it is and how to remove such a thing via termial or otherwise?

---

### Post by SlidingHorn on 2010-05-24
> **pr0t3g3 said:**
> I was fooling with the terminal and accidentally/stupidly installed a, er, well, *something* by the name of ***[COLOR=Red]god[/COLOR]***[COLOR=Red][COLOR=Blue]  Sudo apt-get install god.[/COLOR][/COLOR] oops? How would I remove something like that;  It doesn't seem to be a program.. no.. more like a function... I don't really mind if it's not harmful but still I added it, I might as well know what it is.  I tried searching for it but came up with nothing.  Does anyone know what it is and how to remove such a thing via termial or otherwise?

I lol'ed @ this...anyway, according to Synaptic:

[quote=synaptic]God is an easy to configure, easy to extend monitoring framework
written in Ruby.

Keeping your server processes and tasks running should be a simple
part of your deployment process. God aims to be the simplest, most
powerful monitoring application available.[/quote]

You can get rid of it by:

```
sudo apt-get remove god
```

**Cue: giggling atheists**

---

### Post by pr0t3g3 on 2010-05-24
> **SlidingHorn said:**
> I lol'ed @ this...anyway, according to Synaptic:



You can get rid of it by:

```
sudo apt-get remove god
```**Cue: giggling atheists**


So it's for servers?

---

### Post by dasy2k1 on 2010-05-24
yep its a handy little util for server admins, but of no use to most normal users 
(not having used it myself it looks like it keeps track of server stuff and restarts processes if they stop for some reason)


as previous posters have said just 
```

sudo apt-get remove god

```
and this will uninstall it cleanly

---

### Post by pr0t3g3 on 2010-05-24
> **dasy2k1 said:**
> yep its a handy little util for server admins, but of no use to most normal users 
(not having used it myself it looks like it keeps track of server stuff and restarts processes if they stop for some reason)


as previous posters have said just 
```

sudo apt-get remove god

```and this will uninstall it cleanly
o_o;  . . . uhm... look at my post at the very end! and tell me if the reason for my problem is because that 'server tool' was remote conrolled to edit my system >.< it's a long shot but if I'm correct I screwed myself over and need a solution T_T a big one!
[http://ubuntuforums.org/showthread.php?t=1493214]("http://ubuntuforums.org/showthread.php?t=1491810")

I was running as root when i enabled and messed with some network files.... 
[ ]("http://ubuntuforums.org/showthread.php?t=1491810")

---

### Post by pr0t3g3 on 2010-05-31
I need a solution to the link to a new thread above please!  ^

---

### Post by pr0t3g3 on 2010-06-06
To bump my original post: What are some useful random commands for the terminal... can I use the terminal to install something I downloaded? for example:    [http://www.zophar.net/linux/nes/fwnes.html](http://www.zophar.net/linux/nes/fwnes.html)

I'm hard pressed to find on that has a screen a menu for loading roms and a toolbar to configure the controlls... isn't that all an emulator should be?

---

