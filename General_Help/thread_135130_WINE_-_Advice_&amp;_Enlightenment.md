---
title: "WINE - Advice &amp; Enlightenment"
date: 2006-02-23
forum: General Help
---

### Post by Ingla on 2006-02-23
Hi.

I've never tried to use Wine, but need to run Internet Explorer for a couple of sites. These include online banking sites...not just browsing...so, I need an IE capability to peform actions such as log ins.

I tried running Opera, set tp identify itself as IE. It could view the site, but the log-in and submit buttons would not function. Apparently this requires real IE functionality.

1. I've seen various posts discussing all kinds of problems with Wine, some claiming it doesn't work or won't work for them.

Before I start making all kinds of hard-to-undo mistakes, I'd very much appreciate a general run down of what Wine is and how it works. For example, do I have to start it or does it run in the background at boot. Does it have a GUI? Special locations where I need to install IE or other programs? Is it a command line only program?

How do I go about installing IE and how do I run it (I've noticed there's a Firefox extension that is supposed to be able to run IE inder Wine from a Firefox tab and configure a bookmark to open in IE).

Once Wine and IE are installed, does IE run from a menu item or what?

2. I was planning on installing Wine with Auotmatix. I don't know what that will install exactly or how to proceed from there. Can anyone tell me if this is the best way to go?

If anyone can comment on any of this and, preferably, give me some sort of walk-through (on the most basic level possible), your help will be greatly appreciated.

Thanks very much.

---

