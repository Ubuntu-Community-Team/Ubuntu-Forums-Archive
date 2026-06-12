---
title: "sudo command doesn't work anymore"
date: 2011-01-21
forum: General Help
---

### Post by 1v82TIn1 on 2011-01-21
I was changing some file permissions with the chmod 777 command and i accidentally executed:

```
sudo chmod 777 /*/*/*/*
```

and now i can't get root access to anything.

If I try executing a sudo command i get:

sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting

Could somebody please help.

Sincerely,
Ryan Brothers

---

### Post by jocko on 2011-01-21
You could perhaps boot into recovery mode and change the permission on the sudoers file, but I'm pretty sure there are lots of other things that will misbehave after you gave them the wrong permissions...
I think a clean install is your only reasonable option.

---

### Post by kanishkdudeja on 2011-01-21
you might want to have a look at this:

[http://serverfault.com/questions/221447/how-to-repair-restore-ubuntu-10-04-after-sudo-chmod-777](http://serverfault.com/questions/221447/how-to-repair-restore-ubuntu-10-04-after-sudo-chmod-777)

---

### Post by santoshbarwa@gmail.com on 2011-07-15
can somebody help me.......

**in ubuntu 10.04:**

i gave full permission to /etc directory by entered below command and i renamed ocsinventory-aget name into ocsinventory-agent11.
 
$$ **sudo chmod  777 -R /etc/**

After this whatever i am trying it is showing like this.

sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting

So i need to give old permission to /etc, so what i will do.....**.Helpme.....**

---

### Post by wildmanne39 on 2011-07-15
Hi, here is a guide for fixing sudoer file I hope it helps.
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by raja.genupula on 2011-07-15
> **santoshbarwa@gmail.com said:**
> can somebody help me.......

**in ubuntu 10.04:**

i gave full permission to /etc directory by entered below command and i renamed ocsinventory-aget name into ocsinventory-agent11.
 
$$ **sudo chmod  777 -R /etc/**

After this whatever i am trying it is showing like this.

sudo: /etc/sudoers is mode 0777, should be 0440
sudo: no valid sudoers sources found, quitting

So i need to give old permission to /etc, so what i will do.....**.Helpme.....**


have you followed the above link ?

---

### Post by santoshbarwa@gmail.com on 2011-07-15
[QUOTE=raja.genupula;11049547]have you followed the above link ?[/QUOTE

Actually i need to give old permission to /etc what ever i changed .

and i tried this command it is showing like this.


$chmod 0440 /etc/suders


$chmod: cannot access `/etc/suders': No such file or directory

---

### Post by santoshbarwa@gmail.com on 2011-07-15
$chmod 0440 /etc/sudores

it is showing like this.

chmod: changing permissions of `/etc/sudoers': Operation not permitted

---

### Post by wildmanne39 on 2011-07-15
Hi, double check the spelling it should be.
```
chmod 0440 /etc/sudoers
```

---

### Post by jocko on 2011-07-16
> **santoshbarwa@gmail.com said:**
> $chmod 0440 /etc/sudores

it is showing like this.

chmod: changing permissions of `/etc/sudoers': Operation not permitted
Since you have broken sudo by changing the permissions on the sudoers file, you of course have to run that command logged in as root. So reboot into recovery mode, drop to a root terminal and try:
```
chmod 0440 /etc/sudoers
```

---

### Post by Dangertux on 2011-07-16
I am somewhat curious. Why did you change permissions recursively like that?

---

