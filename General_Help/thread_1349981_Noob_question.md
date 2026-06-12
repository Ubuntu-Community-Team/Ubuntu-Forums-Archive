---
title: "Noob question"
date: 2009-12-08
forum: General Help
---

### Post by DJ . on 2009-12-08
How do you get rid of this? (show more details says permission denied.)
[IMG]http://img38.imageshack.us/img38/7347/screenshotvd.png[/IMG]

---

### Post by Leppie on 2009-12-08
You need root permissions to copy into that location.
Not sure which filemanager you're using, but you can add root permissions by launching it from a terminal:
```
$gksudo thunar
```
or if you're using nautilus:
```
$gksudo nautilus
```

If you don't have gksudo installed, install it from synaptic or from a terminal:
```
$sudo apt-get install gksudo
```

---

### Post by jobix on 2009-12-08
Check the ownership and the permissions on that directory. If you can show us the output of "ls -l that_directory_name", that might help. Typically most directories in the /usr/share directory are owned by root.

---

### Post by DJ . on 2009-12-10
> **Leppie said:**
> You need root permissions to copy into that location.
Not sure which filemanager you're using, but you can add root permissions by launching it from a terminal:
```
$gksudo thunar
```or if you're using nautilus:
```
$gksudo nautilus
```If you don't have gksudo installed, install it from synaptic or from a terminal:
```
$sudo apt-get install gksudo
```
gksudo does not exist.

```
dj@ubuntu:~$ sudo apt-get install gksudo
[sudo] password for dj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gksudo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gksudo has no installation candidate

```

---

### Post by cariboo on 2009-12-10
Try:

```
apt-get install gksu
```

---

### Post by Chesamo on 2009-12-10
Or you could just simply sudo thunar. I've never found a need for gksudo, since sudo works just fine 99% of the time.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) (I disagree with the opinion, but information regarding the differences is there)

---

### Post by synapsys on 2009-12-10
> **Chesamo said:**
> Or you could just simply sudo thunar. I've never found a need for gksudo, since sudo works just fine.

running sudo with a graphical application is dangerous.
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

gksu comes installed by default.....

---

### Post by Chesamo on 2009-12-10
> **synapsys said:**
> running sudo with a graphical application is dangerous.
Only sometimes. Usually, you want Nautilus/Thunar launched with the user's configuration, not root's, and sudo works fine with both of them.

EDIT: Amusing how we linked the same page. Go Google!

---

### Post by SuperSonic4 on 2009-12-10
Or you could use cp from a terminal

```
sudo cp defy /usr/share/games/fretsonfire/data/songs/sectoid/Escape\ from\ chaosland
```

You will have to be in the directory in which defy is in first to copy

---

### Post by joes7 on 2009-12-10
You don't have enough permissions. Log in as the "root" user, it should let you move it.

---

### Post by Chesamo on 2009-12-10
> **joes7 said:**
> You don't have enough permissions. Log in as the "root" user, it should let you move it.
Ubuntu disables root by default. (Also it's against forum rules to tell people how to enable root.)

---

### Post by john987654321 on 2009-12-10
you usually need root to change files in /usr

open terminal and sudo nautilus

---

### Post by Vaphell on 2009-12-10
gksu for gui apps, sudo for cli apps.

---

### Post by synapsys on 2009-12-11
> **Chesamo said:**
> Only sometimes. Usually, you want Nautilus/Thunar launched with the user's configuration, not root's, and sudo works fine with both of them.

True, but it's good habit to have. 

> **Chesamo said:**
> EDIT: Amusing how we linked the same page. Go Google!

lolz

---

### Post by DJ . on 2009-12-11
> **joes7 said:**
> You don't have enough permissions. Log in as the "root" user, it should let you move it.
how do you do that?

---

### Post by Leppie on 2009-12-11
> **Chesamo said:**
> Ubuntu disables root by default. (Also it's against forum rules to tell people how to enable root.)

What is so wrong about having the root account enabled?

---

### Post by DJ . on 2009-12-12
I figured it out how to move the files thanks everybody

---

### Post by louieb on 2009-12-12
> **Leppie said:**
> What is so wrong about having the root account enabled?
Nothing wrong with enabling the root account. Lots of distros enable the root account by default.  Do it if you want. But 1st you have to learn to Google.

 :D I don't need it - I can screwup my system without it. - A disabled root account just makes it harder for someone to hack into your system and screw it up for you. 

[forum policy on log-in-as-root tutorials - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=716201")

---

### Post by Cheesemill on 2009-12-12
> **Chesamo said:**
> Or you could just simply sudo thunar. I've never found a need for gksudo, since sudo works just fine 99% of the time.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo) (I disagree with the opinion, but information regarding the differences is there)

You've obviously never screwed up your home folder by running:
```
sudo firefox
```
then. (Don't run this command).

There are several graphical apps which will change permissions in your home folder if you use sudo instead of gksudo. Also you say 99% of the time. Why risk that when gksudo works 100% of the time?

To reiterate, use sudo for CLI apps and gksudo for GUI apps. :)

---

### Post by Leppie on 2009-12-12
> **louieb said:**
> :D I don't need it - I can screwup my system without it.
If you check this forum, you will find that not even in a long shot you would be the only one with this ability. Is it not better to teach new users how to use the root account properly?

> **louieb said:**
> A disabled root account just makes it harder for someone to hack into your system and screw it up for you.
This may be true, but how much longer would it really take?

---

### Post by Leppie on 2009-12-12
> **Cheesemill said:**
> To reiterate, use sudo for CLI apps and gksudo for GUI apps. :)
Is gksudo installed by default in Ubuntu? It's not in Xubuntu...

---

### Post by SuperSonic4 on 2009-12-12
It might be gksu

What I don't understand is the aversion to the command line. ```
sudo cp src dest
``` is much easier than all this waffle

---

### Post by Leppie on 2009-12-12
> **SuperSonic4 said:**
> It might be gksu
gksudo is like the command line sudo, gksu is like cli su.


> **SuperSonic4 said:**
> What I don't understand is the aversion to the command line.
I don't believe there's an aversion to the cli in this case, gksu and gksudo actually allow you to launch graphical applications from a terminal.

---

### Post by louieb on 2009-12-12
> **Leppie said:**
> . Is it not better to teach new users how to use the root account properly?

:D  What root account? in Ubuntu its disabled. I've enabled the root account in the past. No longer do it. Too big a pain in the butt to use it   Just my two cents.  :mrgreen:  sudo is the better and easier way to perform administrative tasks.

---

