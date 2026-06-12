---
title: "gksudo password timeout don't work."
date: 2012-02-29
forum: General Help
---

### Post by ohnonot on 2012-02-29
hello everybody,

this little problem is driving me mad.
i now managed to add "passwd_timeout=20" to sudoers
(took me hours of rebooting finding out the syntax. should google more before doing things ;-)

but the problem is the same:
password timeout works only from one terminal session, whether it is sudo or gksudo or gksu.
if i use gksu without terminal or close the terminal and then use sudo/gksudo/gksu again, i always have to give my password.

can someone help?

---

### Post by ohnonot on 2012-03-10
...anybody?

maybe i should add:
i would like to give my password once and then be able to do superuser things for about 20 mins before having to give it again.

as i know works with most ubuntu/gnome distros.

the situation now is that i have to give my password every time when any type of *su* starts - even after half a minute. the only exception is when i use sudo several times from within one terminal window.
so it would seem that the password timeout is there and being recognized partly.

i did quite some search on forums and help pages but found nothing on this problem.

the relevant line in sudoers: ```
Defaults    env_reset,passwd_timeout=20
```

---

### Post by sudodus on 2012-03-10
What distro/version/flavour are you running? I think what you describe is normal (that it only works in the same terminal).

An obvious work-around is to start a ```
sudo -i
``` session, but then you have the opposite problem: It will be available 'forever' or until you exit, which might risky depending of where you are and how you work.

---

### Post by ohnonot on 2012-03-10
ah, that was quick. thanks. it's xubuntu 11.10.
...
> as i know works with most ubuntu/gnome distros.
- i might have been wrong about this. just asked my girlfriend who's using ubuntu 10.04, but she's only using sudo from the terminal.
maybe i remember it from linux mint or some other distro i tried...

anyway it's what i would like to accomplish.
without starting a root session.

---

### Post by mc4man on 2012-03-10
Starting with sudo 1.7.4 the timeout is only per instance, previously it was for all during the set time.
The only way to change that with 1.7.4+ is to use !tty_tickets which *I don't like at all.*
Or return to 1.7.2 which I'm okay with, others may feel differently about that..

thread on from a year ago
[http://ubuntuforums.org/showthread.php?t=1648577&page=2](http://ubuntuforums.org/showthread.php?t=1648577&page=2)

---

### Post by ohnonot on 2012-03-10
thanks mc4man, this was really helpful also i see that my memory did not fail me (i had a derivate of lucid lynx lts installed before).

i see that disabling tty-tickets would give remote users the possibility to sudo my computer, but i really could not be bothered at this point and used this quick solution.

also i did not find a way to download sudo 1.7.2p7-1ubuntu3 as a .deb - and frankly i'm a bit frightened to downgrade (=mess around?) with such an important package.

however your link gives the answers i was looking for. thanks again.

---

