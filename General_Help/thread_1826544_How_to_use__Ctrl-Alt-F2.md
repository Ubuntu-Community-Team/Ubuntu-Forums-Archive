---
title: "How to use  Ctrl-Alt-F2?"
date: 2011-08-16
forum: General Help
---

### Post by peoplegetpeople on 2011-08-16
after you hit ctrl+alt+F2 it says < [username]login: > i've tried a thousand different lines here and everytime it asks for password then says wrong login. what am I missing?

---

### Post by Iowan on 2011-08-16
Moved from [this]("http://ubuntuforums.org/showthread.php?p=11158747") thread.

From Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Ctrl-Alt-F2 will open a terminal window. The prompt will be the machine name followed by **login:**
What it wants is the username to login - it takes whatever comes next as the username, and then prompts for a password for that user. If you have issued a command, there is probably no user by that name, so no password will work. For my machine, the sequence normally looks something like:```
mymachine login:
mymachine login: **iowan**
Password:
Welcome to Ubuntu 11.04...

``` 
Notice that the password does not echo - not even "*"s

I suppose it might be worth asking what you are trying to do. There's a *similar* command ALT-F2 that brings up a "Run Application" window.

---

### Post by peoplegetpeople on 2011-08-17
> **Iowan said:**
> Moved from [this]("http://ubuntuforums.org/showthread.php?p=11158747") thread.

From Code of Conduct:

Ctrl-Alt-F2 will open a terminal window. The prompt will be the machine name followed by **login:**
What it wants is the username to login - it takes whatever comes next as the username, and then prompts for a password for that user. If you have issued a command, there is probably no user by that name, so no password will work. For my machine, the sequence normally looks something like:```
mymachine login:
mymachine login: **iowan**
Password:
Welcome to Ubuntu 11.04...

```Notice that the password does not echo - not even "*"s

I suppose it might be worth asking what you are trying to do. There's a *similar* command ALT-F2 that brings up a "Run Application" window.

Yeah, my apologies about replying to an old post, i'm not new to forums so I should have known better - honestly I didn't even think to look - cause they're all new to me! :D 
anyhow, thanks a lot for the reply - I initially had made some changes in CompizConfig that rendered my desktop unresponsive and useless (trying to enable cube) the only response i could get was ctrl+alt+f2 and was getting extremely frustrated that I couldn't even figure out how to get out of it! lol - I have since resolved it via another post which actually prompted me to join the forum just to say thanks to the poster with the solution.

So anyway, sorry for the novel and thanks for the clarification!

---

### Post by seawolf167 on 2011-08-18
If you have it solved, please mark the thread as solved under thread tools.

One handy thing you may need in the future that helps restore a frozen gui session is to enter a tty (via [CTRL][ALT][F1-6]), then restart the gui

```
sudo service gdm restart
```

Note that if you enter a tty and want to go back to your GUI without restarting it you can simply hit [CTRL][ALT][F7] to go back to your desktop

---

