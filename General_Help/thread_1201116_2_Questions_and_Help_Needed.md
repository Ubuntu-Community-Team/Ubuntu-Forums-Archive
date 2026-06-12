---
title: "2 Questions and Help Needed"
date: 2009-06-30
forum: General Help
---

### Post by John Private on 2009-06-30
Solved Thanks Everyone.

---

### Post by credobyte on 2009-06-30
Close Add/Remove, Synaptic and all terminal windows & try again ( enable visual effects ).

Java ( JRE ) :
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

---

### Post by synapsys on 2009-06-30
To install JRE install all the sun-java6 packages except -doc.

What graphics driver do you have installed? (if any)

---

### Post by John Private on 2009-06-30
> **credobyte said:**
> Close Add/Remove, Synaptic and all terminal windows & try again ( enable visual effects ).

Java ( JRE ) :
```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```When I am doing the Visual Effects that doesnt help. and for the JRE I got this

[IMG]http://i363.photobucket.com/albums/oo78/catbodi3577/TerminalJREGetError.png[/IMG]

---

### Post by ibutho on 2009-06-30
Are you already running another package manager process e.g. synaptic or the package updater?

---

### Post by John Private on 2009-06-30
> **ibutho said:**
> Are you already running another package manager process e.g. synaptic or the package updater?Nope I closed everything.

---

### Post by ibutho on 2009-06-30
This [thread]("http://ubuntuforums.org/showthread.php?t=519612") has several solutions to the problem with the locked dpkg directory.

---

### Post by John Private on 2009-06-30
> **ibutho said:**
> This [thread]("http://ubuntuforums.org/showthread.php?t=519612") has several solutions to the problem with the locked dpkg directory.I tryed everything nothing worked...

---

### Post by John Private on 2009-06-30
Everyone Thank You So Much Thanks to Credobyte your JRE Works perfectly fine and thanks again Ubuntu Forums is the right place for friendly help.

---

### Post by ibutho on 2009-06-30
I'm glad you managed to solve your problems. :)

---

### Post by ronaldprettyman on 2009-06-30
> **John Private said:**
> 
[IMG]http://i363.photobucket.com/albums/oo78/catbodi3577/GraphicsCardDriverInstallerError.png[/IMG]
This looks like apt is running or locked up see if its running still, you can only run one instance of any of these Synaptic, Add/Remove, aptitude, apt-get, dpkg
```
ps -A|grep apt
ps -A|grep dpkg
```

Close the one that is running, don't interrupt it, or your run into other problems, let it finish then close it and start a new instance of it to install the restricted drivers. If your running updates, installing software with dpkg apt or any thing else debian/ubuntu based it won't allow you to install using another debian/ubuntu dpkg based file to prevent conflicts and other problems.

The only exception being when your compiling manually or with generic binary or installation script.

---

### Post by John Private on 2009-06-30
Thanks but I have a new problem :(. Read my Topic in General Help its not showing up for me though.

---

### Post by t4thfavor on 2009-06-30
What was the original 2 questions it seems that you removed them. How is this thread going to help anyone else if they don't know the question.

---

### Post by ronaldprettyman on 2009-07-02
> **John Private said:**
> Solved Thanks Everyone.

This really defeats the point. People read to find solution more then they ask. Google before you ask, and don't delete your questions. Its one thing to delete your answer because you were wrong, but its just not cool to delete your question.

---

### Post by John Private on 2009-07-02
> **ronaldprettyman said:**
> This really defeats the point. People read to find solution more then they ask. Google before you ask, and don't delete your questions. Its one thing to delete your answer because you were wrong, but its just not cool to delete your question.Alright I wont do it again.

---

