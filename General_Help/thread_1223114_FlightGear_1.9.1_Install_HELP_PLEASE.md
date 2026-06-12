---
title: "FlightGear 1.9.1 Install HELP PLEASE"
date: 2009-07-25
forum: General Help
---

### Post by bearsomg on 2009-07-25
I have downloaded the FlightGear 1.9.1 source for Ubuntu. I open the Terminal and navigate to the folder where the source is located. I type the first command fore compiling, sh ./configure. It runs for a bit, then tells me that I need SimGear 1.9.0 or newer. I download the latest SimGear package, 1.9.1, and run the same command in that source, but then it says I need plib 1.8.5. I got sick and tired of this constant loop. Could someone please give me step by step instructions here? Or at lease a link to the FlightGear .deb or all of it's dependencies and their links? Please, I liked FlightGear alot in Windows and I really want it to work in Ubuntu. :confused:

I tried running it in Wine, but it was slow as heck.:(

---

### Post by madsmeg on 2009-07-26
Try ```
sudo apt-get install flightgear
```

I am pretty sure it is in the repo's

If the version is lower than what you want to use, this will also install the necasary dependencies it will need, you could also try

```
sudo apt-get build-dep flightgear
```

and then carry on ./configure and ./make

---

### Post by bearsomg on 2009-07-26
Yea, I tried 

```
sudo apt-get flightgear
```
but it gave me the wrong version, it didn't even give me fgrun. I got farther, got plib installed, but now I'm working on OpenSceneGraph another dependency for SimGear.

---

### Post by madsmeg on 2009-07-26
[Try Here]("http://www.integratedtechnologies.eu/?q=node/21") 

See if this helps you at all.

---

### Post by Yellow Pasque on 2009-07-26
Use that build-dep command. You need all the -dev packages, such as libopenscenegraph-dev

---

### Post by bearsomg on 2009-07-27
Thanks for the link, I went there and I'm downloading fgrun right now!

---

### Post by undeadboe on 2009-07-27
just get it from add/remove. youll have no problems installing it then.

---

