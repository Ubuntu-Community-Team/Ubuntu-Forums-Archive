---
title: "Direct X problem?"
date: 2010-05-08
forum: General Help
---

### Post by Tzar Meathammer on 2010-05-08
Everytime I try to run Guild Wars it says that there is a Directx problem, or if I try to run it with wine, it plays the sound, but no video. Any help?

[IMG]http://s863.photobucket.com/albums/ab195/TzarMeathammer/?action=view&current=Screenshot-3.png[/IMG]


[IMG]http://s863.photobucket.com/albums/ab195/TzarMeathammer/?action=view&current=Screenshot-2.png[/IMG]

---

### Post by Oddbio on 2010-05-08
You will have to be more specific.
When do you get this error, does anything show up on the screen at all?
What video card do you have? Using Gnome? version of wine?


But most importantly, try to run it from the terminal and post here what you see as output.

If you are running it with a shortcut then go to the properties and look at the command line it uses, simply copy and paste that into a terminal to run it so that you can view the output.

---

### Post by Tzar Meathammer on 2010-05-08
Well I have some screen caps but im not sure how to get them on here. I get the same result from the terminal as when I use crossover games.

EDIT: Well, I'm not sure the version of wine. My card is crappy, Family Chipset G33/G31. I have a slim computer D: but I've played Guild Wars when I was using windows. I really don't know how to know if I'm using Gnome or not, and I don't know how to check my wine version. Sorry I'm not very helpful , I've only been using Ubuntu for a month.

The one with blue is what happens when I use wine. The second is what happens when I use terminal/crossover games.

---

### Post by TheNerdAL on 2010-05-08
> **Tzar Meathammer said:**
> Well I have some screen caps but im not sure how to get them on here. I get the same result from the terminal as when I use crossover games.

There should me a "Manage Attachments" when you add a reply or edit your post and click on "Go Advanced", just scroll down and you'll see it.

---

### Post by Slim Odds on 2010-05-08
Some Windows programs will run with WINE, some won't.

Check the WINE website for compatibility info. Don't expect too much for running Windows apps on Linux.

---

### Post by sandyd on 2010-05-08
> **Tzar Meathammer said:**
> Well I have some screen caps but im not sure how to get them on here. I get the same result from the terminal as when I use crossover games.

EDIT: Well, I'm not sure the version of wine. My card is crappy, Family Chipset G33/G31. I have a slim computer D: but I've played Guild Wars when I was using windows. I really don't know how to know if I'm using Gnome or not, and I don't know how to check my wine version. Sorry I'm not very helpful , I've only been using Ubuntu for a month.

The one with blue is what happens when I use wine. The second is what happens when I use terminal/crossover games.
[B]Wine version
[/B]```
wine --version
```as for the directx error, try this.
```

wget -c [http://winezeug.googlecode.com/svn/trunk/winetricks](http://winezeug.googlecode.com/svn/trunk/winetricks)
chmod 667 winetricks
sh winetricks d3dx9 ddr=opengl glsl-disable
```and

turn off compiz. If your using fglrx (proprety ATI video driver), you won;t be able to run GUild Wars because of [http://bit.ly/a1llwZ](http://bit.ly/a1llwZ)

---

### Post by Tzar Meathammer on 2010-05-08
> **Slim Odds said:**
> Some Windows programs will run with WINE, some won't.

Check the WINE website for compatibility info. Don't expect too much for running Windows apps on Linux.

Well I've read in alot of places that people have played GW with Wine just fine. I don't know, I just really want to play a MMO right now.

EDIT: OK, I have wine version 1.1.43 and I did that winetricks thing

EDIT2: Ok so it still doesn't work. Having trouble checking, i'm playing some matches on my xbox.

---

### Post by Tzar Meathammer on 2010-05-08
Well, I don't know if there is anything that can be done at the moment, because none of this stuff is working. Oh well...

---

### Post by sandyd on 2010-05-08
sigh....
i guess that leaves me to point you at -> [http://appdb.winehq.org/appview.php?appId=2243](http://appdb.winehq.org/appview.php?appId=2243)

---

### Post by Tzar Meathammer on 2010-05-08
> **carlee said:**
> sigh....
i guess that leaves me to point you at -> [http://appdb.winehq.org/appview.php?appId=2243](http://appdb.winehq.org/appview.php?appId=2243)

Well if you were pointing me to the download on that page, that is what I have been using. I tried the disc just now and got the same results. If there was somethign else on that page that I was supposed to be looking for, then I have no idea o.O It's about midnight, and I'm kinda tired. Sorry for any and all inconvenience I have caused you

---

### Post by Tzar Meathammer on 2010-05-09
OK! I messed around with Wine configuration a bit, and now it's working. Thank you to everyone who tried to help.

---

