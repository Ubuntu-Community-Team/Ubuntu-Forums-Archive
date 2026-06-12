---
title: "Opera Doesn't Work"
date: 2010-03-18
forum: General Help
---

### Post by marshfish on 2010-03-18
Using the command line I installed Opera and it went through the process of installation fine. After I restarted and saw the icon I clicked to find nothing happens. It says loading then *poof* the PC just sits there idle. What is with UNR!?  :mad:

Google Chrome works and so does firefox but why not Opera, help please.

---

### Post by zvacet on 2010-03-18
Why didn´t you install it with double click on package?Opera have to dependencies which must be installed if you want Opera to work.Dependencies are installed during Opera installation.i HAVE TO SAY THAT I never used UNR but I think it should be the same.

---

### Post by marshfish on 2010-03-19
> **zvacet said:**
> Why didn´t you install it with double click on package?Opera have to dependencies which must be installed if you want Opera to work.Dependencies are installed during Opera installation.i HAVE TO SAY THAT I never used UNR but I think it should be the same.
UNR likes saying "PACKAGE INSTALL FAILED" if you try to double click and install the package. That's why I did it through the command line. I really think this bug should be fixed. It happens allot especially when you are in Synaptic Package Manager. 

Any solution to fix this or should I uninstall Opera and then try installing the package the easier way?

---

### Post by lyall on 2010-03-19
try to un-install if you can

then go the Opera site for downloads for Ubuntu 
[http://www.opera.com/browser/download/]("http://www.opera.com/browser/download/")

you might need GDebi Package Installer if you do not already have it 
it is in Synaptic Package Manager look for **gdebi**

It worked for me
I use Opera

good luck and have fun learning

---

### Post by marshfish on 2010-03-26
It still refuses to show Opera. Linux is a joy killer. As soon as you fix one problem another hits you in the face. How would I fix this? I really want Opera and it is installed but doesn't show once you start the program. It's eating my resources while not actually allowing me to use it.

---

### Post by 3rdalbum on 2010-03-26
You can't run multiple package managers at the same time.

Did you download a .deb or a .tar.gz of Opera? If you downloaded a .tar.gz, then you probably don't have all the required libraries to make Opera run.

Download the .deb (it's what the Opera website presents to you when you go to download it), double-click it with no other package managers or package installers running at the same time, and install it that way. It will also download a number of different packages that are necessary.

If you've already done this and are still having problems, open up the terminal: Accessories > Terminal and put in the following:

```
opera
```

Anything that gets put into the terminal, please copy and paste into this thread and we'll see what we can do.

---

### Post by sdowney717 on 2010-03-26
[http://www.opera.com/download/index.dml?platform=linux](http://www.opera.com/download/index.dml?platform=linux)

Download the deb file and click it to install. It simply installs and running for me on Lucid.

---

### Post by marshfish on 2010-03-27
What a joy killer. Here's what happened when I typed Opera in the terminal:

[http://i91.photobucket.com/albums/k289/reshy01/Termianl.png](http://i91.photobucket.com/albums/k289/reshy01/Termianl.png)

This is annoying:

[http://i91.photobucket.com/albums/k289/reshy01/Loading.png](http://i91.photobucket.com/albums/k289/reshy01/Loading.png)

---

### Post by Nolan7689 on 2010-03-28
Rather than creating my own thread for a very similar problem I'll just bump this one.

I've just install Ubuntu on my laptop for the first time, I'm not a fan of Firefox so the first thing I do (after switching back to VGA since DVI makes the text unreadable, but that's a different issue) is go to Opera and download Opera 10.10 .deb. As soon as I try and run it though (with gdebi) I get the following error.

> Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)

I have no clue what to do besides ask for help, so here I am.

---

### Post by mkvnmtr on 2010-03-28
You might have a repository that is not enabled and should be. I have installed Opera about a dozen times with gdebi and it always found what was needed. Even on minimal installs. I believe I have installed ot on 6.06 through 10.04.

---

### Post by Nolan7689 on 2010-03-28
I'm not sure what changed exactly other than I rebooted after installing ATI drivers, and opera installed just fine without a hitch.

---

### Post by seenthelite on 2010-03-29
I just go to Opera.com/downloads and it detects I am using Linux x86-64 then I select Ubuntu and the default package. Click on Download.

---

### Post by marshfish on 2010-03-29
This forum is pretty useless. I can't start Opera, it came up with no binary files even though I used the package installer and still no cigar. What do I need to do to get it to work?

---

### Post by mkvnmtr on 2010-03-29
It looks like you fouled up the installation. Maybe you can figure out how to uninstall and reinstall correctly.

---

