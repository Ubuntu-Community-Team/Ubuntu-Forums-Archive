---
title: "Terminal, how to?"
date: 2012-09-13
forum: General Help
---

### Post by offgridguy on 2012-09-13
I used my first computer with windows OS for  about 4 1/2 years and never heard of a
terminal,  I am realizing now that with ubuntu it is an important working component
of this system.  Where would I find the info  that addresses this function with it's various
command lines?
 Thank you, as always I appreciate the help.:)

---

### Post by steeldriver on 2012-09-13
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

---

### Post by snowpine on 2012-09-13
This page (first Google hit for "Ubuntu terminal" by the way) should get you started: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If you have specific questions, ask away! :)

---

### Post by offgridguy on 2012-09-13
> **snowpine said:**
> This page (first Google hit for "Ubuntu terminal" by the way) should get you started: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

If you have specific questions, ask away! :)

Thank you for the link, I read somewhere " the only dumb questions are the ones
nobody asks"   I won't learn if I don't ask, thanks again.

---

### Post by offgridguy on 2012-09-13
steeldriver,  thank you for the link.

---

### Post by Habitual on 2012-09-13
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html) 
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html) 
[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)
[http://www.grymoire.com/Unix/Sh.html](http://www.grymoire.com/Unix/Sh.html)
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) 
[http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ)
[http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls)

---

### Post by offgridguy on 2012-09-13
Thank you, this is probably enough to hold me for awhile.

---

### Post by houseworkshy on 2012-09-13
I'll add something anyway.  If in the terminal you enter "info info", it will tell you about the built in help.   "man" in front of any command will take you to it's manual page, so "man info" is worth a look.  To find out about commands you don't know "apropos" is useful, it searches through all the manual pages for whatever you entered after the word, so if you knew you wanted to search but didn't know how "apropos search" would pull a list of all the maual pages which use the term 'search'.  You could then use "man" to look at the  candidates and work out which command you wanted and how to use it.  Reading an appropriate guide is a better way of learning, however having authentic referance material which is always available, even off the internet grid, is very useful indeed.

---

### Post by offgridguy on 2012-09-13
Thank you ,this looks very useful.

---

### Post by houseworkshy on 2012-09-13
Offline help is important for another reason. Just as most people prefer to get changed for swimming before rather than after diving in, it's generally a good idea to set up some security before actually going online.  On a default install though a firewall is in the distribution it is not enabled. 
So to set up safe defaults use "sudo ufw default deny", because sudo enables administration powers for 15 minuets you will be asked to provide your password. 
Then "ufw enable" will enable the firewall which will run each time you start up from then on. If you enter the second command quickly it won't need "sudo" in front of it as the timer will still be running, if for some reason it takes longer than 15 minuets to enter the second command you will. 
It's a good idea to stop the timer and kill sudo early when you have finished, especially if browsing. To do that "sudo -k" 
I hope that doesn't seem deep end but I think setting the firewall up before going online matters. It's the only bit which requires command line knowledge on a fresh install, so there is it. One can install graphic managers instead but to do that one goes online.
For more on this "man ufw", "man sudo". 
"man" is probably my most used command. Being new to the command line be cautious of "sudo", you see it all over the forums only because admin powers are often needed to install and fix things.
 
I've been on this forum for a while and haven't seen one yet but there is a warning sticky about malicious commands being posted. So the habit of using "man" to understand what advice you have seen rather than simply copy and pasting it on trust is a good one to develop. It is also one of the best ways of learning.
These links may be useful too
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)

Don't let the huge amount of info daunt you, most things can be done in the gui anyway. So whilst highly useful ( and universal to all distro's ) it's not crucial, it's something you can learn at your own pace. Slightly like early Windows in a way, even though DOS sat under everything windows did, many of it's users never touched it. 
Get familiar with a few commands you are likely to use a lot and add more at your own pace. I'd start with the looking at but not doing anything commands first, can't do damage with those. Once those are under the belt you'll understand the format of the man pages, which is standardised, and be less likely to misunderstand them when you come to use the doing things commands.

There are a lot of commands, over six hundred when last I looked,  and I doubt there are many who know the lot and I don't know of a distro which has all of them.  Usually people know a couple of dozen that everyone uses and a bunch of extra ones associated with whatever they do a lot, maintaining networks or researching theoretical mathematics as examples. Linux is one subject where even a little knowledge is still useful.  Don't feel you have to know the lot in order to be competent.
Have fun.

---

### Post by offgridguy on 2012-09-13
Thanks again, this is the kind of info I was hoping for, real stuff that works for real people.
The tutorials are good but often you follow the instructions only to find it isn't working like it said,usually because the tools they describe don't come up,  then I'm saying i wish there was someone
to ask.  I'm glad I started with windows, it is a lot friendlier to the computer illiterate, however this
learning curve is nothing but good for me.

---

