---
title: "Installing programs from .deb"
date: 2006-03-03
forum: General Help
---

### Post by Valareos on 2006-03-03
I know that this has been asked before, but I cant find it. if you have the answer, or at least a link to the answer, I would be much appreciated.

Im using ubuntu, and everything is working well, but is their an easier way of installing programs from a deb than in the terminal?  or is there a specific way I can type the command to automatically get the needed dependancies?

note, these are programs that dont show up in the application manager as availiable for install

---

### Post by h4ck3r on 2006-03-03
Deleted

---

### Post by halfvolle melk on 2006-03-03
I'm not sure I get you, but an other way than:
```
sudo dpkg ~/a_program.deb
```
?

---

### Post by Valareos on 2006-03-03
I know that way.  and as for me, I got not an issue of using a command prompt.

However, I work for a small computer company, and we are looking to Ubuntu as a free OS to install on customers computer for those that wish a low price computer solution.  The OS is the biggest part of the price of a computer.


We have been experimenting, using different ways of making it as user friendly as possible.  The last part is dealing with installing linux deb programs.   Idealy, the program im looking for will do the following...


1.  Check Dependancy status of the deb file
2.  If there are missing dependancies, automatically install them
3.  install deb after dependancies are fixed

---

### Post by akiro.yamamoto on 2006-03-03
The easiest way for a business to do this is probably for them to set-up a repo on a local server, with the apps and associated files for the various desktop systems? Then you will have total control over the apps that are installed and can perform system updates easily.

---

### Post by Haegin on 2006-03-03
Try the following:
Debins :: [http://programmer-art.org/debins]("http://programmer-art.org/debins")
dadebstaller :: [http://ubuntuforums.org/showthread.php?t=84314]("http://ubuntuforums.org/showthread.php?t=84314")
Gdeb :: Its in the repos, use synaptic

I haven't used any of these (except dadebstaller and that was a while back)

Hope this helps

---

### Post by Valareos on 2006-03-03
dadebstaller is exactly what I needed! THank you!

[QUOTE=Human Prototype]Try the following:
Debins :: [http://programmer-art.org/debins]("http://programmer-art.org/debins")
dadebstaller :: [http://ubuntuforums.org/showthread.php?t=84314]("http://ubuntuforums.org/showthread.php?t=84314")
Gdeb :: Its in the repos, use synaptic

I haven't used any of these (except dadebstaller and that was a while back)

Hope this helps[/QUOTE]

---

