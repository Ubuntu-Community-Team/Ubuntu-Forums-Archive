---
title: "How to automatically login a no-gui ubuntu install?"
date: 2009-12-23
forum: General Help
---

### Post by lumix on 2009-12-23
I've only found information on gui-based auto-login, but nothing on console login.  Any ideas?

---

### Post by musashi39 on 2009-12-23
I rmemeber a method from school (ten years ago): We would change the runlevel... I'm not sure how to do this anymore but you want the runlevel for single user mode I think. Good Luck!

---

### Post by Leppie on 2009-12-23
> **musashi39 said:**
> I rmemeber a method from school (ten years ago): We would change the runlevel... I'm not sure how to do this anymore but you want the runlevel for single user mode I think. Good Luck!

single user mode also provides full root access i believe, not sure that is what the op wants.

---

### Post by lumix on 2009-12-23
Thanks for the replies.  I do want to login as a specific, non-root user.  This is because on boot up I want a number of applications and/or shell scripts to run as that user, no one else.

---

### Post by slakkie on 2009-12-23
Then create init.d script for that task, or run them vi /etc/rc.local

It doesn't make sense to have an auto-login on a server tbh.

An init.d script could look like this:

```

#!/usr/bin/env bash

my_user=someusername

start() {
    su - $my_user -c "/the/thing/you/want/to/exec --whatever options --you like"
}

stop() {
    su - $my_user -c "/the/thing/you/want/to/exec-stop"
}

case $1 in
   start|stop) $1;;
   *) echo "Usage: $(basename $0) <start|stop>";;
esac

```

There is no need to login as a particular user just to start applications as that user.

---

### Post by StuartN on 2009-12-23
> **slakkie said:**
> There is no need to login as a particular user just to start applications as that user.

Will this run on a server that resumes after power loss? I mean whether this will be run without any user logging in or being logged in.

---

### Post by lumix on 2009-12-23
> **StuartN said:**
> Will this run on a server that resumes after power loss? I mean whether this will be run without any user logging in or being logged in.

Correct.  And as to whether it makes sense or not...I'll bite:

Take the case of a no-gui mediacenter.  To start, I'll need things like lircd and irexec to be running-the former a true daemon, the latter not so much.  Then, I'll need my control script to accept the input handed to it from irexec and then execute other commands and programs that use command line parameters.  Can that be done without an actual command line (tty) running?

---

### Post by lykwydchykyn on 2009-12-23
Instructions here:
[http://shallowsky.com/blog/tags/boot/](http://shallowsky.com/blog/tags/boot/)

---

### Post by lykwydchykyn on 2009-12-23
> **lumix said:**
> Correct.  And as to whether it makes sense or not...I'll bite:

Take the case of a no-gui mediacenter.  To start, I'll need things like lircd and irexec to be running-the former a true daemon, the latter not so much.  Then, I'll need my control script to accept the input handed to it from irexec and then execute other commands and programs that use command line parameters.  Can that be done without an actual command line (tty) running?

If it can be scripted and executed without user interaction, then it can be run without using an actual tty.  There's effectively no difference, apart from the lack of user interaction.

---

### Post by wkulecz on 2009-12-23
Use cron.  Set the time field to @reboot.

This should get yo started:
[http://jeremy.zawodny.com/blog/archives/001021.html](http://jeremy.zawodny.com/blog/archives/001021.html)

--wally.

---

### Post by lumix on 2010-04-09
> There is no need to login as a particular user just to start applications as that user.

This apparently isn't true.  If I start lircd and irexec from boot scripts (e.g. /etc/rc2.d/S98lirc), irexec isn't able to launch mplayer in a way that it can communicate with lircd.  If I login to the machine as root, kill irexec and start it again, then log off, it works just fine.

Anybody know why this would be?

---

