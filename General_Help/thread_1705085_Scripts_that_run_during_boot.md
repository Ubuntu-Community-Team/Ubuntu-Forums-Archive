---
title: "Scripts that run during boot"
date: 2011-03-11
forum: General Help
---

### Post by eckeroo on 2011-03-11
Hello all,

I have a script, somewhere, that runs during start up which I want to amend. However, I'm not familiar with the Ubuntu initialisation routine.

What file (presumably somewhere in the /etc/ directory) runs custom scripts during start up?

I need to find this script as it starts my wireless connection and I want to know how to disable it so I can use network manager instead.

Regards

---

### Post by lithopsian on 2011-03-11
You wrote a script and you don't know where you put it?  Might be hard for us to guess ;)

Does it run from /etc/init/rc or from upstart?  Look in /etc/init., /etc/rcS.d, and /etc/rc2.d.  Check /etc/rc.local.

---

### Post by eckeroo on 2011-03-11
#-o

What had happened was this:

I followed a thread with instructions on how to setup an internet connection from boot. It worked a treat, except I can't find that old thread now and I want to undo those changes.

---

### Post by eckeroo on 2011-03-11
I think I may have a clue: [http://ubuntuforums.org/showthread.php?t=885847&highlight=networking+boot&page=3](http://ubuntuforums.org/showthread.php?t=885847&highlight=networking+boot&page=3)

there's this little snippet

[PHP]cd /etc/init.d
sudo -s
chmod +x wifi-fix.sh
update-rc.d wifi-fix.sh[/PHP]

now, I have no wifi-fix.sh. I checked with 'find / -name wifi-fix.sh'

what does that 'update-rc.d' command do?

---

### Post by eckeroo on 2011-03-12
SOLVED!!!!!!

The thread I followed was this

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

There were no scripts. That's why I couldn't find any.

:cool::cool::cool::cool::cool::cool::cool::cool:

---

