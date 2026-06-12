---
title: "Is it possible to xfer already installed games to another os patition?"
date: 2012-04-28
forum: General Help
---

### Post by slixz85 on 2012-04-28
hi. as title is i just want to know Is it possible to xfer already installed games to another os patition?

i have two os on my system peppermint ice and xubuntu

peppermint ice has been giving me problems and i have alot of games installed. i dont have the .deb temporary file downloads anymore just the games installed.
xubuntu runs fine and clean install so just wanting to know how to get these games without redownloading them. i dont have an internet connection right now just trying to enjoy my games for a few months until i get it again.

thanks

---

### Post by slixz85 on 2012-06-13
!bump!

---

### Post by Bucky Ball on 2012-06-13
Not sure you can do that ... but; you could create symlinks in Xubuntu to the games in the Peppermint install, if you can access that partition from Xubuntu.

Find the game's launcher and then do something like this:

```
ln -s /peppermint/usr/share/applications/your_game /xubuntu/games/your_game
```

... where the first part of the command points to your game in the Peppermint install, the second to the symlink in the Xubuntu install. This will give you a symlink to your game in Peppermint in the Xubuntu directory /games. 

Your command will, of course, look totally different to this one, but you get the idea. From the first example here:

[http://linux.byexamples.com/archives/19/how-to-create-symlink/](http://linux.byexamples.com/archives/19/how-to-create-symlink/)

---

### Post by slixz85 on 2012-06-14
> **Bucky Ball said:**
> Not sure you can do that ... but; you could create symlinks in Xubuntu to the games in the Peppermint install, if you can access that partition from Xubuntu.

Find the game's launcher and then do something like this:

```
ln -s /peppermint/usr/share/applications/your_game /xubuntu/games/your_game
```

... where the first part of the command points to your game in the Peppermint install, the second to the symlink in the Xubuntu install. This will give you a symlink to your game in Peppermint in the Xubuntu directory /games. 

Your command will, of course, look totally different to this one, but you get the idea. From the first example here:

[http://linux.byexamples.com/archives/19/how-to-create-symlink/](http://linux.byexamples.com/archives/19/how-to-create-symlink/)

thanks alot I will try this. of course I can understand what you mean by not even knowing for sure if it can be done but I can't redownload the 100-200mb games a piece i share a wifi connection (it is my friends) and i cap it off with wondershaper at only 50KB-100KB TOPS (because i am surfing for free anyway and it would affect there speed to redownload all of it. slow in today's world i know but for simple web browsing it is fast enough

---

### Post by Bucky Ball on 2012-06-14
I'm actually not so sure that will work. You can only give it a try. But thinking it is going to need to access a running Peppermint install (where the rest of the app is installed). 

See what happens ...

---

### Post by Slim Odds on 2012-06-14
There is practically no chance of this working.

There are many dependencies that need to also been handled.

It's just not possible.

---

### Post by Bucky Ball on 2012-06-14
> **Slim Odds said:**
> There is practically no chance of this working.

There are many dependencies that need to also been handled.

It's just not possible.

+1. Agreed.

---

