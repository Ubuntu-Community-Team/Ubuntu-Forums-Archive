---
title: "Can't login as SU"
date: 2009-09-20
forum: General Help
---

### Post by rcaldera43 on 2009-09-20
I just REinstalled Ubuntu because the 1st install wouldn't reconginze my password when I used terminal and tried to use the command 'su'. This 2nd install... same problem. I was never prompted or asked for, a password for 'root'. It just gave me a username and asked me for a passoword for that username. That password works fine for that username. But what about 'su' priviledges? I swear I was prompted only once for a password. This is the 2nd time I installed this, thinking that maybe I screwed up the 1st time. Is there some kind of universal password for 'root'? Of course, I know there isn't, but what the heck am I doing wrong?

---

### Post by Peacefulpieofdeath on 2009-09-20
You dont have to log in as su ever in ubuntu, you can just put sudo in front of the thing you want to do...

But if ever you want to log in as su its 

sudo su+password

---

### Post by lisati on 2009-09-20
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rcaldera43 on 2009-09-20
Thank you guys. Your responses have cleared it up for me. 
There's nothing like open source and these forums.

---

### Post by steveneddy on 2009-10-04
Why do you have to be root all the time?

I think you just want Ubuntu to be another Windows clone.

---

### Post by tuxxy on 2009-10-04
> **Peacefulpieofdeath said:**
> You dont have to log in as su ever in ubuntu, you can just put sudo in front of the thing you want to do...

But if ever you want to log in as su its 

sudo su+password
```

sudo -i
```

---

### Post by falconindy on 2009-10-04
There's a difference between `sudo su` and `sudo -i`. The former will use the environment described in /root, and the latter will keep the environment of the user who initiated the command. Invoking with -i essentially means that you keep all your aliases and other custom settings from .bashrc, etc.

---

### Post by tuxxy on 2009-10-04
> **falconindy said:**
> There's a difference between `sudo su` and `sudo -i`. The former will use the environment described in /root, and the latter will keep the environment of the user who initiated the command. Invoking with -i essentially means that you keep all your aliases and other custom settings from .bashrc, etc.

Yes but encouraging someone to su is against forums policy.

---

### Post by falconindy on 2009-10-05
> **tuxxy said:**
> Yes but encouraging someone to su is against forums policy.
There's a big difference between using `sudo su` and giving someone directions on how to enable the 'root' account (which IS against the CoC). Admins are free to jump in here, but I don't think anyone's ever gotten an infraction for suggesting the usage of `sudo su`. The end result is the same as `sudo -i` minus the imported user environment.

---

### Post by Giblet5 on 2009-10-05
Wanting to use su is as old as UNIX. That's how WE learned to be really careful...

```
<snip>
```

Use sudo -i instead

Of course, anyone who doesn't know how to do that......

With great power comes great responsibility - I expect a flood of "How do I recover from having done XXXXX as root?"

---

### Post by 3rdalbum on 2009-10-05
> **Giblet5 said:**
> Wanting to use su is as old as UNIX. That's how WE learned to be really careful...

With great power comes great responsibility - I expect a flood of "How do I recover from having done XXXXX as root?"

After reading the previous posts, I'm surprised you're not expecting to be given an infraction.

Rcaldera, don't type in the code that Giblet gave you. Very bad. It enables the root account which is not a good idea on Ubuntu.

Instead, use "sudo" before a command to elevate that command to root. Or, if you want to run a graphical program as root, put "gksudo" before it.

If you want a terminal run as root, use "sudo -i" or "sudo bash"; the latter means "Do the following as root: Run the Bash program".

Another handy idea is to install the "nautilus-gksu" package. When you next log in, you'll be able to right-click files and folders and choose "Open as Administrator".

---

### Post by steveneddy on 2009-10-05
> **3rdalbum said:**
> 

Another handy idea is to** install the "nautilus-gksu" package. When you next log in, you'll be able to right-click files and folders and choose "Open as Administrator"**.

Perfect advice

---

