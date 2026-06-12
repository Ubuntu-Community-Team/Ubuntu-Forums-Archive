---
title: "Restart 9.10 and Authentication Prompt"
date: 2009-10-24
forum: General Help
---

### Post by Buschbarber on 2009-10-24
I just installed a clean version of 9.10 64bit on a separate HDD. I also have 9.04 on another HDD.

Unlike 9.04, when I Shut Down or Restart, I am prompted to type in my Password indicating that other users may be Logged In.

Is this normal or do I have a Security Problem?

---

### Post by tommcd on 2009-10-24
I have Ubuntu 9.10 32 bit on my laptop and I don't get this. To see all the users currently logged into your system, open a terminal and type ```
users
```
 On my Ubuntu 9.10 users returns:
```
tom tom
```
On my Slackware desktop users returns:
```
tom tom tom tom tom
```
I'm not sure why there are multiple entries for tom. Anyway, you should not see any users you don't recognize. If you do, then I would be suspicious.
Perhaps 9.10 is picking up the home partition for your 9.04 as well as your 9.10 or something.

---

### Post by Buschbarber on 2009-10-24
> **tommcd said:**
> I have Ubuntu 9.10 32 bit on my laptop and I don't get this. To see all the users currently logged into your system, open a terminal and type ```
users
```
 On my Ubuntu 9.10 users returns:
```
tom tom
```
On my Slackware desktop users returns:
```
tom tom tom tom tom
```
I'm not sure why there are multiple entries for tom. Anyway, you should not see any users you don't recognize. If you do, then I would be suspicious.
Perhaps 9.10 is picking up the home partition for your 9.04 as well as your 9.10 or something.

I am getting just my username, twice, like you. Before, I say a Key icon in the System Tray. I clicked on it and checked Drop the Security, or something like that, and I do not get that same Prompt when I Restart.

---

