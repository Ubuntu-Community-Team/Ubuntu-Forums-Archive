---
title: "Please help me install 'Basic Linux' onto 2 Floppy disks"
date: 2011-04-25
forum: General Help
---

### Post by princerameses on 2011-04-25
[COLOR="DarkOrchid"][B]
[This]("http://distro.ibiblio.org/pub/linux/distributions/baslinux/") is what I am trying to get for my dinosaur, Compaq Presario 5050. But I have never booted linux through floppy disks before, so I haven't a clue what I am doing. 

In the read me from the site I linked above, it said they need to be 1.44 M and DOS formatted. Both are 144, and I went to my computer (in XP) and right clicked on the floppy, format, and create bootable DOS disk.  But this fills the disk up with files, and even when I deleted them all, it said there was not enough room for one of the two files I am supposed to copy on to it.

So, how do I make the file fit onto the floppy, and how do I write the image file to one of the floppies? In DOS? I can use linux too, if necessary. (if it's easier)

I need STEP BY STEP instructions, leaving even the simplest step out; I have never used DOS before. 

Thank you.

[This]("http://tiny.seul.org/en/i.html")
[/B][/COLOR]is another one I am looking at, but basic linux looks easier to install.

---

### Post by mr.farenheit on 2011-04-25
have you looked into installing your choice distro from a flash drive?

---

### Post by btindie on 2011-04-25
Have you read the README.TXT file that comes in the ZIP?

The first file, DISK1.IMG, is a disk image like an ISO that needs to be written directly to a floppy. From Linux you can use *dd* to do this. The second file just needs to be copied to the floppy as a normal file, you can delete everything else that's on there. From Linux just do
```
$ sudo dd if=disk1.img of=/dev/fd0
```
to create the first floppy disk.

---

### Post by princerameses on 2011-04-25
Since I referred to the readme, yes, I read it. But wanted to try DOS so I don't have to switch hard drives. 

Ok, but what about the size issue? It says there's not enough room.

And I would have no clue how to get it to work on a USB if possible.

---

### Post by Joe of loath on 2011-04-25
Is this your PC? [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00191381&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=92982](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00191381&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=92982)

If so, why bother with Basiclinux? That's designed for old 486 machines with <8mb of RAM. Damn Small Linux or a basic install of Debian will suit you better.

---

### Post by princerameses on 2011-04-25
[COLOR="DarkOrchid"][B]Yes, but I've tried most of the other lite ones.. They either wouldn't boot, or lagged/ froze/ crashed. DSL worked pretty well, but only an older version would work, and I couldn't get flash to work. I at least want to give this one a try.



So the capacity is the real issue I guess. Why is it saying there's not enough space? the ReadMe.txt said 1.44 MB Floppy disk, that's what I have x2. [/B][/COLOR]

---

### Post by btindie on 2011-04-25
> **princerameses said:**
> Since I referred to the readme, yes, I read it. But wanted to try DOS so I don't have to switch hard drives. 
If you want to make it from DOS then use the included fdimage program to create the first floppy disk
```
fdimage disk1.img  a:
```I'm not sure if this is a pure DOS program or not, there are a few alternatives that you can use from windows called rawrite and rawritent.

> Ok, but what about the size issue? It says there's not enough room.That's because the first file is designed to be written directly to the floppy as a disk image and NOT a file. The second one is just a normal file for which you can just copy.

> And I would have no clue how to get it to work on a USB if possible.You just create it as if it's a hard disk, quite easy. Though if your PC is old it'd probably only have USB 1.1 which is really slow, probably wouldn't feel much quicker than a floppy! But it would have more space and wouldn't have to mess around with so many floppies.

---

### Post by princerameses on 2011-04-25
I tried doing the fdimage thing, I did not understand it. 

And, yes, that's what I meant. The second one. 
And am I getting this correct: I format the floppy as bootable DOS then delete all the files it put on it?

---

### Post by btindie on 2011-04-25
You don't need to format it as a bootable floppy. The first disk image already has the bootsector implanted at the beginning so when you write it to the floppy it'll overwrite everything that's on there.

As for the second disk, that's simply a data disk which will be read in the boot process.

DISK1.IMG is to a floppy disk what an [ISO]("http://en.wikipedia.org/wiki/ISO_image") is to a CD. It's a raw image that includes the bootsector and filesystem.

Floppies are a slightly different beast to hard disks. The standard format is 1.44MB but they can be formatted to 1.68MB and even more. The floppies you have should already be in the 1.44MB format, all it needs is a filesystem. If you're using Windows then just do a 'Quick Format' (mkdosfs under Linux) without coping system files etc, this will create a blank filesystem on the disk. You can then copy DISK2.TGZ to it.

With the first floppy disk you create based on DISK1.IMG, when you put it in under DOS/Windows/Linux it will be unrecognised as it doesn't contain a valid file system. It's basically the kernel with some header information which is only usable as a boot disk. Whereas with the 2nd one, it's just a normal data disk.

EDIT: If you were to format the disk then delete the files from it, it may not delete all files (system/hidden) thus not freeing up enough space.

---

### Post by princerameses on 2011-04-25
Ok, I formatted them through DOS. And put #2 on. 

But when I try to use the code fdimage disk1.img a: it says the command is not recognised. I tried rawrite and rawritent too. Is that all I type? (open DOS and type fdimage disk1.img a:?

---

### Post by princerameses on 2011-04-25
Well, I got the program "rawwrite" and wrote the image to the disk, now I just have to get into BIOS and make floppy boot first. And I can't remember how to get in there..

---

### Post by oldfred on 2011-04-25
Most computers it is the del key, but some used different f keys. I used to just start hitting keys until something worked. But the first BIOS screen should say which key to use.

---

### Post by princerameses on 2011-04-25
I remember it being a nightmare, the first time I was trying to get in BIOS, to find the correct key. In some forum someone found it for me, but I don't remember which site it was on.. :(

And it doesn't say, all there is is a flashing square in the upper right corner. That's when you press.. something. I'll try delete.


It says "keyboard error" when I press delete. I think it said the same when I tried esc.

---

### Post by Joe of loath on 2011-04-25
> **princerameses said:**
> [COLOR="DarkOrchid"]**Yes, but I've tried most of the other lite ones.. They either wouldn't boot, or lagged/ froze/ crashed. DSL worked pretty well, but only an older version would work, and I couldn't get flash to work. I at least want to give this one a try. **[/COLOR]

You're not going to get flash to work on an OS with no GUI :lol:

Your experiences point towards a memory issue, where in the world are you? If you're in Europe I can send you some 64mb memory modules, that way you'll be able to run a more modern operating system without it crashing.

---

### Post by princerameses on 2011-04-25
Whoa, that extremely nice of you to offer ^^, but no, I'm in the US. 

And AHH, really? so theres no way to get flash/gui? :(

---

### Post by princerameses on 2011-04-25
[http://www.minimalinux.org/ttylinux/downloadPC.html](http://www.minimalinux.org/ttylinux/downloadPC.html)

Ok, which one do I choose here? :)

---

### Post by Joe of loath on 2011-04-25
No GUI in that one either :p

Tried Debian? Just do a CLI install, then chuck on openbox or fluxbox.

---

### Post by princerameses on 2011-04-25
Really? :( I can install GUI though, can't I? 

How do I do that? And how do I change the desktop environment with out loading the default? And want to link me to the website? :)

What about reactOS?

Or anything here under 50 MB? [http://ubuntuforums.org/showthread.php?t=575456](http://ubuntuforums.org/showthread.php?t=575456)

---

### Post by Joe of loath on 2011-04-25
[www.debian.org](www.debian.org)

Install it, when it asks you what you want to install, uncheck 'Desktop environment'. Then when it's installed, reboot, and hook it up to the internet via cable. Then run:

su
(type root password)
apt-get update
apt-get upgrade
apt-get install openbox

Then type startx, and you'll have a basic GUI. Anything else can be installed on there as you would on Ubuntu, with the terminal.

---

### Post by princerameses on 2011-04-25
I'll try it when I get up. Do I choose the i386 one?

And.. 

You never answered my question about installing GUI. :)
Would be nice if I could get basic linux with GUI. =]

If there are any other options that would work for my computer, please let me know, though I must have tried most of them.

---

### Post by Joe of loath on 2011-04-25
Yup, i386.

I don't think BasicLinux has a package manager. Even if it does, it's not GUI centric.

---

### Post by princerameses on 2011-04-26
Ok, I installed openbox through the terminal commands, but the 'startx' command was not found. I even tried 'start x' and some others.. but all weren't found. 
So I powered off manually and now I'm back to the same place I was, and it appears openbox is now not installed? (It's waiting for a command)

Also, is opennox the lightest there is? I would like to get as lite as possible. What does Damn small linux use? That worked pretty fast.

---

### Post by Joe of loath on 2011-04-26
Maybe Debian doesn't install X as a dependancy.

Run as root:

apt-get install xorg-xserver openbox xinit

---

### Post by princerameses on 2011-04-26
Unable to locate xorg-xserver

:(

---

### Post by Joe of loath on 2011-04-26
Sorry, it's simply xorg. I've not used Debian for a little while.

---

### Post by princerameses on 2011-04-26
Ok, that worked. Now Which browser would be best to get? It can be horrid looking and a pain as long is it's very slim and will support flash. Speaking of which, do I have to get flash too? How do I do that?

And am I supposed to have nothing on my desktop? All it is us a black screen; no bars or anything. I right click and have only a few options. This is fine if it'll work.

---

### Post by btindie on 2011-04-26
> **princerameses said:**
> What does Damn small linux use? That worked pretty fast.
DSL uses [fluxbox]("https://help.ubuntu.com/community/Fluxbox").

---

### Post by princerameses on 2011-04-26
No, it wasn't fluxbox.. I don't think, unless they really made it look defferent, because I can't stand fluxbox. -_- It looked more like JWM or something. I know it had the option for fluxbox though.

---

### Post by princerameses on 2011-04-26
[COLOR="Magenta"][B]What about Kazehakase, or dillio? *is waiting for suggestions* :)
And I 'm not sure which ones I CAN get.[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-26
> **princerameses said:**
> Ok, that worked. Now Which browser would be best to get? It can be horrid looking and a pain as long is it's very slim and will support flash. Speaking of which, do I have to get flash too? How do I do that?

And am I supposed to have nothing on my desktop? All it is us a black screen; no bars or anything. I right click and have only a few options. This is fine if it'll work.

For a browser, I'd recommend netsurf or Midori. Midori supports javascript and flash, but will be slower.

Flash isn't a good idea on a 330Mhz box. Not unless you fancy waiting for 10 minutes for a page to load, and watching youtube videos at half a frame per second.

The desktop is meant to be like that, yes. If you want a panel you can install and run lxpanel.

---

### Post by princerameses on 2011-04-26
[COLOR="Purple"][B]Oh, ok. And yeah, that's what I want, though. Is for flash to go slow so I can get a certain score on a game, lol.
What about Kasahakase? And how might I set a background image? The black is a tad annoying.[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-26
Not sure on Kasahakase, it uses FF's browser engine, Gecko, which means it will be a memory hog. By all means try it out though, as long as you have swap the machine won't lock up completely :p

To change the background you're looking at a program called nitrogen. 

[https://wiki.archlinux.org/index.php/Nitrogen](https://wiki.archlinux.org/index.php/Nitrogen)

Install with apt-get install nitrogen, run using the commands in the arch wiki.

---

### Post by princerameses on 2011-04-26
[COLOR="Purple"]**Ok, I got kazehakase :) And it's working, but I'm scared to click a link before the page has loaded completely. So, well see how it handles flash. D: I also may try links2 and the one you suggested for non flash uses.  But how do I get flash, now? And how do I adblock with CSS with kazehakase? I found a page that expained what to do, but I don't know how to do it with this OS/ desktop enviornment..**[/COLOR]

---

### Post by kiyop on 2011-04-26
> **princerameses said:**
> [COLOR=Purple]** But how do I get flash, now? **[/COLOR]

I am not sure, but  I succeeded watching Flash such as in Youtube the other day.

Edit /etc/apt/sources.list and add "contrib non-free" after "main".

```
# apt-get update
# apt-get install flashplugin-nonfree libcurl3-gnutls
```

Download "install_flash_player_10_linux.tar.gz" from [http://get.adobe.com/jp/flashplayer/](http://get.adobe.com/jp/flashplayer/)

```
~/Desktop# tar -xvf install_flash*.tar.gz
```

```
~$ mkdir ./.mozilla/plugins
```

Copy generated libflashplatyer.so into ~/.mozilla/plugins.
```
~/Desktop$ mv libflashplayer.so .mozilla/plugins/
```

Open Iceweasel. I&#12288;could watch Flash.

I am not familiar with Kazehakase.

---

### Post by princerameses on 2011-04-26
[COLOR="DarkOrchid"][B]Hmm, thanks, but I don't think I could handle ice-weasel. :(
Also, the fact that the screen res is like 600x 800 or something like that is really annoying. -_- and I don't have the option to zoom out on this browser. [/B][/COLOR]

---

### Post by kiyop on 2011-04-26
Do you know that Iceweasel is almost the same as FireFox?

And you can easily change resolution of your monitor if you search by google.
Good luck!!

[http://www.google.co.jp/#&source=hp&biw=994&bih=502&q=debian+resolution+monitor&fp=fcf9ab66368543ac](http://www.google.co.jp/#&source=hp&biw=994&bih=502&q=debian+resolution+monitor&fp=fcf9ab66368543ac)

If you use debian, you can easily install iceweasel:
```
# apt-get install iceweasel
```...
EDIT: Excuse me. :(
Your computer does not have enough memory, does it?
You think Flash movie will move veery slooowly with FireFox (iceweasel), don't you? 
I thought that you do not know how to use iceweasel.

---

### Post by princerameses on 2011-04-26
Well, I think the video card is too old to support a higher res. >.>

And yes, but I don;t think I can handle FF either. xD

How would I uninstall it if it's too big?

---

### Post by kiyop on 2011-04-26
What kind of video card?

You can uninstall packages like:
```
# apt-get remove (package name)
```or
```
# apt-get purge (package name)
```You can memorize what packages are installed when you install via "apt-get install", because log is shown.
You can drug the log (package names) and middle click to paste into some text editor.

You can install GUI text editor like leafpad by
```
# apt-get install leafpad
```

You can get help message on some command by 
```
$ man (command)
```
like "man apt-get"

---

### Post by princerameses on 2011-04-26
I'm not sure what the video card is.. Can I probe for it? Also, [this]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00191381&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=92982")is my computer.

But on damn small linux, I had 1024 x 768. It's done this with other computers too.. I think because of this e-machines flat panel monitor; it can't handle it or something..

---

### Post by princerameses on 2011-04-26
[COLOR="Purple"][B]Ok, got iceweasel. :) And it's working about the same as kazehakase.. And I can zoom out, so I zoomed way out and just made the default font bigger and disabled pages from using their on font. :)
Now I will attempt to get flash.[/B][/COLOR]

---

### Post by Slim Odds on 2011-04-26
```
sudo apt-get install newcomputer
```

---

### Post by Joe of loath on 2011-04-26
> **Slim Odds said:**
> ```
sudo apt-get install newcomputer
```

Hey, we aren't all rich, some of us have to make do as best we can.

Although, I did find a half dozen laptops in a dumpster with a higher spec than the OP's machine...

---

### Post by princerameses on 2011-04-26
[COLOR="DarkOrchid"]Lol. :P It would be like finding gold if I found a bunch of laptops that had been discarded. xD
Any chance I could *easily* get my wireless USB adapter to work? I only have one working ethernet cable and other people are getting up and need the wireless. (I had to unplug the cable from the router) So if I could get wireless going that would be wonderful. :)

I worked for like 20 minutes to get an ethernet cable from under a bunch of heavy boxes/ behind wall posts only to find it doesn't work. :mad: It may have been from all the yanking. :(.[/COLOR]

---

### Post by Joe of loath on 2011-04-26
Depends what you think of as 'easy'. What encryption do you run on your network?

---

### Post by princerameses on 2011-04-26
[COLOR="DarkOrchid"][B]I have no close neighbors, so no encryption. :)

The adapter is a WUSB54G V. 4
It works right off when plugged in on most new distros, but since it's all minimal in this case, I doubt it would work by plug & play.. [/B][/COLOR]

---

### Post by Joe of loath on 2011-04-26
Ah, that's easy, then.

If it's plug and play on 10.04, it will be plug and play on Debian, as they use the same kernel. All the drivers are in the kernel :D

As root, run:

iwconfig (interface) essid (network name)
wait a few seconds
dhclient (interface)
wait a few seconds

Then you're done :D You can write it into a script to run at boot if you wish.

---

### Post by princerameses on 2011-04-26
How do I make it start at boot? :)
What's the interface? The adapter name? Sorry, there's some simple stuff like this that I don't know. :(

---

### Post by Joe of loath on 2011-04-26
If you plug it in and type iwconfig, it will be wlan0 or eth1 or something.

To make it start at boot, create a file called wifi.sh or something, and write in it:

iconfig essid (interface) (network name)
sleep 5
dhclient (interface)

Then save it, and run (As root)

update-rc.d (script name) defaults.

---

### Post by princerameses on 2011-04-26
[COLOR="DarkOrchid"]Oh, and how can I get Dillo browser and repositor 0 B or something. It said I needed that when I tried to get one of the browsers.[/COLOR]

---

### Post by princerameses on 2011-04-26
[COLOR="DarkOrchid"]It said iwconfig command was not found.[/COLOR]

---

### Post by Joe of loath on 2011-04-26
Ah, of course. The wireless tools aren't installed by default.

apt-get install wireless-tools

---

### Post by princerameses on 2011-04-26
:P Okay, I'll try that.

---

### Post by princerameses on 2011-04-26
[COLOR="DarkOrchid"]Ok, it's either just not working, or I didn't do it right. What do I type in again? iwconfig wlan0 then what? What's the SSID? [/COLOR]

---

### Post by princerameses on 2011-04-26
> **kiyop said:**
> I am not sure, but  I succeeded watching Flash such as in Youtube the other day.

Edit /etc/apt/sources.list and add "contrib non-free" after "main".

```
# apt-get update
# apt-get install flashplugin-nonfree libcurl3-gnutls
```

Download "install_flash_player_10_linux.tar.gz" from [http://get.adobe.com/jp/flashplayer/](http://get.adobe.com/jp/flashplayer/)

```
~/Desktop# tar -xvf install_flash*.tar.gz
```

```
~$ mkdir ./.mozilla/plugins
```

Copy generated libflashplatyer.so into ~/.mozilla/plugins.
```
~/Desktop$ mv libflashplayer.so .mozilla/plugins/
```

Open Iceweasel. I&#12288;could watch Flash.

I am not familiar with Kazehakase.

[COLOR="Magenta"][B]
How do I get to my home folder to do this?[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-26
iwconfig wlan0 essid (network name).

To get to you home folder, type cd ~.

---

### Post by princerameses on 2011-04-26
[COLOR="Purple"][B]So I type: 
```
iwconfig wlan0 essid linksys
``` 
Is that right?


And I did cd ~ but it did nothing.
[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-26
that's correct.

You're probably in your home directory already.

---

### Post by princerameses on 2011-04-26
[COLOR="Purple"]Nothing came up.. 
I'll try tomorrow. :)[/COLOR]

---

### Post by Joe of loath on 2011-04-26
Nothing will come up. Once you run it, run dhclient wlan0, and you'll have internet hopefully.

---

### Post by princerameses on 2011-04-27
[COLOR="DarkOrchid"]I meant for the home folder. :) 

I type cd ~ and nothing happens...


And.. I got the tar.gz for flash.. but what do I do now? I tried using *kiyop's* instructions, but it said "no such file or directory".[/COLOR]

---

### Post by Joe of loath on 2011-04-27
If nothing happens you're in your home directory already; it's where the terminal starts when you open it.

If it's saying that you got the file name wrong, or a directory hasn't been created.

---

### Post by princerameses on 2011-04-27
[COLOR="DarkOrchid"]Oh, well how do I get to my documents all all that?  

And how do I change my /etc/apt/sources.list? 


I'm trying to add [this]("http://debgen.simplylinux.ch/generate.php")[/COLOR].

---

### Post by Joe of loath on 2011-04-27
All your stuff is in your home folder. The 'Documents' folder is created by Gnome in Ubuntu. If you want to make one, just use mkdir.

edit /etc/apt/sources.list as root. You can use nano in the terminal, or install leafpad and use that in the GUI.

---

### Post by kiyop on 2011-04-27
> **princerameses said:**
> [COLOR=DarkOrchid]how do I change my /etc/apt/sources.list? [/COLOR]

```
su
```Type password for root.
```
nano /etc/apt/sources.list
```... Oh! You do not know how to use nano, do you?
[http://www.gentoo.org/doc/en/nano-basics-guide.xml](http://www.gentoo.org/doc/en/nano-basics-guide.xml)

If you want to edit on GUI text editor,
```
apt-get install leafpad
leafpad /etc/apt/sources.list
```If you always ask how to do what you want, somebody evil-minded may tell you wrong and terrible thing.

Learning by yourself or trying to find some way to solve is better.

EDIT: I did not noticed that Joe of loath had post the above #63. Excuse my duplication.

---

### Post by princerameses on 2011-04-27
[COLOR="DarkOrchid"]

[QUOTE=kiyop]If you always ask how to do what you want, somebody evil-minded may tell you wrong and terrible thing.

Learning by yourself or trying to find some way to solve is better.
[/QUOTE]

Yeah, but How do I learn all this terminal mumbo-jumbo? And everything else? I *try* to google what I need first, but don't usually turn up what I need or it doesn't work.

As for people that may give me a code to do something bad, well I can usually identify what I'm typing.. so if I saw something totally unrelated to what I am trying to do, I'd probably catch it. ;)

And ty, will try that shortly.
[/COLOR]

---

### Post by Joe of loath on 2011-04-27
Learn it by using it :D For example, if you google 'linux connect to wifi network from terminal', you'll find info on how to do it.

---

### Post by princerameses on 2011-04-27
[COLOR="Purple"][B]I try, but a lot of times I get results for a specific distro, and it doesn't work for mine..

Anyways, about my source.list... This is what I got in leafpad:
```
# 

# deb cdrom:[Debian GNU/Linux 6.0.1a _Squeeze_ - Official i386 NETINST Binary-1 20110320-15:03]/ squeeze main

#deb cdrom:[Debian GNU/Linux 6.0.1a _Squeeze_ - Official i386 NETINST Binary-1 20110320-15:03]/ squeeze main

deb http://ftp.us.debian.org/debian/ squeeze main
deb-src http://ftp.us.debian.org/debian/ squeeze main

deb http://security.debian.org/ squeeze/updates main
deb-src http://security.debian.org/ squeeze/updates main

# squeeze-updates, previously known as 'volatile'
deb http://ftp.us.debian.org/debian/ squeeze-updates main
deb-src http://ftp.us.debian.org/debian/ squeeze-updates main
```

Now would you be so kind as to add lines for the repository I need for flash and dillo, please? Then I could just copy and paste it over in my source.list. Thanks.[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-27
There aren't any repos with flash in (that I know of), just install it manually as detailed above.

Dillo is only in the testing release at the moment, but may be in debian backports.

---

### Post by princerameses on 2011-04-27
[COLOR="Purple"][B]Really? Cause I found a page to get one.. Anyhew, how does this look?
```

deb http://ftp.us.debian.org/debian/ squeeze main contrib non-free
deb-src http://ftp.us.debian.org/debian/ squeeze main contrib non-free

deb http://security.debian.org/ squeeze/updates main contrib non-free
deb-src http://security.debian.org/ squeeze/updates main contrib non-free

deb http://b.berteau.free.fr/ sarge main
```[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-27
sarge? That's ancient :lol:

Change it to squeeze, but beware the repository might be dead in the water or gone.

---

### Post by princerameses on 2011-04-27
> **kiyop said:**
> I am not sure, but  I succeeded watching Flash such as in Youtube the other day.

Edit /etc/apt/sources.list and add "contrib non-free" after "main".

```
# apt-get update
# apt-get install flashplugin-nonfree libcurl3-gnutls
```

Download "install_flash_player_10_linux.tar.gz" from [http://get.adobe.com/jp/flashplayer/](http://get.adobe.com/jp/flashplayer/)

```
~/Desktop# tar -xvf install_flash*.tar.gz
```

```
~$ mkdir ./.mozilla/plugins
```

Copy generated libflashplatyer.so into ~/.mozilla/plugins.
```
~/Desktop$ mv libflashplayer.so .mozilla/plugins/
```

Open Iceweasel. I&#12288;could watch Flash.

I am not familiar with Kazehakase.

[COLOR="DarkOrchid"][B]Ok, I got flash  think, now I just have to do this:
```
~/Desktop# tar -xvf install_flash*.tar.gz
```

```
~$ mkdir ./.mozilla/plugins
```

Copy generated libflashplatyer.so into ~/.mozilla/plugins.
```
~/Desktop$ mv libflashplayer.so .mozilla/plugins/
``` But those commands did not work.
[/B][/COLOR]

---

### Post by Joe of loath on 2011-04-27
> **princerameses said:**
> [COLOR="DarkOrchid"][B]Ok, I got flash  think, now I just have to do this:
```
~/Desktop# tar -xvf install_flash*.tar.gz
```

```
~$ mkdir ./.mozilla/plugins
```

Copy generated libflashplatyer.so into ~/.mozilla/plugins.
```
~/Desktop$ mv libflashplayer.so .mozilla/plugins/
``` But those commands did not work.
[/B][/COLOR]

Try it again, but inject a little flexibility into your thinking. Perhaps the file doesn't have the same name? Perhaps you're not in the same directory?

---

### Post by kiyop on 2011-04-27
```
gzip -dc *.tar.gz|tar xvf -
```
or so may help.

---

