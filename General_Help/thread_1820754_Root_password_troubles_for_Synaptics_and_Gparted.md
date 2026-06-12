---
title: "Root password troubles for Synaptics and Gparted"
date: 2011-08-08
forum: General Help
---

### Post by Neraste on 2011-08-08
Hello everyone!

Something strange occurs with my root password on my Ubuntu Studio 11.04...

On the terminal, when I'm asked to enter my root password, no problem.
On most of the GUI windows that ask me the same thing, no problem too.

**But**, when I open **Synaptic** or **Gparted**, a diferent window appears for my root password and when I enter it, I'm told :
> Unable to laucnh /usr/sbin/synaptic as root

Fail at communicating with gksu-run-helper

Recieved:
su: authentification failed
What was wanted:
gksu: waitingWhat's wrong ? I enter the right root password and it's always he same thing.

I add that my Ubuntu has had a "unusual" installation, since I have had to install the Ubuntu Studio packages manually with **apt-get** ([here]("http://ubuntuforums.org/showthread.php?t=1796117"), the topic of my installation problem). It may be the cause of my troubles; since I've installed Ubuntu, I've never be able to launch Synaptic...

Thank you for your help!

---

### Post by sikander3786 on 2011-08-08
Press Alt + F2 and type:

```
gconf-editor
```

Importantly, temember not to include sudo or gksudo

Navigate to /apps/gksu and make sure sudo-mode is ticked. If not, that is the problem.

---

### Post by Neraste on 2011-08-09
My question was certainly sounding stupid...

Thank you, **sikander3786**, now it works fine and I have access to Synaptic.

---

