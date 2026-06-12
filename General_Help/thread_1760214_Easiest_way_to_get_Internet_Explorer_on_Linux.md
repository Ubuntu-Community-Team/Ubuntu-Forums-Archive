---
title: "Easiest way to get Internet Explorer on Linux"
date: 2011-05-16
forum: General Help
---

### Post by Curse on 2011-05-16
I'm trying to convert my GF's brother to Linux, but he requires IE for a school website to work.

I've tried ies4linux, which doesn't work because it is abandonware as I later learned. 

I found [this](http://forums.gentoo.org/viewtopic-t-830877-start-0.html) and ran 

```
sh winetricks ie6
```

Which seemed to install IE, but I can't find how to run it anywhere.

Help? :/

---

### Post by Mark Phelps on 2011-05-16
Basically, there is no way to get IE versions newer than 6 working fully in Linux, period.

WineTricks and Crossover for Linux have features to try to force the install of IE7 or IE8, but from the reports I've seen, the results are not very good.

Sorry, but if you MUST use IE, especially version 9, then you really have no choice other than to stay with Windows, or to install Windows in a Virtual environment.

---

### Post by wojox on 2011-05-16
Open a terminal and run **ie6** or find the correct path to where it's installed in the home directory.

---

### Post by jim_deadlock on 2011-05-16
The solution may be as simple as using Firefox with the user-agent switcher addon:

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/")

---

### Post by NormanFLinux on 2011-05-16
There's no way to install it in Linux and the latest version won't work all that well with WINE.

Firefox is a cross-platform browser and so is Chrome and Opera. If Microsoft and Apple want to be taken seriously, they need to build true cross platform browsers.

---

### Post by Thewhistlingwind on 2011-05-16
> **jim_deadlock said:**
> The solution may be as simple as using Firefox with the user-agent switcher addon:

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)

+1, this works like a charm 90% of the time.

---

### Post by 3 frags left on 2011-05-16
On that topic... does this Firefox add-on allows you to use ActiveX stuff? Because that's the main thing that locks many users in Windows: lazy programmers who only do stuff to IE.

---

### Post by jim_deadlock on 2011-05-16
There's nothing IE can do that FF can't as far as I'm aware. You will need to install a couple of things via the software centre though:

flashplugin-installer
sun-java6-plugin

Edit: you're right, I think ActiveX only runs under Windows anyway so the browser is irrelevant.

---

### Post by Curse on 2011-05-18
Alright, so the program needs ActiveX to work.

Anyway to do that without messing around with Wine etc? Wine hasn't been working out too well for me.

---

### Post by jim_deadlock on 2011-05-18
I think you've run across one of the very few things you can't do in linux. The whole point of ActiveX is that it integrates with the Windows system, so you need to be on Win to run it - other browsers will run ActiveX but only from within a Win environment. Your only real option is to install Windows in Virtualbox or VMware, it's quite a major job. With that said, it'll give you nice bragging rights when you show your friend that you can run Win from within Ubuntu :)

---

### Post by Toz on 2011-05-18
> **wojox said:**
> Open a terminal and run **ie6** or find the correct path to where it's installed in the home directory.

The default path will be:```
~/.wine/drive_c/Program Files/Internet Explorer
```

---

### Post by samMD on 2011-05-18
Chromium wont work with the website?

Thats weird..most "business sites" work with Chrome as I have switched many people's browsers from IE to Chrome simply b/c IE hangs way too much.. Haven t met a website that DOESN'T work with chrome even those sites that recommend  to use IE explicitly

---

### Post by Toz on 2011-05-18
Meh.
Too much time on my hands.....

---

### Post by wildmanne39 on 2011-05-18
> **Curse said:**
> I'm trying to convert my GF's brother to Linux, but he requires IE for a school website to work.

I've tried ies4linux, which doesn't work because it is abandonware as I later learned. 

I found [this](http://forums.gentoo.org/viewtopic-t-830877-start-0.html) and ran 

```
sh winetricks ie6
```

Which seemed to install IE, but I can't find how to run it anywhere.

Help? :/
Hi,one other thing you could is run ubuntu with virtualbox and install windows in it and that way you can run both operating systems at the same time,and have them each on a separate desktops.

---

### Post by Hedgehog1 on 2011-05-18
The 'Windows in VBox' is a handy solution:


[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]


***The Hedge***

:KS

---

### Post by wildmanne39 on 2011-05-18
> **Hedgehog1 said:**
> The 'Windows in VBox' is a handy solution:


[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]


***The Hedge***

:KS
Hi, that is a very cool screen shot.

---

### Post by johndharvey on 2011-05-19
The ugly and convoluted possibility that comes to mind would be to run a Windows version of Firefox on WINE, with the User Agent Switcher add-on.  This is very far from ideal, but it's the best I can think of.

---

### Post by samMD on 2011-05-19
I know this has probably been said but I think try Chrome first if you havent already...you will spend more time and its more chances of screwing something up on the system..(not that your touching anything important) but virtualization has issues.. again im no expert in ubuntu as Im still new but bringing knowledge I knew from windows..

---

### Post by samMD on 2011-05-19
> **Toz said:**
> Meh.
Too much time on my hands.....

lol yea you do haha..is that Arch by any chance?

---

### Post by Toz on 2011-05-19
> **samMD said:**
> lol yea you do haha..is that Arch by any chance?

Actually, it's plain Xubuntu Natty - with some tweaking.

---

### Post by Curse on 2011-05-22
> **jim_deadlock said:**
> I think you've run across one of the very few things you can't do in linux. The whole point of ActiveX is that it integrates with the Windows system, so you need to be on Win to run it - other browsers will run ActiveX but only from within a Win environment. Your only real option is to install Windows in Virtualbox or VMware, it's quite a major job. With that said, it'll give you nice bragging rights when you show your friend that you can run Win from within Ubuntu :)

Sounds like a fun challenge :]

Unfortunately, he lives in Utah and I live in Idaho, and so if I were to do something like that it'd have to be as braindead user friendly as iTunes.... he's not quite as tech savvy as yours truly :p

---

### Post by jim_deadlock on 2011-05-22
Well when I say major job I mean in terms of the length of time it takes to install Win, it's actually easy peasy if you have the time. It's just a matter of installing Virtualbox then from VB create a new machine and run your Windows installation CD.

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

(install the extension pack also) - the download is a .deb file which will automatically open in the software center. It's all newbie friendly.

Note: there is "Virtualbox OSE" in the software center but I don't recommend it, there are some important features missing. Better to download it from the site as above.

---

