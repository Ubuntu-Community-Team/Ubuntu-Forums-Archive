---
title: "Nautilus segmenation fault"
date: 2010-11-29
forum: General Help
---

### Post by Ad1217 on 2010-11-29
Hello, i have been using ubuntu for a while, and recently nautilus has been acting up. It will load fine at boot, but after some time it will crash and fill my lower bar with "Starting File Manager." When I try to start it from a terminal, It gives me 
"Initializing nautilus-gdu extension
Segmentation fault"
every time. When I run it as root it is fine, but very annoying (the permissions of everything get messed up). Does anyone know what is wrong or how to fix it?

---

### Post by DarthScape on 2010-11-29
Does it work in another user? Create a test user and see.

---

### Post by Ad1217 on 2010-11-30
It works under root and "test."

---

### Post by Ad1217 on 2010-12-02
when I do sudo nautilus it works, but my desktop is replaced by the root desktop, and all files created/moved/copied are owned by root. this is quite annoying as all of my other programs cannot use these files

---

### Post by mc4man on 2010-12-02
Probably a real longshot - the only time I've seen this here - "fill my lower bar with "Starting File Manager" was connected to a malfunction with ubuntuone.
If you're not using it then run this, restart, and see
```
sudo apt-get purge ubuntuone*
```

---

### Post by Ad1217 on 2010-12-02
unfortunately, I am quite using it...

---

### Post by Ad1217 on 2010-12-02
however, I just tried it and it worked like a charm!

---

### Post by Ad1217 on 2010-12-02
but when I reinstall it fails again

---

### Post by Ad1217 on 2010-12-02
I can get "ubuntuone-client" but not "ubuntuone-client-gnome." Any idea why?

---

### Post by Ad1217 on 2010-12-02
I read the output from sudo apt-get purge ubuntuone* and is said that a folder had not been deleted, so i deleted it it and now it works! yay!!:)

---

### Post by mc4man on 2010-12-02
hopefuly it will stay good - one thing to ck. - 
In firefox go edit - preferences - advanced. Make sure firefox is the default, click the check now box.

---

### Post by Ad1217 on 2010-12-09
Why?

Oh, and the shortcuts under "places" do not work anymore:(

---

### Post by Ad1217 on 2010-12-12
bump

---

### Post by mc4man on 2010-12-12
> shortcuts under "places" do not work anymore
you may want to explain that a bit more - possibly this.?

[http://ubuntuforums.org/showthread.php?p=10098466#post10098466](http://ubuntuforums.org/showthread.php?p=10098466#post10098466)

If so, after fixing - whenever using the open with - other application menu make sure the 'Remember this....' box is unchecked or the default for whatever you are opening will be changed to app chosen

---

### Post by Ad1217 on 2010-12-12
no, not that. The "Places" menu shortcuts in the top left of the screen do not work any more. When I click on one, I get a spinning wheel and a "Opening..." bar in the window list, but they both go away and nothing happens.:(

However, folders on the desktop still open, and the bookmarks still work after nautilus is open

---

### Post by 311005901 on 2010-12-12
I would suggest deleting your .nautilus file under /home/USER/.nautilus .

If you still can't fix it, I'd also suggest reinstalling nautilus.

---

### Post by Ad1217 on 2010-12-14
> **311005901 said:**
> 
If you still can't fix it, I'd also suggest reinstalling nautilus.

Reinstalling nautilus did:
a. not fix the problem](*,):frown:
b. also happened to remove gnome-session for some reason.](*,):frown:

DON'T DO THIS!

---

