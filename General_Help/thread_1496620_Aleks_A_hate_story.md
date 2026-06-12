---
title: "Aleks: A hate story"
date: 2010-05-29
forum: General Help
---

### Post by blagosphere on 2010-05-29
As some of you may know ALEKS is a new "tool" used by schools as a supplement  math program. I need to keep up with my ALEKS and have a weekly class to work on it. The only problem, other than ALEKS being completely evil is that i can not get it to work on my AMD64 ubuntu 10.04 system. I am dual booting on a toshiba portege tablet and once logged in to ALEKS it thinks about it, pretends to load, and then says "page not found." Even the streaming plugin will not work. I have looked into the issue somewhat and found that the "openjdk" on my system will not work and i need java6-sun; however, i can not figure out how to accomplish this. I need this worked out before school starts again or i will be forced to use the horrid Windows again! help is appreciated!

---

### Post by fancypiper on 2010-05-29
See the community support page: [Java Documentation]("https://help.ubuntu.com/community/Java")

---

### Post by blagosphere on 2010-05-29
I have looked at that page and it did not help. every time i attempt to install there are unmet dependencies. each piece relies on the other so that i may not install one. I am quite frustrated at this point because this really should be a simple process....

---

### Post by fancypiper on 2010-05-29
Perhaps you should post the errors so others could inspect them.

[Get the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

---

### Post by wilee-nilee on 2010-05-29
It would be highly unlikely if it is ported to open source, hope I'm wrong, but I doubt it.

---

### Post by blagosphere on 2010-05-29
From what i have read all i need to do is get sun-java6-jre and sun-java6-plugin with all dependencies of course. from there, there is a way to simply cache the ALEKS plugin to the browser so that i do not need to install that.... the only problem is that i have not found a viable way to install aforementioned java package for Lucid [AMD64].  

The dependacy issues have been that the -jre needs the -bin and i36[i think]-xxxxx-bin... -bin needs the -jre  and the other i36-xxxxx-bin needs the jre as well so no piece can be installed with out the others. as such i can not proceed.

---

### Post by s3a on 2010-05-29
Does it work with sun's java6 jre?

---

### Post by blagosphere on 2010-05-29
> **s3a said:**
> Does it work with sun's java6 jre?

i think it will but i have not been able to get that to work on my system.... i could use some installation instructions.

---

### Post by Sin@Sin-Sacrifice on 2010-05-29
Uninstall the openjdk then.
```
sudo apt-get install sun-java6-jre
```
Or you can search for it in synaptic...

---

### Post by blagosphere on 2010-05-29
> **Sin@Sin-Sacrifice said:**
> Uninstall the openjdk then.
```
sudo apt-get install sun-java6-jre
```Or you can search for it in synaptic...

attached is the terminal output from that command.

---

### Post by clhsharky on 2010-05-29
blagosphere

You need the partner respiratory's enabled in software sources. 
Then you can do as Sin@Sin-Sacrifice suggested.

Sharky

---

### Post by blagosphere on 2010-05-29
> **clhsharky said:**
> blagosphere

You need the partner respiratory's enabled in software sources. 
Then you can do as Sin@Sin-Sacrifice suggested.

Sharky


attached are two pics of my software sources... what do i need to change?

---

### Post by Chronon on 2010-05-30
Have you updated apt since adding new repositories?  
```
sudo apt-get update
```

Since you're using Jaunty, the packages should be in Multiverse.

---

### Post by blagosphere on 2010-05-30
I am actually using Lucid i just enabled the jaunty repositories to see if that helped. It did not. I updated apt-get and have the same result. "no installation candidate"

---

### Post by CoreyB. on 2010-05-30
> **blagosphere said:**
> I am actually using Lucid i just enabled the jaunty repositories to see if that helped. It did not. I updated apt-get and have the same result. "no installation candidate"

Uninstall openjdk, change your sources back to lucid (changing to jaunty is just going to cause more problems), in synaptic search for sun-java6-plugin, and install it.

This really isn't that difficult and I am sorry it has taken two pages to get a simple answer.

---

### Post by stinkeye on 2010-05-30
There is a tutorial here if that helps.
[**_[COLOR="DarkRed"]http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/[/COLOR]_**]("http://www.ghacks.net/2010/05/21/install-java-on-ubuntu-10-04/")

---

### Post by blagosphere on 2010-05-30
Thanks stinkeye! it works now!! I love the ubuntu community, eveyone is so helpful!

---

### Post by B-Mart on 2010-09-10
So yeah, I got it to work, but now for some reason the windows don't pop up for me to input answers or sometimes the "next" buttons don't show up for me to go to the next question...so any help would be stellar

---

### Post by jackechanprime on 2010-09-11
I've got the same problem as b-mart. I got the program "operational" but firefox isn't running several critical scripts within it. These scripts are the answer interface (kinda critical, as it's basically math homework... no answer = no points = FAIL) and some form of navigation interface with "next, back, done, etc" buttons. Without these scripts running properly, simply put, Aleks is NOT running yet, and this is NOT solved (for all cases).

p.s. totally agree with the thread name. "a hate story"


;_; please help me not have to revert back to windows.

---

### Post by jackechanprime on 2010-09-13
O_o erm.... never...mind? It kinda... spontaneously started working right.

nooooo idea what did it.
pretty sure i didn't even to a system update... and now it works right.

oh well, take the blessings as they come i guess.
~Q

---