### Post by Sutekh on 2006-02-23
[QUOTE=Ingla]Before I start making all kinds of hard-to-undo mistakes, I'd very much appreciate a general run down of what Wine is and how it works.[/QUOTE]
 - Wine - **W**ine **i**s **n**ot an **e**mulator.  Wine is like a compatibilty layer between Windows programs and the Linux operating system.

 - I think this will explain things better than I could [http://www.winehq.com/]("http://www.winehq.com/")


[QUOTE=Ingla]For example, do I have to start it or does it run in the background at boot. Does it have a GUI?[/QUOTE]
 - Wine is installed as a program.  When you want to use it, you run it.  There is a GUI interface for configuring wine
```
winecfg
```
But for using wine you must use the **wine** command, either from the command line (terminal) or through a launcher.

 - In general a program is run using wine, in the following way
```
wine /media/cdrom0/setup.exe
```
 - Here **wine** is used to run the **setup.exe** that is found in the **/media/cdrom0** folder.  All you need to do is use the command **wine** and specify the location of the executable (.exe)


[QUOTE=Ingla]How do I go about installing IE and how do I run it (I've noticed there's a Firefox extension that is supposed to be able to run IE inder Wine from a Firefox tab and configure a bookmark to open in IE).[/QUOTE]
 - I think you should check this link out for installing IE with Wine.

[http://www.tatanka.com.br/ies4linux/]("http://www.tatanka.com.br/ies4linux/")


 - Once you've set this up, you can create a menu item to run IE, very easily.

 - If you would like to create a menu entry, simply open up the **Application Menu Editor** found in the Applications -> System Tools menu.

 - From here you can choose to add a new entry to the menu of your choice.  You will be given the option of choosing the title, description, etc.  The only important option one is the **command**.

 - If you setup IE using the link - [ies4linux]("http://www.tatanka.com.br/ies4linux/en/instructions") and wish to use run IE, all you need to specify in command is **ie6** or **ie55** or whatever version you wish to run.


[QUOTE=Ingla]I was planning on installing Wine with Auotmatix. I don't know what that will install exactly or how to proceed from there. Can anyone tell me if this is the best way to go?[/QUOTE]
 - I can run you through it right here and now

 - Open a terminal window (from the Menu; Applications -> Accesories -> Terminal), and issue the commands
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo gedit /etc/apt/sources.list
```- This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

- To install wine you will need the wine repository; add these lines to your sources.list
```
deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
```
- Then save the file and exit.

- Update the repositories using
```
sudo apt-get update
```

- Finally you can install wine using
```
sudo apt-get install wine
```
 - That's it!  Let us know if you need to know more :D 



 - Lastly, what kind of dodgy bank only works with IE?  You should send an email of complaint. :rolleyes:

---

### Post by Ingla on 2006-02-23
Thank you very much.

1. The installation doesn't sound bad. I've heard, however, that it's hard to configure. I don't know, of course, what needs configuring. Can you comment on that?

2. Also, someone just told me you need a license to run IE (I'm not dual booting...this hard drive has only Linux on it). I own a legal copy of Windows, but I've had that for years and don't know any registration numbers or anything (it was registered once upon a time with MS for support purposes but I haven't used any of that for years...just have the original serial number for installing.

Do you know anything about that?

Thanks very much.

---

### Post by Sutekh on 2006-02-23
> **Ingla]Thank you very much.

1. The installation doesn't sound bad. I've heard, however, that it's hard to configure. I don't know, of course, what needs configuring. Can you comment on that?[/QUOTE]
 - My experience with wine, in terms of the programs I use with it, is pretty limited.  The main programs I have used wine to run have been DVD Decrypter and some software for my portable media player.  The configuration program said:**
> WineHQ - Wine User's Guide - Using Winecfg[/URL]


 - Perhaps some of the harder aspects are when using Windows Libraries (.dll).  There is a section in the Wine User's Guide (from the WineHQ site) that deals with this.  

[WineHQ - Wine User's Guide - Library Settings]("http://www.winehq.com/site/docs/wineusr-guide/config-wine-main#AEN217")


 - I think in general the problems that people have are with configuring specific programs not wine itself.  There is an application databse that tracks compatability between wine and specific programs.  Some of the more documented programs even have tips, howtos and bug reporting.

[Wine Application DB]("http://appdb.winehq.org/")

 - Check out the entry for IE.  [Wine Application D - Internet Explorer]("http://appdb.winehq.org/appview.php?appId=25")

 - After having a *brief* look, it seems that IE5.5 works okay with Wine 0.9.7.

 - IEs4Linux may work differently to setting up IE yourself in wine.  It would be nice to hear from someone who has used IEs4Linux


[QUOTE=Ingla]
2. Also, someone just told me you need a license to run IE (I'm not dual booting...this hard drive has only Linux on it). I own a legal copy of Windows, but I've had that for years and don't know any registration numbers or anything (it was registered once upon a time with MS for support purposes but I haven't used any of that for years...just have the original serial number for installing.

Do you know anything about that?

Thanks very much.
 - Hmm, I'm afraid I don't have much to offer on this.  I expect that the IEs4Linux program handles this issue, if it is actually an issue.  Again hopefully someone who has used IEs4Linux can chip in.

---

### Post by dcstar on 2006-02-24
[QUOTE=Ingla]
.......
How do I go about installing IE and how do I run it (I've noticed there's a Firefox extension that is supposed to be able to run IE inder Wine from a Firefox tab and configure a bookmark to open in IE).

Once Wine and IE are installed, does IE run from a menu item or what?
......[/QUOTE]
The IE View Extension requires a script to be created to run in Linux - but once you have it set up (and IE working under Wine), then you just right-click a web page in FF and select "View this page in IE". I have it working 100% with my FF/IE setup.

---

### Post by Stickittotheman on 2006-08-06
IE used to be on my windows desktop for YTMNDs before they patched it for FF... it was labeled "teh suxxy intranetz"..

---

### Post by nkayesmith on 2007-01-15
> **Ingla said:**
> 
2. Also, someone just told me you need a license to run IE (I'm not dual booting...this hard drive has only Linux on it). I own a legal copy of Windows, but I've had that for years and don't know any registration numbers or anything (it was registered once upon a time with MS for support purposes but I haven't used any of that for years...just have the original serial number for installing.

Thanks very much.

No problem: No serial numbers will be asked for - the EULA just tells you to have a valid license.

---

