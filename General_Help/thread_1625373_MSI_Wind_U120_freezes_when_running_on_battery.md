---
title: "MSI Wind U120 freezes when running on battery"
date: 2010-11-19
forum: General Help
---

### Post by bokamba on 2010-11-19
I have an MSI Wind U120 netbook (Intel Atom N270 1.6GHz processor, 1 GB RAM). I'm running Ubuntu 10.10 Netbook Remix. Ever since upgrading to Ubuntu 10.10 from 10.04, my system has experienced unrecoverable freezes when running on battery.

The system reliably freezes when resuming from the suspend or hibernate modes when running on battery. It seems to load back up successfully but then freezes before I get a chance to enter my password.

Yesterday and today I also noticed that the system freezes while idle and running on battery! This is even more disconcerting.

I would be grateful for any help the community can offer in troubleshooting and bug reporting. I have some experience as a Linux user (including using the terminal & editing configuration files) but not much experience as a Linux system administrator.

---

### Post by bokamba on 2010-11-27
Upon further testing the problem is even more serious than I previously thought. Simply removing the power cord caused the system to freeze immediately! I hope someone has some ideas for how I can investigate and fix this, since I would very much like to be able to run on battery when I take a long trip next month.

---

### Post by bokamba on 2010-12-02
I'm kind of dismayed that nobody has responded--surely I'm not the only one who has experienced a problem like this!

---

### Post by bokamba on 2010-12-04
I wonder if the problem could be related to the new Unity interface. How do I go about disabling Unity?

---

### Post by alex_ole on 2011-01-01
Hello there,

I am afraid you are not the only one in this one. I am experiencing the same symptoms myself. The moment I unplug the power my laptop freezes in the next couple of seconds. Also when I try booting without the power cable plugged right after entering the correct log in details I get my HP laptop crashed.

Really... anyone that can share some instructions?

Thanks!

---

### Post by alex_ole on 2011-01-01
Hey... check this one out


[http://ubuntuforums.org/showpost.php?p=10185265&postcount=12](http://ubuntuforums.org/showpost.php?p=10185265&postcount=12)

---

### Post by bokamba on 2011-01-03
Thanks! Did those instructions work for you? If so, are you able to clarify them a bit? They weren't written very clearly and I don't want to risk making a mistake and ending up worse off.

---

### Post by JC Cheloven on 2011-01-03
Hi, it seems to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/531190)

Dunno if the workaround stated there works. You may also check whether what I suggested [here]("http://ubuntuforums.org/showthread.php?p=10310050#post10310050") helps or not.

---

### Post by bokamba on 2011-02-25
Thanks for your help. Due to this problem and another, unrelated problem, I decided to downgrade to 10.04 LTS.

---

