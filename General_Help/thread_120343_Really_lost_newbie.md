---
title: "Really lost newbie"
date: 2006-01-21
forum: General Help
---

### Post by tanman on 2006-01-21
Hi Everyone
I just installed ubuntu last night and I am trying to figure things out. I am a windows user. Not to sound too stupid, but I have no idea how to install programs. I have downloaded both firefox 1.5 and aim and they are sitting on my desk top. The firefox is a 1.5.tar.gz. I am use to just clicking on the icon and it installs. Where do I go to install anytime of program not just these 2. I really want to learn linux, but I am really lost and a little frustrated that I can not figure out what to do. 
Thanks for any help.

---

### Post by Adrian on 2006-01-21
[QUOTE=tanman]Hi Everyone
I just installed ubuntu last night and I am trying to figure things out. I am a windows user. Not to sound too stupid, but I have no idea how to install programs. I have downloaded both firefox 1.5 and aim and they are sitting on my desk top. The firefox is a 1.5.tar.gz. I am use to just clicking on the icon and it installs. Where do I go to install anytime of program not just these 2. I really want to learn linux, but I am really lost and a little frustrated that I can not figure out what to do. 
Thanks for any help.[/QUOTE]

Installing software in Linux is a bit different from doing it in Windows.

Read this guide by aysiu:
[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by bschuteker on 2006-01-21
It takes some getting used to, I'm still learning myself.These forums are a great place to start. Search for what you are trying to do. Chances are that someonehas done it and will tell you how. I'm not sure about AIM but when I did my permanant install over a month ago I found Automatix. It will do a lot of things for you. Just make sure that you read and select what you want to do . It will make Breezy a lot more user friendly.

Here is the post for Automatix
[http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

Most importantly search the forum, it has taught me a lot!!!

---

### Post by tanman on 2006-01-21
So not to sound really stupid, but were do I go to type thses commands in. If I go to synaptic package manager is that right or is there some where I am missing. I realize it is probably really simple once I find the right place to be and where to type in these commands.

---

### Post by Adrian on 2006-01-21
[QUOTE=tanman]So not to sound really stupid, but were do I go to type thses commands in. If I go to synaptic package manager is that right or is there some where I am missing. I realize it is probably really simple once I find the right place to be and where to type in these commands.[/QUOTE]

The commands (such as **apt-get**) are supposed to be executed from a *terminal*. You can find one in the "Applications" menu at the top of the screen.

The Synaptic Package Manager is a graphical tool to help you avoid typing these commands. :)
Instead it lets you search for packages and mark them for installation. Pressing the "Apply" button finally does the install.

---

### Post by aysiu on 2006-01-21
[QUOTE=Adrian]The commands (such as **apt-get**) are supposed to be executed from a *terminal*. You can find one in the "Applications" menu at the top of the screen.[/QUOTE] Specifically, Applications > Accessories > Terminal

---

### Post by poiuytr on 2006-01-21
For a newbie, I would recommend using Synaptic at first.  Although, Linux is a learning experience so the more you can understand what is happening behind the scenes, the better off you will be in the long run.

To use Synaptic, just go to the menu at the top of your desktop and click on "System" and then "Administration" and then on "Synaptic Package Manager"

One of the first things you might want to do within Synaptic is click on "Settings" and "Repositories."  A screen will open up that says "Software Preferences."  On the bottom of that screen, click on where IT says "Settings"(next to where it says "Authentication."  After you do this, make sure you check "Show Disabled Software Sources."  Click "OK," and close that screen.  Then, back in the "Software Preferences" screen, make sure you have enabled not only the official Ubuntu "Software sources" but also the "Multiverse/Universe" sources.  You will be asked if you now want to download new available new packages (in Linux, "packages" are basically the equivalent to .exe "programs" or "applications" in the Windows world).  Click "Yes" to that.

Remember, Synaptic is just a GUI, hiding the real commands from you to make it really easily point and click just as you are used to with Windows.  But in reality, what have you just now actually done with all of this pointing and clicking?

If you were doing this from the command line, you would have been changing your directory to the one where the sources.list file is, and modifying that file (example, "cd /etc/apt"  and then "sudo gedit sources.list")

Okay, now to find "Firefox" or whatever package you need.  In Synaptic, close the Software Preferences screen, and click on Search" (upper right corner) and type in "Firefox" or whatever.  When you ind it, Mark its box for Installation, and when you're ready, click on "Apply" (it's up there near "Search") like the other poster told you.  Soon, Firefox will have been installed on your system and you can start using it.

Oh, and PS, usually you don't have to re-boot after installing a package.  In many ways, installing programs in Linux is way easier than in Windows, once you get used to it.

BTW, if you did this from the command line, after you had modified your sources.list file as described above, you oul b typing things like "apt-get update" and "apt-get upgrade" and "apt-get install firefox."  Read Google for details on those.  Synaptic is just a nice, pretty overlay for doing all of that.  Windows uses nice, pretty overlays, also, but Windows doesn't usually allow you to look behind the curtain and see what is actually happening.  In Windows you'll get a pretty splash screen saying "55% installed" or something.  One of the beuties of Linux is that you CAN look behind the pretty curtain that is covering up and hiding your computer experience from you, and the more you can learn about the command line and what is really happening, the more powerful a computer user you become.

I hope this helps a little.  Good luck!

---

### Post by tanman on 2006-01-21
Ok Thanks. I have tried that, but when I search for firefox 1.5 it does not find anything. When I search for just firefox it finds the one that is installed in Ubuntu already.
I would like to upgrade to 1.5. I found the download on the firefox web page, but it just sits on my desk top when I down load it.
Thanks again for any help.
Has anyone else tried the automatic mentioned earlier in the thread

---

### Post by f76 on 2006-01-21
try the automatix script - it gives you ffx1.5 and a lot of other stuff

---

### Post by nominal on 2006-01-21
ok , im also new ot linux, and i had the same exact problem as u!

then people helped me so this is what you do:

1. screw aim, seriously, use the already supplied 'Gaim' found by going to applications-->internet---> gaim messenger

2. u can use automatix "search for the thread" to get firefox, or u can do it the way i did it, so you can only add the extensions you want!

ok...you have to go to this site [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

then this is where i got confused b4--but help came

after d/l the firefox for linux---its called a tar i think, leave it on ur desktop. then go to applications-->accesorires-->terminal

this will bring up terminal...terminal is odd, and really wierd to windows users, this is what u wnan type in first: sudo apt-get install libstdc++5

by doign that it will aks u for ur pasword, WHICH WHEN U TYPE will not come on the screen, dont fret, it is typing, just type in ur pasword and hit enter,

if u put the codei n right it will do some sutff and not tell u that u didnt get the file

next, follow the rest of the instructions on the page, you hsould be fine, but if ur not just feel free to post.! :D

---

### Post by Adrian on 2006-01-21
[QUOTE=tanman]Ok Thanks. I have tried that, but when I search for firefox 1.5 it does not find anything. When I search for just firefox it finds the one that is installed in Ubuntu already.
I would like to upgrade to 1.5. I found the download on the firefox web page, but it just sits on my desk top when I down load it.
Thanks again for any help.
Has anyone else tried the automatic mentioned earlier in the thread[/QUOTE]

Once a certain Ubuntu version (like Breezy Badger that you are using now) is released, no newer versions of the programs will be added to the main repositories. As a consequence of this, you can't use them for installing a newer version of Firefox. This is usually no problem since a new Ubuntu version is released every six months.

Anyway, for people wanting the newest versions anyway, there is the Backports repository. You can enable it by editing the file **/etc/apt/sources.list** (and following the instructions). However it doesn't include Firefox 1.5, because it would be very tricky to backport.

As other posters have written, you can use Automatix to install FF1.5.

---

