---
title: "How to change console color at SSH-connection establish"
date: 2011-07-12
forum: General Help
---

### Post by kordenal on 2011-07-12
Hello!

I have small network at home - three computers.
Often I have establish connection from my computer to another by SSH-protocol in console.
Is it possible to automatic change console profile (color of background and text) at SSH-connection establishment? To avoid confuse who is where.

---

### Post by Habitual on 2011-07-12
I believe this IS possible (although I don't have the instructions to give out, and I am not certain you are asking for them)

an internet search for "customize bash" will yield tons of results.

Some of my favorites for "bash hacking" as it's called are:
[http://wiki.bash-hackers.org/doku.php](http://wiki.bash-hackers.org/doku.php) and 
[http://www.ibm.com/developerworks/aix/library/au-satbash.html?ca=drs-](http://www.ibm.com/developerworks/aix/library/au-satbash.html?ca=drs-) and
the [unix.com](unix.com) forums, and 
google of course.

---

### Post by nothingspecial on 2011-07-12
Change the $PS1 variable for each.

So, for example, give computer 1 green text

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[COLOR="Red"][01;32m\][/COLOR]\u@\h\:\w\\$ '
```

Computer 2 blue text

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[COLOR="Red"][01;36m\][/COLOR]\u@\h\:\w\\$ '
```

And computer 3 yellow

```
PS1='${debian_chroot:+($debian_chroot)}\[\033[[COLOR="Red"]01;33m\][/COLOR]\u@\h\:\w\\$ '
```

---

### Post by kordenal on 2011-07-12
Great thanx !!!

Your answer was helpful.
Problem solved.

King regards.

---

