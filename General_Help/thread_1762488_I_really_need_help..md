---
title: "I really need help."
date: 2011-05-19
forum: General Help
---

### Post by Baijix on 2011-05-19
Hi there. I'm really new to the Linux scene, and I really feel like an idiot trying to run an .exe file. I am amazing at Windows, but when it comes to Linux, fail. So, I've been trying to run an .exe file.

I wanted to download Internet Download Manager, and I did. But when I tried to run the .exe file, it wouldn't open. So, I searched on alot of forums just to find an answer. I'll show you what I'm trying to do.

In the Terminal:
/home/baijix/Desktop/idman606b3.exe

And then, I get an error saying:
/home/baijix/Desktop/idman606b3.exe: Permission Denied

So, I login as "root user." But, I still get the error. Currently, I'm downloading Wine, but my Internet is slow.

So, what I'm trying to do is how do I run an .exe file. Help?

---

### Post by ysangkok on 2011-05-19
when you get hold of Wine, you run it like: "wine notepad.exe" (or whatever).

If it's a .NET program you can run it with Mono like "mono dotnetprogram.exe"

EDIT: I'd really **recommend finding another** download manager though. Look here: [http://en.wikipedia.org/wiki/Template:Download_managers](http://en.wikipedia.org/wiki/Template:Download_managers) . The ones listed as "cross-platform" or "Unix" are usable on Linux. I use *DownThemAll!* (for Firefox) and it works great for me. Lots of people use JDownloader and like that too. It requires Java though, and is therefore probably a bit hard to get working than DownThemAll (since Firefox is included with Ubuntu).

EDIT2: You normally shouldn't use the root user for anything other than installing system-wide applications and maintenance. Since Wine emulates the whole Windows system, it's never necessary to be root when running Wine.

---

### Post by ghostborg on 2011-05-19
By default the file permission is not allowed to execute.
You can use the file browser Nautilus to locate the file and right click on it and select Properties. A Properties window should pop-up with some tabs. Select the Permissions tab and check box the  execute box.

---

### Post by Stephen Morgan on 2011-05-19
You can make a file executable from the command line with the 

```
chmod +x
```

command.

But .exe files, other than Mono programmes, will need to be run through WINE so changing the executable permission isn't necessary.

---

### Post by Morbius1 on 2011-05-19
And just to add a bit of confusion to this topic, Wine is incapable of determining if a given file has a Linux executable bit set. The problem is "cautious-launcher". To fix that please see this: [http://ubuntuforums.org/showthread.php?t=1747138](http://ubuntuforums.org/showthread.php?t=1747138)

---

### Post by sanderd17 on 2011-05-19
RULE NUMBER 1: Do not get your software from a website.

The software center in Ubuntu (and all other popular distributions) is fantastic. You can find any software you like (apart from games). 

If I just search "download manager", then I get five responses. Look at the descriptions and decide.
But I don't use a download manager as a separate program though, I use it integrated in firefox as an add-on, I use Down-them-all.

The only software you can get of a website is one of the following three:
[LIST]
[*]brand new and therefore very buggy
[*]old and unsupported
[*]or for windows and will not work on Linux without a lot of work
[/LIST]

So you don't want to install anything from a website unless you have a brand new computer, with brand new hardware, and a brand new driver is not included by default, or something like that.

---

### Post by oldos2er on 2011-05-19
I checked the Wine app database ([http://appdb.winehq.org/](http://appdb.winehq.org/)), there are older versions of IDM, all of which are rated 'Garbage,' so I don't think there's much chance of getting this app running.

No Windows apps run natively on Linux, but some may run with Wine. You can save yourself some trouble by checking the Wine app database first. To find Linux app equivalents, see [http://www.linuxalt.com/](http://www.linuxalt.com/) , _[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)_ , and [http://www.osalt.com/](http://www.osalt.com/)

---

