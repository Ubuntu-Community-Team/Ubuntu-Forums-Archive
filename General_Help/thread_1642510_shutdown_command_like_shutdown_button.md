---
title: "shutdown command like shutdown button"
date: 2010-12-10
forum: General Help
---

### Post by hyfanious on 2010-12-10
Hi to all
hey guys I'm looking for a command that shutdown/reboot my ubuntu  just same as process that happened when I press shutdown button

In fact I need to close all programs that are running ,first
and then PC shutdown (that happened when I press shutdown button).

---

### Post by wojox on 2010-12-10
[Here]("http://www.cyberciti.biz/faq/shutdown-ubuntu-linux-computer/") I don't feel like typing it all out. ;)

---

### Post by karthick87 on 2010-12-10
Shut down your system immediately 
```
sudo shutdown -h now
```
Shut down your system in 60 minutes
                 ```
shutdown -h 60
```

---

### Post by hyfanious on 2010-12-10
> **karthick87 said:**
> Shut down your system immediately 
```
sudo shutdown -h now
```
Shut down your system in 60 minutes
                 ```
shutdown -h 60
```

hey Guys Please Pay Attention:
I Need A Code TO CLOSE ALL OPEN PROGRAMS FIRST

---

### Post by argedion on 2010-12-10
in a script do this

#Kill all processes you can kill.
kill -9 -1
#then          
shutdown -h now

you may need to do sudo kill and sudo shutdown

---

### Post by cgroza on 2010-12-10
> **argedion said:**
> in a script do this

#Kill all processes you can kill.
kill -9 -1
#then          
shutdown -h now

you may need to do sudo kill and sudo shutdown

That does not close them properly, it kills them with cold blood. This might lead to data loss.

---

### Post by hyfanious on 2010-12-10
> **cgroza said:**
> That does not close them properly, it kills them with cold blood. This might lead to data loss.

EXACTLY

dude if I want to kill them I use shutdown -h now!!!

let me to be more clear:
I have two program that I need they be closed! (not killed) before shutting down,
so , who knows what command runs when we push shutdown button?
obviously it is NOT shutdown -h now (or something like that)

The Question IS:
WHAT COMMAND WORKS BEHIND THE SHUTDOWN BUTTON?
(also restart button)
;)

---

### Post by MooPi on 2010-12-10
Just create a .desktop application that includes shutting down your two applications. Right click desktop for create launcher, Write command and us the launcher as your shutdown button.

---

### Post by hyfanious on 2010-12-10
> **MooPi said:**
> Just create a .desktop application that includes shutting down your two applications. Right click desktop for create launcher, Write command and us the launcher as your shutdown button.

Why No ONE read the Question????

What Command Works Behind The Shutdown Button?????

---

### Post by wojox on 2010-12-11
Are the two programs always the same and if so what are they?

---

### Post by QLee on 2010-12-11
[QUOTE=hyfanious]Why No ONE read the Question????[/QUOTE]

I don't think your assumption is correct.

The shutdown command does an orderly shutdown of the system, not just kill processes as you seem to think.

Perhaps you might get whatever advice you seek if you would be specific about what isn't working for you or what errors are encountered when you try.

In addition, follow poster wojox's advice, it's possible the answer you seek could be dependent on the programs you mean.

Help us to help you, don't snap at those who try, that's likely to make them ignore your question.

---

### Post by hyfanious on 2010-12-11
> **QLee said:**
> I don't think your assumption is correct.

The shutdown command does an orderly shutdown of the system, not just kill processes as you seem to think.

Perhaps you might get whatever advice you seek if you would be specific about what isn't working for you or what errors are encountered when you try.

In addition, follow poster wojox's advice, it's possible the answer you seek could be dependent on the programs you mean.

Help us to help you, don't snap at those who try, that's likely to make them ignore your question.


fine, let's see:
I have two programs :
1.keepassx 2.guayadeque
I use this command "shutdown -h now" with shortkey
this code causes these programs wont be closed properly
and this will has results in that next startup, aforementioned  programs, encountered with problems

excuse for misunderstanding for your helping again.  

](*,)](*,)](*,)

and I say again:
When I press shutdown button , one or some scripts run definitely
whats that script?

---

