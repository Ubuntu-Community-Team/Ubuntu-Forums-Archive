---
title: "Where are my new files???"
date: 2009-09-19
forum: General Help
---

### Post by thegutterpoet on 2009-09-19
I have installed gtalk, and also a game called sauerbaten, from the file sauerbraten-data_0.0.20090504-1~getdeb1_all.deb 

and also gtalk, via the synaptic package manager...and the installations seemed to run fine, but nothing new has appeared in any of the drop down menus for Applications. So where do I find my new files???


( i am running the 64bit version of ubuntu 9.04)

---

### Post by beastrace91 on 2009-09-19
Pop open a terminal and try running 'gtalk' (with out quotes) and/or 'sauerbaten'  (again with out the quotes)

~Jeff

---

### Post by thegutterpoet on 2009-09-19
Perhaps I need more than just the words alone, mate???

I tried typing them into the terminal, as single words, but 'command not recognized...'

---

### Post by beastrace91 on 2009-09-19
> **weedguru said:**
> 'command not recognized...'

Are you sure you are typing the names correctly? You have it typoed for the game at least in your first post - try running 'sauerbraten'

~Jeff

---

### Post by beastrace91 on 2009-09-19
Also is this - [http://www.getdeb.net/app/pidgin-musictracker](http://www.getdeb.net/app/pidgin-musictracker)

The gtalk app you installed? If so that is simply a pluggin for pidgin and not a stand alone application (Meaning load pidgin and enable the pluggin)

~Jeff

---

### Post by thegutterpoet on 2009-09-19
My pidgin already was happy to play google talk details...I thought I had download a stand alone gtalk for linux...but you may have been Right.

As for the Game file...no joy whatsoever.
Where would I find the folder it created when it installed??? And perhaps I need to download more files??? This one was 344MB and called (DATA)...I assumed as it was the biggest of the bunch, that it was the one I needed...

---

### Post by beastrace91 on 2009-09-19
Ahh yes you are correct there is a second file you need install for that game - [http://www.getdeb.net/release/4339](http://www.getdeb.net/release/4339)

See this [second deb download](http://www.getdeb.net/download/4339/0) actually called the game's name and not data? Thats the one you need to install to add the menu entries and such. Where did you download gtalk from? The only thing I can find online about it is a pidgin pluggin.

~Jeff

---

### Post by 3rdalbum on 2009-09-19
> **weedguru said:**
> I have installed gtalk, and also a game called sauerbaten, from the file sauerbraten-data_0.0.20090504-1~getdeb1_all.deb 


The file "sauerbraten-data" just contains maps, 3d models and sounds for the game. You need the "sauerbraten" package as well because it contains the actual game.

> and also gtalk, via the synaptic package manager...and the installations seemed to run fine, but nothing new has appeared in any of the drop down menus for Applications. So where do I find my new files???

First check that whatever you have installed isn't just a library or command-line program. Secondly, look at the screencast in my signature. Tells you all about how to find the names of the programs included in a package, and then about putting the name as "command" in a new launcher.

---

### Post by qamelian on 2009-09-19
> **weedguru said:**
> My pidgin already was happy to play google talk details...I thought I had download a stand alone gtalk for linux...but you may have been Right.

As for the Game file...no joy whatsoever.
Where would I find the folder it created when it installed??? And perhaps I need to download more files??? This one was 344MB and called (DATA)...I assumed as it was the biggest of the bunch, that it was the one I needed...
You need to download all of them. The file you downloaded is not the game, just data needed to play it.

---

### Post by thegutterpoet on 2009-09-19
damn it...but I suspected as much.

So...as I am new to linux...I want to ask:

Unlike windows, where a new file is easy to find, just by heading to where I CHOSE to have it installed when asked, when I install applications with ubuntu, do I sometimes nee to use the terminal to run them??? Or do they invariably find their niche in the Applications drop down menu???

(thankyou for the help, people, especially as I realize that I am making, what would seem perhaps insultingly rudimentary errors for those in the Know!)

---

### Post by beastrace91 on 2009-09-19
> **qamelian said:**
> You need to download all of them. 

I think the third deb is optional unless you want to run a server ;) "sauerbraten-server  (124.0 kB)"

~Jeff

---

### Post by beastrace91 on 2009-09-19
> **weedguru said:**
> Unlike windows, where a new file is easy to find, just by heading to where I CHOSE to have it installed when asked, when I install applications with ubuntu, do I sometimes nee to use the terminal to run them??? Or do they invariably find their niche in the Applications drop down menu???

This depends 100% on the application in use NOT the operating system. There are some apps in Ubuntu/Linux that give you an optional install path (just like there are in Windows) but for the most part they just install to your /home directory.

As for "popping" in your applications menu - any decent app for Linux will automatically add it's own menu entries yes.

~Jeff

---

### Post by thegutterpoet on 2009-09-19
I also had this file:

sauerbraten_0.0.20090504-1~getdeb1_i386.deb

but when i clicked to install it, i was told 'i386' WRONG ARCHITECTURE...

does this mean I am unable to install this game on my ubuntu version?? or just that I need to find another version????

---

### Post by qamelian on 2009-09-19
> **beastrace91 said:**
> I think the third deb is optional unless you want to run a server ;) "sauerbraten-server  (124.0 kB)"

~Jeff
Yeah, that's right. I should have specified that I was referring to apps downloaded from getdeb in general.

---

### Post by Barrucadu on 2009-09-19
> **beastrace91 said:**
> There are some apps in Ubuntu/Linux that give you an optional install path (just like there are in Windows) but for the most part they just install to your /home directory.

Really? Name one application that, by default, installs itself to the user's home folder.

---

### Post by qamelian on 2009-09-19
> **beastrace91 said:**
> This depends 100% on the application in use NOT the operating system. There are some apps in Ubuntu/Linux that give you an optional install path (just like there are in Windows) but for the most part they just install to your /home directory.
~Jeff
Actually, this is wrong. Most apps don't install to the users home directory at all. There isn't necessarily a single point where the files that make up an app will in stall. They may be scattered across a variety of directories. The executable usually ends up in /usr/bin or /usr/local/bin, but additional libraries and config file will end up in other locations. The only thing that normally nds up in you home folder is any personalization you do to the app's config that would not be system-wide.

---

### Post by qamelian on 2009-09-19
> **Barrucadu said:**
> Really? Name one application that, by default, installs itself to the user's home folder.
Gnome-shell, if you follow the build instruction on live.gnome.org. :P

But you're right, in general, nothing installs to home.

---

### Post by beastrace91 on 2009-09-19
> **weedguru said:**
> i was told 'i386' WRONG ARCHITECTURE...

You are running 64bit Ubuntu correct? i386 is the 32bit installer. Go download the 64bit version.

> Really? Name one application that, by default, installs itself to the user's home folder. 

Most all applications by default store the bulk of their data in the users /home folder, Wine, Cedega, Mozilla, Virtual Box...

~Jeff

---

### Post by beastrace91 on 2009-09-19
> **qamelian said:**
> The only thing that normally nds up in you home folder is any personalization you do to the app's config that would not be system-wide.

Yea - all the end user configuration and saves are stored in /home. Isn't this typically the bulk of the data?...

~Jeff

---

### Post by beastrace91 on 2009-09-19
> **Barrucadu said:**
> Really? Name one application that, by default, installs itself to the user's home folder.

And if you really want to be picky the Maple series fully installs to /home as well as the Heros of Nernwerth Beta ;)

~Jeff

---

