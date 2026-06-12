---
title: "My first steps out of a windows environment, advice?"
date: 2010-03-14
forum: General Help
---

### Post by makari on 2010-03-14
so I've finally decided to install and try out an OS other than windows... 
 
but where do I start? ubuntu? kubuntu? something else?
 
if using any of these is there a shell program or something that will allow me to install windows applications still? games in particular - or am I under a false impression that windows based programs will not run on linux in general?
 
aside from the general looks, and default programs like browsers... what if any are the real differences between ubuntu, kubuntu, edubuntu, gobuntu, and any other popular versions out there?
 
what is kde?   I see a lot about it on this forum but I'm clueless..
 
what exactly is gnome?  again, i see a lot but I'm clueless...
 
 
and I'm looking for suggestions for what to do fresh after install... for example with windows I'd run around grabbing updated drivers, then possibly setup email programs and install office or something, install firefox, tweak resolution and some file options (like view hidden files, show file extensions.. ) but I have no idea if any or all these things are even necessary in linux, and if they are, how to even check or where to go to get them done.
 
is there a device manager equivalent? a quick rundown of things still needing drivers?
 
where would I go to change settings like resolution?
 
thanks for any suggestions or advice you can give.

---

### Post by linuxman94 on 2010-03-14
> but where do I start? ubuntu? kubuntu? something else?


Ubuntu would be just fine.

> if using any of these is there a shell program or something that will allow me to install windows applications still?

There is wine.  It won't work with all windows programs though.  You could use virtualbox and install windows as a virtual OS. (Windows inside linux)

> aside from the general looks, and default programs like browsers... what if any are the real differences between ubuntu, kubuntu, edubuntu, gobuntu, and any other popular versions out there?

Basically the only difference is the applications that come pre-installed.

> what is kde? I see a lot about it on this forum but I'm clueless..


KDE is a desktop environment.

> what exactly is gnome? again, i see a lot but I'm clueless...

Gnome is the desktop environment that comes standard with Ubuntu.

> and I'm looking for suggestions for what to do fresh after install... for example with windows I'd run around grabbing updated drivers, then possibly setup email programs and install office or something, install firefox, tweak resolution and some file options (like view hidden files, show file extensions.. ) but I have no idea if any or all these things are even necessary in linux, and if they are, how to even check or where to go to get them done.


Ubuntu loads most drivers automatically.  You may need to enable proprietary drivers for your graphics card in System -> Administration -> Hardware Drivers but thats about it.

> is there a device manager equivalent? a quick rundown of things still needing drivers?

As i said, Ubuntu loads the drivers automatically.

> where would I go to change settings like resolution?

System -> Preferences -> Display

I hope you enjoy Ubuntu!

Remeber, Linux is NOT Windows so dont get frustrated if you can't figure out how to do something.

---

### Post by Pjotr123 on 2010-03-14
This is the list of things that I always do straight after a fresh installation of Ubuntu:
[http://sites.google.com/site/easylinuxtipsproject/first](http://sites.google.com/site/easylinuxtipsproject/first)

Have fun! :)

---

### Post by makari on 2010-03-14
awesome, thanks for the info and the tips..
 
any other suggestions for a first time user?

---

### Post by spiky001 on 2010-03-14
Hi welcome to the world of linux, Why dont you download all the flavors of unbuntu that you would like to try, you can try before you install ( run as live cd ) see which 1 you like the best, Another option when you have decided you can dual boot with windows incase gaming dosn't work to well on linux and still have a friendly OS incase of trouble

---

### Post by gadolinio on 2010-03-14
· where do I start? ubuntu? kubuntu? something else? 
 

