---
title: "It is very difficult to install software in Ubuntu in a computer without internet"
date: 2009-08-12
forum: General Help
---

### Post by praveesh on 2009-08-12
It's very difficult. Download the deb file. Download the dependancies, then the dependancies of dependancies, then their dependancies  etc.  . I have a solution for this problem. Why not packing the app and the dependancies in a single tar ball along with a shell script which can install all packages in the order ?.

---

### Post by bryonak on 2009-08-12
You're looking for [SuperDebs]("http://hacktolive.org/wiki/Super_Deb").

As for downloading packages on another machine, here's the relevant part of my post about installing a KDE application (kexi) with lots of dependencies in Gnome from [this]("http://ubuntuforums.org/showthread.php?t=1226163") thread:

> **bryonak said:**
> 
Open a terminal on a machine with internet access (and the same Ubuntu version/architecture as your other) and type:
```
sudo aptitude clean
```
This will clean the cache, so you don't mix up packages. Then type:
```
sudo aptitude install -d kexi
```
The '-d' will only download the packages (without installing) to the /var/cache/apt/archives folder.
Copy the files ending with **.deb** from that folder to your other PC.
You can clean the cache on your internet computer again with ```
sudo aptitude clean
```

On your other machine, put all the files in one folder, for example "foo" on your desktop.
Since installing every single one of them by klicking is way too slow, we'll use the terminal again.
Browse to that folder within the terminal with the 'cd' (change directory) command... that should be about:```
cd Desktop/foo
```
Then install all the packages in that folder with:```
sudo dpkg -i *
```

---

### Post by Cheesemill on 2009-08-12
Or you could just use Keryx:
[http://keryxproject.org/](http://keryxproject.org/)

---

### Post by Tibuda on 2009-08-12
Have you installed Pidgin from GetDeb? You have to download four packages and install them in the *correct* order. I like this idea of a 'superdeb' with multiple packages.

---

### Post by Barrucadu on 2009-08-12
> **danielrmt said:**
> You have to download four packages and install them in the *correct* order.

Oh my god, installing things in the correct order&#8253; :P

---

### Post by praveesh on 2009-08-12
O

---

### Post by Cheesemill on 2009-08-12
Why the double post?
[http://ubuntuforums.org/showthread.php?t=1238418](http://ubuntuforums.org/showthread.php?t=1238418)

---

### Post by juancarlospaco on 2009-08-12
I got Repos on DVD, and no is not.
*.iso avaliable for download on this forum.*

---

### Post by Tibuda on 2009-08-12
> **Barrucadu said:**
> Oh my god, installing things in the correct order&#8253; :P

It sounds really dumb! I have no problem with it myself, it is more for the beginners trying to update Pidgin because of the broken protocols. The main problem is that you have to guess this correct order. libpurple0 first (obvious), then if you try to install libpurple-bin, nope it requires pidgin-data to be installed first.

---

### Post by NightwishFan on 2009-08-12
Here is a simple tip. Yes, it is hard, yes I am in the same boat.

Try AptonCD. It allows you to make a repository of all your download debs, and add it to a cd. I wish it could add it to a folder structure though.

HOWTO:

[LIST=1]
[*]Install Ubuntu on a friends computer with internet using Wubi, so it wont cause problems.
[*]Use synaptic package manager to install all the software you want. Check 'download only' after you hit apply, this is important.
[*]Install AptonCD without using download only.
[*]Run aptoncd to create your own DVD repository.
[*]Remove Ubuntu from Windows Add/Remove programs
[*]Install the APTONCD on your Ubuntu at home.
[/LIST]

Edit: Multiple threads, request workerbee mod to sort it out. :D

---

### Post by mcduck on 2009-08-12
> **danielrmt said:**
> Have you installed Pidgin from GetDeb? You have to download four packages and install them in the *correct* order. I like this idea of a 'superdeb' with multiple packages.

Nope, you can install all of them at the same time and dpkg will handle the correct order automatically. :)

You only need to figure the order yourself is you install them by clicking the .deb packages in a GUI.

---

### Post by Tibuda on 2009-08-12
> **mcduck said:**
> Nope, you can install all of them at the same time and dpkg will handle the correct order automatically. :)

"dpkg -i *.deb" works, but not gdebi...

---

### Post by RiceMonster on 2009-08-12
```
sudo apt-get install the-internet
```

---

### Post by juancarlospaco on 2009-08-12
Nah, Synaptics have the *"**create package download script**"*, 
and then use **WGET for windows** stand-alone .exe, thats it.
*No need to install Ubuntu to get packages.*

:)

---

### Post by TravisNewman on 2009-08-12
Threads merged.

---

### Post by Tibuda on 2009-08-12
> **RiceMonster said:**
> ```
sudo apt-get install the-internet
```

[http://www.w3schools.com/downloadwww.htm](http://www.w3schools.com/downloadwww.htm)

---

### Post by juancarlospaco on 2009-08-12
> **juancarlospaco said:**
> Nah, Synaptics have the *"**create package download script**"*, 
and then use **WGET for windows** stand-alone .exe, thats it.
*No need to install Ubuntu to get packages.*
:)

Also works on OS X and BSD too.

---

### Post by RiceMonster on 2009-08-12
> **danielrmt said:**
> [http://www.w3schools.com/downloadwww.htm](http://www.w3schools.com/downloadwww.htm)

I've never been able to get that download to finish. Maybe I need a better ISP.

---

### Post by praveesh on 2009-08-12
> **Cheesemill said:**
> Why the double post?
[http://ubuntuforums.org/showthread.php?t=1238418](http://ubuntuforums.org/showthread.php?t=1238418)

Iam sorry . My  browser didn't load the page(connectivity problem) . So I once again hit on "post thread". That made 2 threads

---

### Post by aysiu on 2009-08-12
Maybe you can vote up this Brainstorm idea?
[Idea #142: Optional add-on CDs (not advertised heavily, but still available) ](http://brainstorm.ubuntu.com/idea/142/)

---

### Post by praveesh on 2009-08-12
> **aysiu said:**
> Maybe you can vote up this Brainstorm idea?
[Idea #142: Optional add-on CDs (not advertised heavily, but still available) ](http://brainstorm.ubuntu.com/idea/142/)

voted up

---

### Post by praveesh on 2009-08-12
Super deb feels great. I wish if it were official. More over there are only 2 apps to install. Have to try keryx.

---

### Post by praveesh on 2009-08-12
> **juancarlospaco said:**
> Nah, Synaptics have the *"**create package download script**"*, 
and then use **WGET for windows** stand-alone .exe, thats it.
*No need to install Ubuntu to get packages.*

:)

from where can I get the windows installer and the script?

---

### Post by juancarlospaco on 2009-08-12
> **praveesh said:**
> from where can I get the windows installer and the script?

Windows installer is not needed.
[Its a stand-alone wget.exe]("http://sourceforge.net/projects/gnuwin32/files/wget/")

SYNAPTIC generate the Script, 
the script run on Linux/BSD/Windows/DOS
File--->Generate package download script

:)

---

