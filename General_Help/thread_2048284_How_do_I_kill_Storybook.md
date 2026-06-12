---
title: "How do I kill Storybook:"
date: 2012-08-26
forum: General Help
---

### Post by Bucky Ball on 2012-08-26
Hi all,

I installed Storybook then realised it was pretty much a toy until you paid $35 bucks to register it. Then you could print! Neat app but that sucked so wanting to uninstall it. 

I located all files and killed them. When I issue:

```
locate storybook4
```... I get nothing. Good. But:

```
whereis storybook4
storybook4:
```?

Where and what the heck is 'storybook4:'? I would like it gone, despite the fact it's not doing anything (I presume). Just bugs me ... 

All suggestions welcome. ;)

PS: The file was a .run file. The instructions for installing it are on the site but don't remember the procedure off hand. Certainly couldn't find out how to uninstall it on that site. Might be hard to uninstall that way anyhow, if possible, as I've deleted all other files related to whatever 'storybook4:' is.

---

### Post by thnewguy on 2012-08-26
Why are you running "whereis storybook4"? Just to see if it is still installed? When you run "whereis" and it returns the name you just typed without any other information that means the file doesn't exist in your path. Judging from the information you have provided it looks like you have removed the application from your computer.

---

### Post by Lars Noodén on 2012-08-26
It looks like it might be a quirk in the program [whereis](http://manpages.ubuntu.com/manpages/precise/en/man1/whereis.1.html).  It seems to print a heading even if there are no search results.  From your output it looks like there are no results for storybook4.

Just to be sure, what method did you use to install storybook4 and what method did you use to uninstall it.  If you used the package manager for both, either through synaptic or the software center, then the program is removed for you.

---

### Post by gandaran on 2012-08-26
hi
I had a look at the storybook download file and it is a .bin file, these type of files usually install to /opt and may have an uninstall script inside or you can just delete the whole storybook folder, should get rid of storybook completely if you find it in /opt.

---

### Post by Bucky Ball on 2012-08-26
> **gandaran said:**
> hi
I had a look at the storybook download file and it is a .bin file, these type of files usually install to /opt and may have an uninstall script inside or you can just delete the whole storybook folder, should get rid of storybook completely if you find it in /opt.

Did that before I posted. Thanks for the input people. I will assume Storybook is no longer. At least on this machine. ;)

---

