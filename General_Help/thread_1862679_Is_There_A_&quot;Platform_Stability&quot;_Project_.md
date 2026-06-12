---
title: "Is There A &quot;Platform Stability&quot; Project or Group?"
date: 2011-10-17
forum: General Help
---

### Post by 0c-bill on 2011-10-17
Hi!  I've been having alot of stability problems over the last few years.  This has prompted me to wonder if there is anyone out there who is developing a method of systematically testing a platform against common usability issues?

My example is a core i7 pc with an nvidia-based video card that will freeze with the wrong combination of kernel/nvidia-drivers.  This is one of those freezes where even an sshd running independantly of session won't respond to an ssh attempt.  LOL there are just too many variables involved in this kind of issue. Is it hardware? Software?  Are there hardware bugs that must be compensated for, but the vendors won't tell anyone because it's proprietary?  Maybe a slightly-faulty card/motherboard?  

Doesn't really matter.  Either it can be made to work or it can't.

I'm looking to see if anyone is developing a good method of testing a platform against instability with an eye for a guide to finding problems, work-arounds, and how to keep from deep-sixing all that work with one careless automatic update.. :P

OR advice on how to start up such a project from someone who's experienced with such things. :P

Bill

---

### Post by ubuntu27 on 2011-10-17
This doesn't answer your question, but I thought it might be *interesting* for you.

[Ubuntu Friendly]("http://www.omgubuntu.co.uk/2011/10/ubuntu-friendly-what-it-is-and-how-you-can-help/") -- "Ubuntu 11.10 users are being encouraged to take part in ‘Ubuntu Friendly’ – a community-drive database of desktops, laptops and netbooks that work well with Ubuntu."

******

It seems that there are no "stability team" of sort (I could be wrong). You could join the **[Bug Squad]("https://wiki.ubuntu.com/BugSquad")** since what you describe is a collection of bugs.

Even if you do not [want to] become a Bug Squad, you could just be a Bug Reporter"

Here is a [Beginners Guide to Filing Bug Reports]("http://ubuntuforums.org/showthread.php?t=1011078")


Other ways to help or contribute to Ubuntu Linux can be found [here]("http://www.ubuntu.com/community/get-involved") and [here]("https://wiki.ubuntu.com/ContributeToUbuntu").

*************

I hope someone will be able to answer your questions.

---

### Post by Someone uk on 2011-10-17
it's usually a choice, you can either have lots of features added or you can have stability, the latest ubuntu releses seems to focus more on features

stability is achieved by not adding features but refining and bug fixing what exists
the closest thing i can think of as "platform stability" are LTS releases where the software is used for a long time and bugs are fixed rather than features are added

the most stable ubuntu release will probably be [10.04.3](http://releases.ubuntu.com/lucid/) (a revised 10.04 image made this year) or of course there is debian, once debian is configured correctly it'll work every day without fail

but back to your original problem i would say from my experience, nvidia are terrible when it gets to their propritry drivers, my experience left be to never buy anything nvidia again
if you don't need 3d i have found noveau to be more linux friendly and tend to never run into issues

---

### Post by 0c-bill on 2011-10-17
> **ubuntu27 said:**
> This doesn't answer your question, but I thought it might be *interesting* for you.

[Ubuntu Friendly]("http://www.omgubuntu.co.uk/2011/10/ubuntu-friendly-what-it-is-and-how-you-can-help/") -- "Ubuntu 11.10 users are being encouraged to take part in ‘Ubuntu Friendly’ – a community-drive database of desktops, laptops and netbooks that work well with Ubuntu."

******

It seems that there are no "stability team" of sort (I could be wrong). You could join the **[Bug Squad]("https://wiki.ubuntu.com/BugSquad")** since what you describe is a collection of bugs.

Even if you do not [want to] become a Bug Squad, you could just be a Bug Reporter"

Here is a [Beginners Guide to Filing Bug Reports]("http://ubuntuforums.org/showthread.php?t=1011078")


Other ways to help or contribute to Ubuntu Linux can be found [here]("http://www.ubuntu.com/community/get-involved") and [here]("https://wiki.ubuntu.com/ContributeToUbuntu").

*************

I hope someone will be able to answer your questions.
Thanks for your advice ubuntu27!
  I might try the bug-squad.  I can also contribute data to the "ubuntu friendly" site; but that venue is nearly useless for many of the problems I've experienced; since not every machine is "branded".

In any case, if there's already an effort to make it more reliable, then that is worth exploring. :)

Bill

---

### Post by 0c-bill on 2011-10-17
> **Someone uk said:**
> it's usually a choice, you can either have lots of features added or you can have stability, the latest ubuntu releses seems to focus more on features

stability is achieved by not adding features but refining and bug fixing what exists
the closest thing i can think of as "platform stability" are LTS releases where the software is used for a long time and bugs are fixed rather than features are added

the most stable ubuntu release will probably be [10.04.3](http://releases.ubuntu.com/lucid/) (a revised 10.04 image made this year) or of course there is debian, once debian is configured correctly it'll work every day without fail

but back to your original problem i would say from my experience, nvidia are terrible when it gets to their propritry drivers, my experience left be to never buy anything nvidia again
if you don't need 3d i have found noveau to be more linux friendly and tend to never run into issues
Someone uk;

I have to agree that lucid lynx was the least troublesome version for me so far.  And, unfortunately, I need 3d acceleration for several of my main focuses.  

Maybe one of the graphics card manufacturers out there will become a linux supporter...

Bill

---

### Post by 0c-bill on 2012-07-07
With the help of some friendly people in the Linux department of Nvidia and a brand new AMD graphics card (tested the system with 3 different cards total).  I have come to the conclusion that the issue is an obscure incompatibility between the ASUS P6TD deluxe motherboard and the recent Linux Kernel builds from Ubuntu. But, it's still intermittent and I can't prove the culprit.

I am FINALLY closing this thread as I have given up on a solution and purchased a system76 desktop.

---

### Post by 0c-bill on 2012-07-07
Woops!

Looks like I don't hav the power to close my own thread...

OK, so it's marked 'SOLVED'.

Though it's not much of a solution to solve it by completely replacing the machine...

---

