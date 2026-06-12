---
title: "GameMaker 8.1 for ubuntu?"
date: 2011-08-25
forum: General Help
---

### Post by Benja6678 on 2011-08-25
Hello,
I have been trying to get GameMaker working on linux, but it does not seem to work. 
When I tried running it on wine, it said "Wine: Install the windows version of mono to run .Net executables"
I installed Mono for windows. It says it is installed (using Mono --version).
it still does not work.

(note: I would paste what it said on the terminal, but for some reason i cant copy or paste to and from the terminal. any help for that?)

Thanks, Ben
(By the way, first post!)

---

### Post by MegaLoler on 2011-08-25
If it is a .net application then you should be able to run it without wine.  Open a new terminal window and type:
```
mono <path to file>
```

If you don't have mono installed then do
```
sudo apt-get install mono-runtime
```
(I think that is the right package, not 100% sure, though)

Don't be fooled into thinking that a .exe can only be run in wine, that is also the file extension for .net applications.  I learned that the hard way.

For copying/pasting in terminal the keyboard shortcuts have a shift in them.  Copy = ctrl+shift+c  Paste = ctrl+shift+v

---

### Post by SingingBush on 2012-02-02
I know this is an old thread but it is worth pointing out to anyone wanting to use Game Maker on Linux that there is a cross-platform alternative for handling Game Maker projects: [lateralgm]("http://lateralgm.org")

---

### Post by driver8086 on 2012-02-24
and a multi-platform game studio here:
[http://www.sandboxgamemaker.com](http://www.sandboxgamemaker.com)
mac, linux, windozzzzzz

ow, yea, its FREE too ::P

---

### Post by 3v3rgr33n on 2012-07-28
> **SingingBush said:**
> I know this is an old thread but it is worth pointing out to anyone wanting to use Game Maker on Linux that there is a cross-platform alternative for handling Game Maker projects: [lateralgm]("http://lateralgm.org")

I know this is old but I have to thank you SingingBush, you saved my life! I've been using Game Maker for a week now and I was getting tired of seeing Windows.:)

---

