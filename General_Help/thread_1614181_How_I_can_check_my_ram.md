---
title: "How I can check my ram?"
date: 2010-11-05
forum: General Help
---

### Post by IL TRIVELLA on 2010-11-05
Hello guys sorry if I open a topic for write that, but I really don't know so, I need to ask, I also try to find it in google, but I didn't find, I have 4gb ram in my pc how I can check with Ubuntu if my ram work correct? and If I have all my ram?

thanks...

---

### Post by Chazz44able on 2010-11-05
Go into terminal and type "sudo lshw" then enter your password

---

### Post by CharlesA on 2010-11-05
Memtest86+ will test the RAM for errors.

---

### Post by raheelsuleman on 2010-11-05
hi there you can check your ram using the following commands:-
top
htop
and also
sudo lshw 
also 
sudo lshw | grep -e size
here you will see all the sizes of storage devices too

---

### Post by Chazz44able on 2010-11-05
That command shows you all of your computer details

---

### Post by IL TRIVELLA on 2010-11-05
```
*-memory
          description: System memory
          physical id: 0
          size: 1942MiB

```

this is what show me with lshw, I'm using the trial version of Ubuntu, I still don't install the OS because I want try that everything is ok, and I don't think so...

---

### Post by CharlesA on 2010-11-05
Try running this please:

```
free -m
```

---

### Post by Verbeck on 2010-11-05
could you post the output of [B]free -m

[/B]

---

### Post by IL TRIVELLA on 2010-11-05
```
ubuntu@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1942        849       1093          0        108        475
-/+ buffers/cache:        264       1677
Swap:            0          0          0
ubuntu@ubuntu:~$ 

```

really strange, because I've 4 gb of ram...

---

### Post by CharlesA on 2010-11-05
Does the BIOS show all 4GB of RAM?

---

### Post by IL TRIVELLA on 2010-11-05
> **CharlesA said:**
> Does the BIOS show all 4GB of RAM?

how I can check that?

---

### Post by CharlesA on 2010-11-05
You'd have to boot into "setup" or whatever it's called when you first turn on the PC.

Usually you'd have to hit Delete or F1 or one of those keys.

---

### Post by IL TRIVELLA on 2010-11-05
[LEFT][IMG]http://img514.imageshack.us/img514/7589/dsc04810v.jpg[/IMG][IMG]http://img186.imageshack.us/img186/213/dsc04809e.jpg[/IMG]I really don't understand why show this, I've 4 gb of ram...:confused:
[/LEFT]

---

### Post by CharlesA on 2010-11-05
It's only seeing 2GB of RAM.

How many sticks do you have in the machine?

EDIT: Unless you upgraded the memory, it'll have one 2GB stick of RAM:

From the specs:

> Up to 2 GB of DDR2 667 MHz memory, **upgradable** to 4 GB using two soDIMM modules.

[http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire5735Z/Aspire5735Zsp3.shtml](http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire5735Z/Aspire5735Zsp3.shtml)

---

### Post by Goldfissh on 2010-11-05
You're only showing 2GB of RAM in that BIOS screenshot... Which is odd if you say you've got 4GB.

---

### Post by Verbeck on 2010-11-05
if you're sure you've got 4 gb ram, try cleaning the RAM slots with something alcoholic/ edit : compressed air is better

---

### Post by CharlesA on 2010-11-05
> **Verbeck said:**
> if you're sure you've got 4 gb ram, try cleaning the RAM slots with something alcoholic

I'd suggest not using regular rubbing alcohol, since it can leave a residue on the contacts.

of course that being said, I use regular rubbing alcohol for cleaning off thermal paste.

---

### Post by Goldfissh on 2010-11-05
Usually if there's a fault with a RAM, the POST check at boot will go mad and start beeping at you. Perhaps the RAM has totally fallen out of place, or there is no power going to the slots?

This is getting far-fetched now though :D

---

### Post by CharlesA on 2010-11-05
> **Goldfissh said:**
> Usually if there's a fault with a RAM, the POST check at boot will go mad and start beeping at you. Perhaps the RAM has totally fallen out of place, or there is no power going to the slots?

This is getting far-fetched now though :D

Yep. If there is a (major) problem with the memory, it won't POST.

My bet is that there's only one 2GB stick in that machine, since that's what it comes with by default.

---

### Post by IL TRIVELLA on 2010-11-05
no I have 2 sticks of 2gb each, and I'm sure because I open my laptop more the one time, so what you suggest me for solve?

---

### Post by CharlesA on 2010-11-05
Try them both separately and see if it doesn't see one of the sticks.

Other then that, reseat both of them and go from there.

---

### Post by IL TRIVELLA on 2010-11-05
ok I  open the laptop, take out the 2 stiks, blown air with my mouth inside and now the computer detect 4 gb, thanks guys =)[IMG]http://img19.imageshack.us/img19/2748/immagineir.png[/IMG]

---

### Post by CharlesA on 2010-11-05
You still can only use 2.93GB, but that's cuz you are using a 32-bit OS.

If you use Ubuntu it should see the whole 4GB.

Please mark the thread as solved from the thread tools menu. :)

---

### Post by oldsoundguy on 2010-11-05
You should be able to use all of that ram in Ubuntu 32bit (but NOT Windows 32bit) provided that PAE was installed (on the newer UBUNTU builds it installs when the system is installed).

But here is the check and the manual install method:
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

---

### Post by IL TRIVELLA on 2010-11-05
> **CharlesA said:**
> You still can only use 2.93GB, but that's cuz you are using a 32-bit OS.

If you use Ubuntu it should see the whole 4GB.

Please mark the thread as solved from the thread tools menu. :)

Sorry I don't understand my computer detect less ram of what I have because I'm using a os at 32bit? so you suggest me to use a os at 64bit?

and what is the Memtest86+??? how I can do???

---

### Post by CharlesA on 2010-11-05
> **oldsoundguy said:**
> You should be able to use all of that ram in Ubuntu 32bit (but NOT Windows 32bit) provided that PAE was installed (on the newer UBUNTU builds it installs when the system is installed).

But here is the check and the manual install method:
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/)

Definitely hit the nail on the head there. :)

> **IL TRIVELLA said:**
> Sorry I don't understand my computer detect less ram of what I have because I'm using a os at 32bit? so you suggest me to use a os at 64bit?

and what is the Memtest86+??? how I can do???

See the above post for the reason.

As for running memtest, you can just boot off a ubuntu cd and select it from the start up menu.

---

### Post by IL TRIVELLA on 2010-11-05
oh sorry, my english is not perfect and sometimes I don't understand all...

I will try to understand how I can do the Memtest86+...

thanks for all =)

---

