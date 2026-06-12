---
title: "How can I disable password`"
date: 2011-09-01
forum: General Help
---

### Post by BlackoutWorm on 2011-09-01
Hey. This problem really goes on my nerves and makes me hate ubuntu, which is not good.
So, is it possible to disable the password or let it only ask for password ones per hour or something?
Because every freaking time I want to install or change something, it asks for that damn password.
There should be a "remember password" button there.
I Know the password is there for security reasons, but I do have the ufw firewall running in the background, plus I prefer to not let the system **** me off rather than having it 100 percent secure.

---

### Post by haqking on 2011-09-01
> **BlackoutWorm said:**
> Hey. This problem really goes on my nerves and makes me hate ubuntu, which is not good.
So, is it possible to disable the password or let it only ask for password ones per hour or something?
Because every freaking time I want to install or change something, it asks for that damn password.
There should be a "remember password" button there.
I Know the password is there for security reasons, but I do have the ufw firewall running in the background, plus I prefer to not let the system **** me off rather than having it 100 percent secure.

If you disable it you leave yourself open to allsorts of potential issues.

It is not about attackers from outside only, it is also about services and scripts running under admin privelege.

which is why sudo exists.

it is possible but the canonical model of using sudo is supported here.

see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

for information sudoers file where things may be changed see here [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by BlackoutWorm on 2011-09-01
Thanks.
So the same goes for leaving sudo open in 10 minutes or so too?
It is basically too risky?

But if that's true. Then that means linux is in more danger than windows when it comes to attacks and stuff like that.
Because I haven't had a virus, bugs, hackers or any sort of attack on my windows 7 yet. And Windows is not password protected at all.

---

### Post by oldos2er on 2011-09-01
I think the default timeout for sudo is 15 minutes, which you can change if you need to. **sudo -i** will give you a persistent root terminal; type **exit** when you're done.

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

---

### Post by agillator on 2011-09-02
The article haqking points you to is the answer to your question. I will simply emphasize the dangers involved, like everyone else. When you work as root, which is what you are doing in effect, you run the major risk of screwing up everything. When you run as root, there are two kinds of people: those who have, and those who will. If you wish to say you haven't, then please add the word 'yet'. This is the voice of experience.

If you insist on doing this, why do it the hard way by screwing around with sudo? You are asking to effectively act as root all the time so just go ahead and put a password on the root account and start signing in as root all the time. At least you will be honest about it to yourself and not mislead yourself into thinking you are protected at least part of the time.

---

### Post by BlackoutWorm on 2011-09-02
> **oldos2er said:**
> I think the default timeout for sudo is 15 minutes, which you can change if you need to. **sudo -i** will give you a persistent root terminal; type **exit** when you're done.

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

Thanks, but the timeout is when I exit synaptic or another sudo program.
I have to type in the password fore every single software I install from the software center.
Why can't it be possible to type in the password when you open the software center instead of every single software you install?

---

### Post by mikejonesey on 2011-09-02
login to tty1 as root, switch to that to run root commands then switch back to tty7 when u have finished...

---

### Post by oldos2er on 2011-09-02
> **BlackoutWorm said:**
> Thanks, but the timeout is when I exit synaptic or another sudo program.
I have to type in the password fore every single software I install from the software center.
Why can't it be possible to type in the password when you open the software center instead of every single software you install?

Have you tried **gksu software-center** ?

---

### Post by BlackoutWorm on 2011-09-02
> **mikejonesey said:**
> login to tty1 as root, switch to that to run root commands then switch back to tty7 when u have finished...
Who and what now?
Sorry but I have no idea what tty is.

Thanks oldos2er, that works:)

---

