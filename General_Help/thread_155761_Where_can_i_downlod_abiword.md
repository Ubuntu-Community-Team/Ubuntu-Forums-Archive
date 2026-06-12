---
title: "Where can i downlod abiword"
date: 2006-04-05
forum: General Help
---

### Post by junglemike on 2006-04-05
Hi all. I have slow and old laptop. Openoffice is really handy  - no doubt about it, but it takes 3-5 minutes to open empy worksheet on my machine. 
Q1:
I heard that abiword is much lighter. Any tips on where can i download it , and how can I install it?
Q2:
Can anybody recommend some light alternative to excel (i mean the part in openoffice which is like excel)
Q3:
HOw and where can i find specific application.
For example I wanted to download Mplayer, i tried using 
sudo apt-get install mplayer
but it cannot be found. Any Idea where can i find it.

Sorry for silly questions. I'm new to Linux. Guess every1 start sometime...

---

### Post by Sef on 2006-04-05
> I heard that abiword is much lighter. Any tips on where can i download it , and how can I install it?

To Download Abiword:

1) Command line: Open the terminal  Applications > Accessories > Terminal and type this:   sudo apt-get update   then   sudo apt-get install abiword

2) Synaptic: System > Administration > Synaptic Package Manager.  Then in search type abiword, then highlight it, then click on Apply.

3) Add Applications:  Applications > Add Applications > Office > more programs >click on abiword > click apply >click apply again.

> Sorry for silly questions. I'm new to Linux. Guess every1 start sometime...

Not silly questions.  As you said you got to start somewhere.  So did we all.

---

### Post by localzuk on 2006-04-05
You need to enable repositories. Take a look at [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

Abiword is available through apt also, as is mplayer. If you want to be able to use video formats of various types, take a look at:[https://wiki.ubuntu.com/Multimedia](https://wiki.ubuntu.com/Multimedia) and specifically [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for information.

I'm not to sure about a light weight spreadsheet program. You could try gnumeric as that is about the only one I know of.

---

### Post by localzuk on 2006-04-05
Note that you only need to do one of these commands, not all of them :)

---

### Post by gingermark on 2006-04-05
I'm gonna assume you're using Kubuntu, and add a few things.

Do K-Menu --> System --> Konsole. This brings up KDE's terminal emulator.

Type 'kdesu /etc/apt/sources.list' and press enter.
Enter your password when prompted.

Remove any '#'s that appear at the beginning of any lines. This will enable more repositories (needed for MPlayer).

Save the file, close the text editor. (EDIT: localzuk beat me to that part).

Again in Konsole, now type 'sudo apt-get update'.

Now for abiword: sudo apt-get mplayer abiword.
For MPlayer: sudo apt-get install mplayer.

This all uses a process call apt-get. There is a GNOME frontend called Synaptic (as mentioned above). In KDE the application is called Adept.

K-Menu --> System --> Adept.

In this app you can search for new applications, and select for them to be installed.

---

### Post by junglemike on 2006-04-05
Thanks guys, you're really helpful.
2Sef:
First option worked fine for me for installing abiword. thanks
BTW, i'm using XFCE4

2localzuk & gingermark:
I uncommented any # eintries in /etc/apt/sources.list file.
Than i made ```
 sudo apt-get update
```
When i tried to install mplayer same way i installed abiword using: ```
sudo apt-get install mplayer
```
I got "couldn't find the package mplayer"
So i guess i have old repositories , maybe because i'm using 5.04 version.

Q:
How can i  find that specific repository with appropriate link, where mplayer package presents?

---

### Post by junglemike on 2006-04-05
Ps.:
Just installed abiword - Wow, it's fast! Lauched before i pressed the button :-)
Where can i find some excel-like program? Pleeeeez


**2localzuk**
I tried ```
sudo apt-get install gnumetric
```
It said couldn't find the package

---

### Post by localzuk on 2006-04-05
In answer to both your posts (gnumeric and mplayer). It may be due to you using Hoary (5.04) so take a look at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) which is a comprehensive guide for that release.

I would advise upgrading to Breezy (or Dapper when it comes out in June) as this is the current stable and most up to date version (Dapper will be in June). It should not slow down your computer any more than Hoary already does. It will ensure that you have a longer security update lifespan though.

---

### Post by gingermark on 2006-04-05
In Hoary use an application called "Kynaptic" to search for packages and install them.

MPlayer used to release kernel specific versions - for example, if you're using the normal x86 version I think you'll need to type "sudo apt-get install mplayer-386", or as I say, use Kynaptic.

I think the gnumeric problem might just be a typo (you said you typed "sudo apt-get install gnume**t**ric" - lost the T).

---

### Post by megabyte405 on 2006-04-19
Starting "synaptic" in a terminal is the easiest way to install programs - you can do a search for mplayer in there.  There might be some issues with patents that keep it away from you, however, it did show up on my system, where I have both universe and multiverse enabled.

For AbiWord, you actually shouldn't have needed to edit your sources - it is in Main.

Gingermark is right - for Gnumeric, just lose the t, it is also in main.

Good luck!

-- Ryan

---

### Post by openmind on 2006-04-19
[quote=Sef] <snip>Not silly questions.  As you said you got to start somewhere.  So did we all.[/quote] 
  It's attitudes and responses like this that make this the best Linux Forum today, and is contributing to the success of Ubuntu Every Day.    =D>=D>=D>

---

