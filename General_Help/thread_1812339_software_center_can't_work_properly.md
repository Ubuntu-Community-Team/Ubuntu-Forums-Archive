---
title: "software center can't work properly"
date: 2011-07-26
forum: General Help
---

### Post by papertigerv5 on 2011-07-26
hi, guys, i meet a problem recently while i try to install a software via software center.
After i start the software center, i input the name of software into the input filed. The panel keep the status of searching with nothing return.
While i click the installed software, the right panel show nothing but the icon showing processing.
My network works perfect, i can install software using the terminal.
The ubuntu version i used is 10.14.
Pls help me out, i can't stand such problem and it torture me a lot.
Thx in advance

---

### Post by thefasterblueone on 2011-07-26
Try installing using the Terminal so you can read any error messages that might appear.

Also 

```
sudo apt-get update && sudo apt-get upgrade
```

won't hurt either.

---

### Post by papertigerv5 on 2011-07-26
> **thefasterblueone said:**
> Try installing using the Terminal so you can read any error messages that might appear.
 
Also 
 
```
sudo apt-get update && sudo apt-get upgrade
```
 
won't hurt either.
 
Thx reply. thefasterblueone.
To my wired, there is no error inform. I can install the software use sudo apt-get install command to install the software, sudo apt-cache search would work either. But i want to read some information about this software as the software center show.

---

### Post by thefasterblueone on 2011-07-26
In Terminal,to show package information.

```
sudo apt-cache show 'package name'
```

More information on 'apt-cache'

```
man apt-cache
```

Hope this will help you.

---

### Post by papertigerv5 on 2011-07-26
> **thefasterblueone said:**
> In Terminal,to show package information.

```
sudo apt-cache show 'package name'
```More information on 'apt-cache'

```
man apt-cache
```Hope this will help you.

yeah. It works . Thx

---

