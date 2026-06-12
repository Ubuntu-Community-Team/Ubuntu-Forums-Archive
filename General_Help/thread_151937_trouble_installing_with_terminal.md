---
title: "trouble installing with terminal"
date: 2006-03-28
forum: General Help
---

### Post by aresgoddess on 2006-03-28
i just updated from Hoary Hedgehog to Breezy Badger. (i was holding out for Dapper Drake, but when i found out it wasn't going to be released in April and that Breezy Badger has better support for this one wireless card i want to get, i switched. ^_^' )

anyways, i was trying to follow the directions located [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) to install codecs because I couldn't find anything about using Synaptic PM to install them. But I keep getting error messages when I type in the code and hit enter in the terminal.

For instance:
user@compname:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer
 
and

user@compname:~$ wget -c [ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb) sudo dpkg -i w32codecs_20040412-0.0_i386.deb
--20:12:45--  [ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
           => `w32codecs_20050412-0.0_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14, 2001:7a8:1:5::14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat/pool/mail/w/w32codecs ...
No such directory `debian-marillat/pool/mail/w/w32codecs'.

--20:12:49--  [http://sudo/](http://sudo/)
           => `index.html'
Resolving sudo... failed: Name or service not known.
--20:12:49--  [http://dpkg/](http://dpkg/)
           => `index.html'
Resolving dpkg... failed: Name or service not known.
w32codecs_20040412-0.0_i386.deb: No such file or directory
No URLs found in w32codecs_20040412-0.0_i386.deb.

Am I doing something wrong? Please help! My roommate is singing some really awful songs and I need my own music to block out the horrors!

PS Is it possible to install the codecs using Synaptic?

---

### Post by wsanders on 2006-03-28
Do you have the extra repositories enabled in your /etc/apt/sources.list file?

---

### Post by xXx 0wn3d xXx on 2006-03-28
use [ this sources.list ](http://www.ubuntuforums.org/showthread.php?t=92672) then it will work fine. Might I also recommend automatix to install the things that you need ?

---

### Post by aresgoddess on 2006-03-28
[QUOTE=wsanders]Do you have the extra repositories enabled in your /etc/apt/sources.list file?[/QUOTE]

eh heh...i thought i did. but i double checked and they weren't enabled... X.x i hate it when that happens... ](*,)

---

### Post by aresgoddess on 2006-03-29
For anyone who does a search on .avi or avi codecs because they can't get Totem to play their media files and because using a terminal or Automatix makes you feel like an idiot:
(1) open up Synaptic Package Manager
(2) make sure you have enabled all of the repositories
 --Click on Settings, then Repositories
(3) edit the community maintained repositories
 --Under Sections, add "multiverse" after "universe"
(4) Click OK and allow Synaptic to refresh itself. (it should prompt you to do so.)
(5) search for totem-xine and mark for installation. it will say that Totem and totem-gstreamer will need to be uninstalled. This is what you want. :D 
(6) Apply changes and after it's done, enjoy your movie files! 
Fu!! ^_^d

---

### Post by NewWithoutClue on 2006-03-29
[QUOTE=aresgoddess]i just updated from Hoary Hedgehog to Breezy Badger. (i was holding out for Dapper Drake, but when i found out it wasn't going to be released in April and that Breezy Badger has better support for this one wireless card i want to get, i switched. ^_^' )

anyways, i was trying to follow the directions located [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) to install codecs because I couldn't find anything about using Synaptic PM to install them. But I keep getting error messages when I type in the code and hit enter in the terminal.

For instance:
user@compname:~$ sudo apt-get install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mozilla-mplayer

[/QUOTE]

Maybe thats the wrong name? ( mozilla-mplayer ) try ```
sudo apt-cache dump | grep 'mplayer' 
``` to find names of packages that may be what you need/want.

[QUOTE=aresgoddess]

and

user@compname:~$ wget -c [ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb) sudo dpkg -i w32codecs_20040412-0.0_i386.deb
--20:12:45--  [ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb)
           => `w32codecs_20050412-0.0_i386.deb'
Resolving ftp.nerim.net... 62.4.17.14, 2001:7a8:1:5::14
Connecting to ftp.nerim.net|62.4.17.14|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /debian-marillat/pool/mail/w/w32codecs ...
No such directory `debian-marillat/pool/mail/w/w32codecs'.

--20:12:49--  [http://sudo/](http://sudo/)
           => `index.html'
Resolving sudo... failed: Name or service not known.
--20:12:49--  [http://dpkg/](http://dpkg/)
           => `index.html'
Resolving dpkg... failed: Name or service not known.
w32codecs_20040412-0.0_i386.deb: No such file or directory
No URLs found in w32codecs_20040412-0.0_i386.deb.

Am I doing something wrong? Please help! My roommate is singing some really awful songs and I need my own music to block out the horrors!

PS Is it possible to install the codecs using Synaptic?[/QUOTE]

Yes you are doing something wrong. BASH thought that all that line was one command because you didn't tell it other wise... so wget thought you wanted to get index.html from 'dpkg' when you really wanted to execute dpkg.

To tell BASH to execute some command then other on the same line you could 
A) use the ';' instruction to tell bash to execute the commands after ';' only after the first command has exited ( regardless of exit status ) 
B) you could use "&" which would execute both commands at the same time ( echo "blah" & echo "blah2"  would execute both echo commands at the same time ). 
C) you could use "&&" which would tell BASH _only_ to execute the following command if the previous command exited with a succesful status ( eg. no error )

The C option is what i suggest you use. Or just enter the commands one at a time.

EXAMPLES:
A) would be this in your situation:
```
wget ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb; sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```
B) would be this in your situation:
```
 wget ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb & sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```
This would execute both the download and the installation AT THE SAME TIME.. you don't want this because you have to have the package before you can install it.. ( remember the "&" instuction tells BASH ( the shell ) to execute the commands before and after it ( the "&" ) AT THE SAME TIME ) so don't use it.. i'm just showing you this so you ( and others ) know in the future what to do and what not to do depedning on the current sistuation they are in.

And C) ( the better one ) ```
wget ftp://ftp.nerim.net/debian-marillat/pool/mail/w/w32codecs/w32codecs_20050412-0.0_i386.deb && sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```

This will ONLY execute the "dpkg -i w32codecs_20050412-0.0_i386.deb" if, and ONLY IF, the download process exited WITHOUT errors. This is the suggested action for most situations.

I'm sorry is if you don't understand. I try to be as clear as i can.


--
p01n7

---

### Post by aresgoddess on 2006-04-02
i typed the command in exactly as I saw it written in the post. ;.; 

i've been using Ubuntu for a while now, but I get so confused when it comes to using the terminals. my boyfriend, who uses gentoo (spelling?), helps me out, but he doesn't really teach me about how to use command lines. he kinda just does it himself... x.X

---

