---
title: "Is there any utility to limit time for kids?"
date: 2011-10-27
forum: General Help
---

### Post by geek2330 on 2011-10-27
I mean, a utility that you can execute and then specify in minutes the time your kid can spend on a session.

I usually have to negotiate with my kids and when I tell them they can be on the computer for 30 minutes they usually keep going (since I'm not necessary paying attention) and spend hours on it.

---

### Post by Silent Warrior on 2011-10-27
I think I heard of something like it, but I don't remember where, when, or what it was called... Or even what distribution it was for. You might as well look through Synaptic or Software Centre while waiting for someone who Knows. It's probably in an Education section.

---

### Post by raja.genupula on 2011-10-27
> **geek2330 said:**
> I mean, a utility that you can execute and then specify in minutes the time your kid can spend on a session.

I usually have to negotiate with my kids and when I tell them they can be on the computer for 30 minutes they usually keep going (since I'm not necessary paying attention) and spend hours on it.

after you switch on the system 
open the terminal and then 

sudo shutdown -h 13:00

then your system will shutdown at the time of 13:00 (i mean 1:00 PM )

all the best.

---

### Post by flipper T on 2011-10-27
well if you are going to do it that way, just enter:

sudo shutdown -h 30

and it will shutdown in 30 minutes time

---

### Post by lykwydchykyn on 2011-10-27
I used to use this:

[https://launchpad.net/timekpr](https://launchpad.net/timekpr)

It allows you to determine when and how long each user can log in.  It also periodically warns a user how long they have left on their session.

I had some problems using it with kdm, and my kids eventually lost actual important data when it cut them off in the middle of working on stuff, so I uninstalled it in exchange for them being responsible of their own accord. :)

---

### Post by satanselbow on 2011-10-27
Or you could use the "at" command as discussed here: [http://ubuntuforums.org/showthread.php?p=9374930](http://ubuntuforums.org/showthread.php?p=9374930)

and combine it with the lock-screen discussed here: [http://ubuntuforums.org/showthread.php?t=496512](http://ubuntuforums.org/showthread.php?t=496512)

Don't tell the kids the password to unlock :popcorn:

---

### Post by SeijiSensei on 2011-10-27
I wrote a [script]("http://ubuntuforums.org/showpost.php?p=10191675&postcount=16") in response to a similar inquiry that lets you specify the start and end times of the period you want to let the computer access the network.  This only controls network access; it doesn't shut down the machine itself.  You could use this script as a starting point for one that controls when the machine can be active.  (Hint: Look into replacing the "ifdown" command with something based on the "shutdown" command.)

---

