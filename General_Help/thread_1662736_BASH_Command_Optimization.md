---
title: "BASH Command Optimization"
date: 2011-01-08
forum: General Help
---

### Post by micha8l on 2011-01-08
I'm using BASH to access a shell tool, but to access the shell tool I have to take the following steps every time:

```

$sudo su
$source /etc/profile
$zf.sh

```Is there a way I could make it so I could access the shell tool like this:

```

$sudo su
$zf

```My memory ain't too good for memorizing all these commands, alls I want is a nice platform to create PHP websites without this bother.

---

### Post by zigzag77 on 2011-01-08
Try
```
$ sudo zf.sh
```

You can also define an alias for this command at the end of your ~/.bashrc
```
alias zf="sudo zf.sh"
```

---

### Post by zigzag77 on 2011-01-08
If you really need a root shell for more than one command, simply enter
```
$ sudo bash
```Don't forget to exit the root shell as soon as possible after you're done. You know, you can easily damage your system when working as root...

---

### Post by micha8l on 2011-01-08
I didn't know about "sudo bash" thanks for the reply zigzag, I appreciate it.

The alias thing was the sort of thing I was looking for, and I seem to have it working for root, but not for my user "michael".

I did:

```

sudo su
gedit /root/.bashrc

```Added the following to the .bashrc file and saved it:

PATH=$PATH:/usr/local/zend/bin
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/zend/lib
alias zf="zf.sh"

So now when I login as root I can type zf to bring up the tool, but as user "michael" I still have to type zf.sh. Is there a .bashrc file that applies to every user, inluding root?

---

### Post by micha8l on 2011-01-08
Never mind managed to figure this one out for myself. For aliases that are global stick 'em in: /etc/bash.bashrc

Just a newbie in the Ubuntu world I am, but to anyone using aliases I recommend namespaces to avoid collisions e.g,

alias update = "sudo apt-get update" -  bad
alias alias_update "sudo apt-get update" - better

Thanks again for the help :)

---

### Post by cepal on 2011-11-14
I think "sudo su -" is a lot better than "sudo su", usually solves problems similar to the one described here. More details in "man sudo".

---

