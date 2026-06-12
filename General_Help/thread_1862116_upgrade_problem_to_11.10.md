---
title: "upgrade problem to 11.10"
date: 2011-10-16
forum: General Help
---

### Post by mar11 on 2011-10-16
Hi all,

I tried yesterday to upgrade my ubuntu 11.4 to 11.10. But during the upgrading, more precisely during the  installing of the downloaded packages I got an some errors which told me the some loader can't be installed, may be because at that moment I lost the internet connection, and finely I got a error message after the installation completed that the upgrade is failed.

As I restarted my laptop I noticed that the new version 11.10 is installed but I know that he upgrade isn't not successfully completed.

Now I have tow questions:

1- Do I have any possibility to recover the old version 11.4 again without needing to install the OS from scratch?

2- How can I repair the corrupted upgrade? 


One of the consequence I have now that the ubutu 11.10 does not recognize my Andriod smart phone. This problem I never hat by ubuntu 11.4.


Any Suggestions are very welcome.


My best regards.

---

### Post by mar11 on 2011-10-16
please guide me to a solution..

---

### Post by Bobonov on 2011-10-17
As any operating system is not possible to downgrade (or better... with linux is possible but require a lot of acking and anyway can easily lead to a broken system)

So lets see how to finish the upgrade.
At fist, from the terminal, type the following

sudo -s

and enter the password, this will prevent you to have to type sudo for all the commands.

then try to run 
apt-get update
apt-get dist-upgrade

If. it run without problem wait untill it ends and you upgrade is done
But probably it will complain about anothe program loking the process, somenthing like:

E: Impossible to the the lock /var/cache/apt/archives/lock

(the message is not exactly this, I translated it form the italian one)
or something similar.
The lock file can be different also because it depeneds at which point the process stopped.

just remove the lockfile

rm /var/cache/apt/archives/lock

and try again.

apt-get update
apt-get dist-upgrade

at this point it should go on or tell you to run:

dpkg --configure -a

so run it an wait the process to end.

At this point you should be ok.

---

### Post by cblanquer on 2011-10-18
My upgrade went worse: the pc got locked and after 1 h I had to restart.
I have got several error messages and after "dpkg --config -a" it seemed to complete the upgrade.
But at restart, no more graphics, I do not even get to a start screen. I must probably install from zero.
(no upgrade then on my other computers until I am sure this is safe)

---

### Post by stanley82 on 2012-01-19
With a blank screen how do you open a terminal?
For dummies Ctl+Alt+T or simply is it F6 or F2 and I think they open different sorts of terminals.

> **Bobonov said:**
> As any operating system is not possible to downgrade (or better... with linux is possible but require a lot of acking and anyway can easily lead to a broken system)

So lets see how to finish the upgrade.
At fist, from the terminal, type the following

sudo -s

and enter the password, this will prevent you to have to type sudo for all the commands.

then try to run 
apt-get update
apt-get dist-upgrade

If. it run without problem wait untill it ends and you upgrade is done
But probably it will complain about anothe program loking the process, somenthing like:

E: Impossible to the the lock /var/cache/apt/archives/lock

(the message is not exactly this, I translated it form the italian one)
or something similar.
The lock file can be different also because it depeneds at which point the process stopped.

just remove the lockfile

rm /var/cache/apt/archives/lock

and try again.

apt-get update
apt-get dist-upgrade

at this point it should go on or tell you to run:

dpkg --configure -a

so run it an wait the process to end.

At this point you should be ok.

---