ubuntu is very easy to use, so it would be a very good choice to begin with. Then you can compare other distributions also, and then choose which one is better for you. I still use ubuntu because i find it really simple to use, and everything works perfectly.
 

  

 ·if using any of these is there a shell program or something that will allow me to install windows applications still? games in particular - or am I under a false impression that windows based programs will not run on linux in general? 
 

 You can use some windows programs, but not all of them, and even some of the ones that do work do it in a, let's say, “rough” way.  
 The linux application you can use as an “adaptor” is called “wine”. After you have it installed, you'll be able to execute windows's exe files just as you usually do. They might not work (not be opened at all), attempt to open and then suddenly close, work but with some flaws, or work perfectly OK. I use it with some games and other applications and in general it works perfectly well.
 



  
 ·what is kde? I see a lot about it on this forum but I'm clueless.. 
  ·what exactly is gnome? again, i see a lot but I'm clueless... 
 

 They're both desktop environments. That would be, they take care of the graphical interface of your computer. In my personal opinion, GNOME is better. I find KDE a bit ugly :P
  
  
 



·and I'm looking for suggestions for what to do fresh after install... for example with windows I'd run around grabbing updated drivers, then possibly setup email programs and install office or something, install firefox, tweak resolution and some file options (like view hidden files, show file extensions.. ) but I have no idea if any or all these things are even necessary in linux, and if they are, how to even check or where to go to get them done. 
 

 Regarding updates and any important thing you need to add to your system after fresh intall, ubuntu will automatically let you know that there are things to install, and you'll only need to say OK.
 Other thigns might need to be added when you first use them. For example, the first time you open a mp3 file, you'll be told that you lack the necessary codecs. The same prompt has the option of finding them, so you just have to follow the steps you see.
 Email programs are used almost the exact same way in linux.  
 You don't need to install office in ubuntu, as it comes with an equivalent called openoffice. Once the system is installed, you'll also have openoffice to deal with .doc, .xls, .ppt, etc.
Firefox comes installed with ubuntu.
For other config changes you want to make, you have two menus inside the System menu in the upper toolbar: preferences, and administration. Preferences has the config settings more user-related, let's say, and administration deals with those that affect the whole system. Give those menus a look, and you'll find what you have in thw windows control panel.
 
 



·is there a device manager equivalent? a quick rundown of things still needing drivers? 
 ·where would I go to change settings like resolution? 
 

 Things like this, which affect the entire system, are under the administration menu (from the system menu of the upper panel). Other configuration can be done from system---> preferences.


Remember that for any other question you have, you will almost certainly find an answer in theese forums o others, or in the ubuntu documentation page. Just surf the web... everything can be foud there!
Good luck, and reply if you have any doubts!

---

### Post by gjoellee on 2010-03-14
.> **makari said:**
> so I've finally decided to install and try out an OS other than windows... 
 
but where do I start? ubuntu? kubuntu? something else?
[B]
I recommend starting with Ubuntu, as it usually will get fester help with it[/B]
 
if using any of these is there a shell program or something that will allow me to install windows applications still? games in particular - or am I under a false impression that windows based programs will not run on linux in general?
 
**Some windows programs may run on Linux with programs as WINE, Cedega or Corssover (WINE is recommended)**

aside from the general looks, and default programs like browsers... what if any are the real differences between ubuntu, kubuntu, edubuntu, gobuntu, and any other popular versions out there?

