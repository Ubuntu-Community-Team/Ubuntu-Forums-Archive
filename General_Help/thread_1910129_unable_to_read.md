---
title: "unable to read"
date: 2012-01-16
forum: General Help
---

### Post by toscanv on 2012-01-16
Hello all, new to Ubuntu. installed 11.10 and am having trouble. you can see by the screen shot that the words are a jumbled mess. they are ok when starting up but as more files are opened or closed things look like this. after re boot back to normal. Anyone seen this before? running on pentium 4 only 512 mb ram but upgrading to 2gb.

---

### Post by jerrrys on 2012-01-18
Ubuntu should run on those[ specs. ]("https://wiki.ubuntu.com/OneiricOcelot/ReleaseNotes#System_Requirements")but your still asking a lot of your P4.  Have you considered Xubuntu?

---

### Post by Mark Phelps on 2012-01-18
What video card/chipset are you using?

If you don't know, open at terminal and enter "lspci" -- and look for the line containing "VGA".  That will display the make and model video card/chipset.

---

### Post by jerrrys on 2012-01-18
It may be easier for you to read the output of this command:

lspci -nn | grep VGA

or just

lspci | grep VGA

---

### Post by toscanv on 2012-01-23
just went ahead and upgraded ram. runs like a champ. thanks

---

### Post by jerrrys on 2012-01-23
Congratulations and welcome to the forum :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

