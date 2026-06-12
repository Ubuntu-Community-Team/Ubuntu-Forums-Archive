---
title: "Unity is not working"
date: 2011-05-21
forum: General Help
---

### Post by 381hfk328fn38d1 on 2011-05-21
.

---

### Post by Hedgehog1 on 2011-05-21
After installing Ubuntu from a LiveCD/LiveUSB, these steps were not necessary.

Here is the 'typical' list you would do for these commands:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

You can try that 3rd command and see how it goes.

However, in your case I think a reinstall of natty over the old install might be best.

Do you need assistance with that?

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-21
In case you choose to reinstall 'over the top' of your current natty:

Start the install again, and select 'SOMETHING ELSE' in the 'allocate disk' option

First, define your '/' (root) partition to use the current one:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then, if you are using a seperate '/home' partiton, define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE OR REINSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by 381hfk328fn38d1 on 2011-05-21
.

---

