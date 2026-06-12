---
title: "Advice needed"
date: 2006-05-09
forum: General Help
---

### Post by maxping on 2006-05-09
I have a old Pentium III 922 PC with 256mb ram and on board vid & sound it has something like windows NT4 on it. (saved from the tip) 

I have just installed Ubuntu and wiped windows off the pc , all seems well.

Is there a internet parental control filter that will work with it. 

I am currently using this on my sons PC, will it work with Ubuntu ? [http://www.radiance.m6.net/](http://www.radiance.m6.net/) 

If i can get it to work i intend to put it on my sons PC which is the same spec as the one above but has more ram and a GeForce2 MX 200 64MB graphics card . 

Are my sons games likely to work ?

---

### Post by Dr. Nick on 2006-05-09
Never used it but here is a filter [http://dansguardian.org/](http://dansguardian.org/) Im sure their are others

Depends on the game as to how well it works in linux

---

### Post by Monster_user on 2006-05-09
[QUOTE=maxping]Are my sons games likely to work ?[/QUOTE]

First requirement computer games to work on Linux. Have a 500mhz or faster processor for older games.  Have a 2.0ghz or faster processor for newer games.

You have a 922mhz... ??? 
*I think that is wrong. either you have a fancy PIII 900mhz system, or you were using a speed dection tool, and you have a 933mhz. Most Intels slower than a Gigahertz kept to a specific set of numbers. x00, x33, and x66. Pentium 75s, and P90s were oddballs. Either way, your system is faster than a 500mhz so your good.*

Second requirement. Have a NVidia graphics card for older games. Have a NVidia Geforce FX (a.k.a Geforce 5) card, or better for newer games. Preferably a Geforce 6800. 
You have an older NVidia card, so you can play older games. 

Third requirement. Get a Linux game, or get to know Wine.
You made no mention of Wine, CrossOver Office, or Cadega. 

Wine is a free Windows 98/NT4 compatibility layer, which allows many Windows programs to run under Linux. Not all programs work, and games have the most trouble. Support for the DirectX API is limited (used by most games).
However OpenGL software works 90% of the time (used by screensavers, and a lot of games).

Wine can be a pain to try to configure, and get working (Its free, you get what you pay for. Actually you get more than you paid for.). Once it works though, it stays out of sight, and can fool you into thinking the software is running natively.

Cadega is a subscription based, DirectX game compatibility program, based on Wine. It has also made Wine a little bit easier to use. A lot of games work, but it is recommended that you check the compatibility list, to see if there are any problems, or if anybody has even tried to play the game.

CrossOver Office is an enhanced, easy to use version of Wine, optimized for use with Office software. It costs about $50 for the standard version.
Few games work out of the box with CrossOver.

---

### Post by maxping on 2006-05-09
[QUOTE=Monster_user]
Third requirement. Get a Linux game, or get to know Wine.
You made no mention of Wine, CrossOver Office, or Cadega. 

.[/QUOTE]

Thanks for the info , i am new to Linux so haven't a clue what the above do but i will try your suggestions.

The games my son plays are not the most modern , need for speed underground is probably the most resource hogging game he has.

The graphics card is more than enough for this game.

---

### Post by nanomad on 2006-05-10
> Is there a internet parental control filter that will work with it. 

If you are interested, I'm working on this feature for ubuntu right now.
I've prepared an howto + a couple of packages to implement a content-filtering proxy. You can find it [ here ](http://www.ubuntuforums.org/showthread.php?t=172803&highlight=parental). If you try it, please say what do you think of it (and report bugs also!)

---

