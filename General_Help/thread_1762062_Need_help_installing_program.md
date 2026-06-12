---
title: "Need help installing program"
date: 2011-05-18
forum: General Help
---

### Post by jackbones10 on 2011-05-18
I'm running Ubuntu 11.04 (also Classic, don't really care.) I'm trying to install [Greeting Card Factory DELUXE V7] Can anyone help me or does anyone have any clue whatsoever if this can be achieved?

---

### Post by wildmanne39 on 2011-05-18
> **jackbones10 said:**
> I'm running Ubuntu 11.04 (also Classic, don't really care.) I'm trying to install [Greeting Card Factory DELUXE V7] Can anyone help me or does anyone have any clue whatsoever if this can be achieved?
Hi, is that a windows program?

---

### Post by idoitprone on 2011-05-18
[http://www.amazon.com/Greeting-Card-Factory-Deluxe-VERSION/dp/B000XSDM04](http://www.amazon.com/Greeting-Card-Factory-Deluxe-VERSION/dp/B000XSDM04)

from the looks of it, it is.

i can only give the general directions

there are two options;wine or emulate windows with a program kidda like virtual box.
I am going give some help for the wine direction

```
sudo apt-get install wine

```or use synaptic
put the install cd in the computer

cd to the install cd
```
wine install.exe
```or use nautilus and open with wine

to run the program.
go the file and open with wine
or 
```
wine program.exe
```[http://www.winehq.org/](http://www.winehq.org/)

if that version of wine do not work, get the more bleeding edge of wine
[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")

---

### Post by wildmanne39 on 2011-05-18
> **idoitprone said:**
> [http://www.amazon.com/Greeting-Card-Factory-Deluxe-VERSION/dp/B000XSDM04](http://www.amazon.com/Greeting-Card-Factory-Deluxe-VERSION/dp/B000XSDM04)

from the looks of it, it is.

i can only give the general directions

there are two options;wine or emulate windows with a program kidda like virtual box.
I am going give some help for the wine direction

```
sudo apt-get install wine

```or use synaptic
put the install cd in the computer

cd to the install cd
```
wine install.exe
```or use nautilus and open with wine

to run the program.
go the file and open with wine
or 
```
wine program.exe
```[http://www.winehq.org/](http://www.winehq.org/)

if that version of wine do not work, get the more bleeding edge of wine
[https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/%7Eubuntu-wine/+archive/ppa")
Thats what I thought too, I dont use wine I use virtualbox with windows.

---

