---
title: "Help me get rid of Evolution remanents -- please"
date: 2012-04-15
forum: General Help
---

### Post by motomixon on 2012-04-15
Every time Update Manager runs I always see these two references to an Evolution files. (See my attached screen shot.)

Both Update Manager listings (in my screen shot) shows a reference to file 2.32.2-0ubuntu7, but I have done a "find" command from / and no where is such a file to be found. 

Evolution is currently not installed on my machine (Ubuntu 11.10), although maybe I once installed it and removed it. If I try to install Evolution from Software Center, I get the error: 

"Package dependencies could not be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time."

And the details line there shows this:
"evolution: Depends: evolution-common (= 3.2.2-0ubuntu0.1) but 3.2.2-0ubuntu0.1 is to be installed"

What is going on here and how to fix it??
Actually, I would like to try Evolution out, but am blocked. And otherwise I would like to repair an obvious fault in my Ubuntu installation.

Any ideas??

thanks in advance!! ;)

---

### Post by dcstar on 2012-04-15
> **motomixon said:**
> 
.........
What is going on here and how to fix it??
Actually, I would like to try Evolution out, but am blocked. And otherwise I would like to repair an obvious fault in my Ubuntu installation.

Any ideas??

thanks in advance!! ;)

Use Synaptic to look at your packages and do a Fix Broken Packages.

---

### Post by motomixon on 2012-04-16
Thanks for the tip, David.

Apparently, more things were (are) screwy on this system. First Syn Pac Man would not load. After authentication it flashes and shuts down.a

The answer to this problem can be found [here]("http://askubuntu.com/questions/69474/synaptic-package-manager-keeps-crashing")  
Here is a quote:
"It appears that it's related to accessibility settings. I was able to fix this problem on my system by opening Universal Access, enabling then disabling the screen reader, then opening Synaptic again."
This might prove useful to others.

Then Syn Pac Man gave me the error:
"Unable to correct problems, you have held broken packages."
And this fixed that:
sudo apt-get clean && sudo apt-get update

Finally I got Syn Pac Man working and discovered that I still had Evolution installed, but it's launcher was absent. So I uninstalled it and that cleaned up my Update Manager display!!!
Finally!):P

---

