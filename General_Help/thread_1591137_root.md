---
title: "root"
date: 2010-10-08
forum: General Help
---

### Post by hungerformore on 2010-10-08
i just installed ubuntu how do i set up my root password it didnt prompt me in the setup

---

### Post by Quackers on 2010-10-08
The password you use to get to use root privileges is your normal user password.

---

### Post by sandyd on 2010-10-08
> **hungerformore said:**
> i just installed ubuntu how do i set up my root password it didnt prompt me in the setup
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by hungerformore on 2010-10-08
i go to the terminal and type su - and put the pass i log in with and it says failure

---

### Post by Quackers on 2010-10-08
In Ubuntu use sudo not su

---

### Post by markh789 on 2010-10-08
If you really, really - REALLY have to make a root account it is possible - but I so so sooo suggest that you don't!

To do so, you just use passwd:
$ sudo passwd root

But do know that running things through sudo is like running things as root. But if you only need root for a short amount of time just go:
$ sudo su root

Use:
$ exit

When done, or just use sudo for each command.

And you will be root - which is a lot more suggestable.

[SIZE="5"]**[COLOR="Red"]BEING ROOT IS DANGEROUS![/COLOR]**[/SIZE]

Please, please refrain from being root! There is a good reason why they don't enable it by default. 

Enjoy Ubuntu!

---

### Post by hungerformore on 2010-10-08
so i just typed sudo - and it says command not found

---

### Post by TonyChaos on 2010-10-08
> **hungerformore said:**
> so i just typed sudo - and it says command not found

Do sudo - and type in the password you use to log in. The default password, I suppose you could say.

---

### Post by Quackers on 2010-10-08
sudo precedes a command ( like sudo update-grub, for instance).

---

### Post by Iowan on 2010-10-08
**sandyd** beat me to the RootSudo link. 
I *seem* to remember **sudo -i** as an option, too...

---

### Post by markh789 on 2010-10-08
> **hungerformore said:**
> so i just typed sudo - and it says command not found

Type sudo and your command.

Example,

sudo ls -A

Will run "ls -A" as root privileges. 

You will be authenticated for your password - that is your current accounts password.

If it's saying the command's not found, we have bigger problems, make sure your typing it correctly.

---

