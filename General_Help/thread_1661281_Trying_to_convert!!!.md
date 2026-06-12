---
title: "Trying to convert!!!"
date: 2011-01-06
forum: General Help
---

### Post by XavierLore on 2011-01-06
Ok here goes everything..I'm new to this forum as well as ubuntu.I came from windows XP , Vista , & 7 .I have read a lot but I'm just getting overwhelmed.I would like to know first if windows is the "bug" and linux 'ubuntu' is the fix then why isn't one of the first default programs in ubuntu a program that makes it easier to change over? My problem is I have a desktop with about 3 terrabytes of movies, music, games, and other data that I've gained over the years that is useless to me because I don't know how to do anything on ubuntu.I don't have the internet on my desktop so I can't use the sofware center so I'm forced to download and research off my vista(puke) laptop.This is making things really hard.I don't know how to install anything that will help me.My main concern is the ability to watch my movies ( Mp4 avi ect.) play my music (mp3) and my games (exe.).I know I don't want to transcode my movies and music so what do you guys advise?As far as my games and other exe programs go are they just useless to me now or is there a way to install them that ubuntu understands?I'm just a fustrated noob trying to use my laptop to get my desktop working(I'm dual booting ubuntu off my laptop but since the ubuntu on my laptop won't connect to the Wi Fi I still can't use the software center or even mess around with it .So understanding the state I'm in what are the steps that you would advise.(I'm also having trouble finding good guides that would help) please hook me up with some links before I throw all my computers away and go eat grass.:mad:

---

### Post by nothingspecial on 2011-01-06
You need to connect to the internet. What`s the problem there? What have you tried.

You will have no problem with your music and movies.

Games, however, will be a an issue. You maybe able to get some of them going, sort of with a program called wine.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)



If there is no way you can get an internet connection, I suggest you haul your computer to a friends house and get aptoncd.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by HermanAB on 2011-01-06
To play movies, you will need to connect to the medibuntu repositories to get the codecs.  One solution is to install Linux Mint instead of Ubuntu, since Mint installs all the medibuntu codecs by default.

---

### Post by ShakeyJake on 2011-01-06
You seem to have dived into this head first without a plan. Why can't you access the internet? If it's wifi issue then its really a good idea to haul your desktop down to where the router is and plug it in via ethernet.

Then just use it for a bit. If you try to play a file that needs a piece of software then it will automagically start downloading the software for you. You should also be able to sort out your wifi issues and come up with a more permanent fix. 

.exe files are useless to you now, you should reall expect for any Windows-only programs to not work, that way you'll end up pleasantly surprised if they do. Wine has already been mentioned and there is the awesome playonlinux too.

---

### Post by peedeeramone on 2011-01-06
yeah, mostly been said already, music and videos should work fine you'll just need to install the codecs (internet required)

for that if you open a command terminal type this:

sudo apt-get install ubuntu-restricted-extras

again you will need an internet connection to do so. 

wine will run a whole buunch of windows software, its pretty impressive, it sometimes runs them better than windows itself (in legacy cases at least) but again you will need an internet connection to install.


so basically you need to get the internet working on your desktop. i have honestly never heard of a desktop being plugged in through ethernet not working properly in ubuntu (thats the standard cat5 network cable into the back) is this not available for you? for your lappy, it can sometimes be a little more difficult but anytime i havent been able to get a laptop to work initially i just plug it into via ethernet and it downloads drivers for me (at least within the past 3 or 4 years).

you sound stressed, i would just relax and play with it as you can. its okay to convert from windows to linux over time. just remember that linux is not windows and you do things just a little differently (the same way if you bought a mac you would have to do things differently).

i would reccomend plugging your computer up to a hardwire connection and i would give you at least a 90+% chance that would solve your problem. good luck

---

### Post by nothingspecial on 2011-01-06
> **HermanAB said:**
> To play movies, you will need to connect to the medibuntu repositories to get the codecs.  One solution is to install Linux Mint instead of Ubuntu, since Mint installs all the medibuntu codecs by default.


Good point.

Doesn`t ubuntu prompt you to install the codecs nowadays?

Here`s something to look at

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/solve%20all%20your%20muli-media%20problems%20with%20a%20few%20copy%20and%20pastes")

---

