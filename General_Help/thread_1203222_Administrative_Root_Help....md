---
title: "Administrative Root Help..."
date: 2009-07-03
forum: General Help
---

### Post by exeon on 2009-07-03
Hi All

I have been search for a solution but I have been unable to find one. I have just installed xubuntu 9.04 on my playstation 3. I am trying to update the repositories by typing:

*sudo apt-get update*

It asks for my password and then returns:
[I]
user is not in the sudoers file. This incident will be reported.[/I]

I did set a password during the installation and a proper username. I reinstalled because I thought I had made a mistake. If I try to goto Users and Groups, I dont have privileges to. If I goto the Synaptic Package Manager it prompts for my password and I enter it and it doesnt let me.

I have tried to turn on the root user by doing sudo passwd but no luck.. Can anyone help me? Thanks

-Andrew

---

### Post by coffeecat on 2009-07-03
Have a look at this:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

You probably need to boot into recovery mode and then from the command line, run the command:

```
adduser *username* admin
```


... substituting your user name for 'username', but check through that link first.

---

### Post by exeon on 2009-07-03
Thanks for the info coffeecat. There is one problem. The link tells you how to boot into recovery mode with GRUB but I use kboot. 

I can't seem to figure out how to boot into recovery mode as root with kboot... Anyone know how?

And another thing. Could it be that I installed xubuntu with the encryption option? I came across something that said doing this might mess up user accounts and passwords.

---

### Post by exeon on 2009-07-03
Nevermind I found it. Could this be a bug when installing 9.04 on a ps3?

Heres a link for anyone else if they run into the problem:
[http://ubuntuforums.org/showthread.php?t=1171457&highlight=kboot+recovery+mode](http://ubuntuforums.org/showthread.php?t=1171457&highlight=kboot+recovery+mode)

---

