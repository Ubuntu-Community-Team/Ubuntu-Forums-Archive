---
title: "Repos messed up"
date: 2010-08-16
forum: General Help
---

### Post by MikeHunt on 2010-08-16
A few days ago I added Linux Mint repos to my sources list, let's skip this part where I would explain why. Today I ran update and some things got messed up (attachment).

The question is, how to change back to default?

---

### Post by wojox on 2010-08-16
You just need to remove Linux Mint repos from your sources.list. How did you add them to begin with?

---

### Post by darolu on 2010-08-16
Open a terminal, go to /etc/apt/sources.list.d/, the Linux Mint repo lines should be there, remove them and then run "apt-get update":
```
:~$ cd /etc/apt/sources.list.d/
:/etc/apt/sources.list.d$ ls
bluefish.list  linuxMin.list  opera.list  vlc-korn.list
:/etc/apt/sources.list.d$ sudo rm linuxMin.list
:/etc/apt/sources.list.d$ ls
bluefish.list  opera.list  vlc-korn.list
:/etc/apt/sources.list.d$ sudo apt-get update
```
Then you can upgrade or reinstall whatever software you need.

If you don't see a linux-mint file in sources.list.d/ edit the /etc/apt/sources.list file.

---

### Post by MikeHunt on 2010-08-16
@up & @2up
No change. Still default ver is Mint's.

Clearing packages cache does not work, the only way seems to be forcing Synaptic to use specific version (ctrl+e). But then no updates will be available. Any other suggestions?

---

### Post by wojox on 2010-08-16
Post back from the terminal:

```
ls /etc/apt/sources.list.d/
```

and 

```
cat /etc/apt/sources.list
```

---

### Post by MikeHunt on 2010-08-16
Thanks everyone, managed to fix this myself.

Uno. Sources.list etc was clean, no traces of Mint detected :P
Dos. Synaptics is not stupid. 2.2-2-_1_mint1 > 2.2-2, maths can't lie.
Tres. [http://bazaar.launchpad.net/~ubuntu-security/ubuntu-security-tools/trunk/annotate/head%3A/utilities/downgrade-all]("http://bazaar.launchpad.net/%7Eubuntu-security/ubuntu-security-tools/trunk/annotate/head%3A/utilities/downgrade-all")


Have a nice day/night/whatever
MH


P.S: Just because I have less than 10k posts doesn't mean I can't be a power user.

@down
Most.

---

### Post by wojox on 2010-08-17
> **MikeHunt said:**
> 
P.S: Just because I have less than 10k posts doesn't mean I can't be a power user.

Most power user's don't add Mint's repo's to their sources.

---