[B]Ubuntu is the standard distro with the GNOME desktop
Kubuntu is Ubuntu, but with KDE
Edubuntu is Ubuntu designed for educational users
Gobuntu [http://en.wikipedia.org/wiki/Gobuntu](http://en.wikipedia.org/wiki/Gobuntu)

There are other flavors of Ubuntu, as well as hundreds of other Linux distributions out there. See [www.distrowatch.com](www.distrowatch.com) to see the most popular
[/B]  
what is kde?   I see a lot about it on this forum but I'm clueless..

**KDE is the K Desktop Environment [http://www.kde.org/community/whatiskde/](http://www.kde.org/community/whatiskde/) [http://en.wikipedia.org/wiki/Desktop_environment](http://en.wikipedia.org/wiki/Desktop_environment)**
 
what exactly is gnome?  again, i see a lot but I'm clueless...
 
GNOME is also a desktop environment [www.gnome.org](www.gnome.org)
 
and I'm looking for suggestions for what to do fresh after install... for example with windows I'd run around grabbing updated drivers, then possibly setup email programs and install office or something, install firefox, tweak resolution and some file options (like view hidden files, show file extensions.. ) but I have no idea if any or all these things are even necessary in linux, and if they are, how to even check or where to go to get them done.
 
is there a device manager equivalent? a quick rundown of things still needing drivers?
 
**See "Hardware Drivers" in the Systeam --> Administration menu**

where would I go to change settings like resolution?

**See the System menu**
 
thanks for any suggestions or advice you can give.

**Play around. It is the only way to learn how stuff works!**

---

### Post by colobix on 2010-03-14
You know, you don't have to completely change to ubuntu.
You can install it as a daul boot next to windows so that you can choose windows or ubuntu when you start your PC.
There are still a few things you must have windows installed for.
For example you need windows to your ipod touch or iphone (or you can jailbreak it).
But if you don't play alot pc games nor have an ipod touch you don't need windows.
You can find many cool games for ubuntu on [http://www.playdeb.net](http://www.playdeb.net).

---

### Post by colobix on 2010-03-14
You know, you don't have to completely change to ubuntu.
You can install it as a daul boot next to windows so that you can choose windows or ubuntu when you start your PC.
There are still a few things you must have windows installed for.
For example you need windows to your ipod touch or iphone (or you can jailbreak it).
But if you don't play alot pc games nor have an ipod touch you don't need windows.
You can find many cool games for ubuntu on [http://www.playdeb.net](http://www.playdeb.net).
Also, a very important thing to keep in mind is that if something goes wrong in ubuntu you can always fix it. And I mean alwasy.
You know, in windows you have spyware and viruses that can piss you off and sometimes you can't even fix all the bugs you get.
And in windows, you can't just play around and see how things works because in windows things will always go wrong somehow.
In ubuntu you can play around and stuff to learn how things works and stuff.

---

### Post by d3v1150m471c on 2010-03-14
If you have at least 3GiB of RAM and dual 2.0ghz processors or higher, I would strongly recommend kubuntu. The KDE environment is wonderful. For anything less than that, go with default Ubuntu or xubuntu for less flash and bang but better performance. All of these come with a default browser but I would suggest switching to google chrome beta for linux or swiftfox for addons and performance. For everything else there's mastercard.

PS. for typical things you'll want to alter only takes a touch of common sense and are relatively easy to find/manage. IE network manager, keyboard settings, display manager, ect. ;)

---

### Post by gadolinio on 2010-03-15
> **colobix said:**
> you know, you don't have to completely change to ubuntu.
You can install it as a daul boot next to windows so that you can choose windows or ubuntu when you start your pc.
There are still a few things you must have windows installed for.
For example you need windows to your ipod touch or iphone (or you can jailbreak it).
But if you don't play alot pc games nor have an ipod touch you don't need windows.
You can find many cool games for ubuntu on [http://www.playdeb.net](http://www.playdeb.net).
Also, a very important thing to keep in mind is that if something goes wrong in ubuntu you can always fix it. And i mean alwasy.
You know, in windows you have spyware and viruses that can piss you off and sometimes you can't even fix all the bugs you get.
And in windows, you can't just play around and see how things works because in windows things will always go wrong somehow.
In ubuntu you can play around and stuff to learn how things works and stuff.

+1

---

### Post by blairm on 2010-03-15
Once you install Ubuntu, with the default Gnome desktop environment, you might like to try KDE as well.
You can do that by downloading the kubuntu-desktop package from the Synaptic Package Manager (found under System - Admin).
I'd suggest that so you can see which you're more comfortable with; different people have different preferences.
You can switch between the two when you log in to Ubuntu.

---

