---
title: "help with command shell"
date: 2011-09-30
forum: General Help
---

### Post by cona on 2011-09-30
hi every body,

how can i get to shell for ubuntu?

Thank u.

---

### Post by 2F4U on 2011-09-30
What about opening the terminal application?

---

### Post by Blasphemist on 2011-09-30
Do you mean the command shell or the gnome shell?

---

### Post by cona on 2011-09-30
how can i get shell with the terminal please?

---

### Post by cona on 2011-09-30
i am using VMW in W7

---

### Post by cona on 2011-09-30
yes, command shell.

---

### Post by Blasphemist on 2011-09-30
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by cona on 2011-09-30
Thank you [Blasphemist]("http://ubuntuforums.org/member.php?u=1165520")

the link that you just sent me is general, so i need some spicific thing:

how to get shell prompt from the terminal, please?

---

### Post by Slim Odds on 2011-09-30
> **cona said:**
> Thank you [Blasphemist]("http://ubuntuforums.org/member.php?u=1165520")

the link that you just sent me is general, so i need some spicific thing:

how to get shell prompt from the terminal, please?

Terminals give shell prompts automatically.... are you talking about a root shell perhaps?

```
sudo su
```

---

### Post by cona on 2011-09-30
....

---

### Post by cona on 2011-09-30
i did try sudo su, but the terminal show me this:

root@root:~#sudo su    or   root@root:~#sudo -s
root@root:~#

means nothing! am i right?

---

### Post by Blasphemist on 2011-09-30
No, it shows you that you now have root privileges. Note the user change after the command.
```
jim@jim-Satellite-L505:~$ sudo su
[sudo] password for jim: 
root@jim-Satellite-L505:/home/jim#
```

---

### Post by Slim Odds on 2011-09-30
> **cona said:**
> i did try sudo su, but the terminal show me this:

root@root:~#sudo su    or   root@root:~#sudo -s
root@root:~#

means nothing! am i right?

You were already in a root shell prompt (note the # instead of $ at the end of the prompt).

---

### Post by cona on 2011-09-30
okay [Slim Odds]("http://ubuntuforums.org/member.php?u=100117")

but, how i can get this path /pentest/web/bing/?

i can just be in this path /pentest/web/.

---

### Post by Slim Odds on 2011-09-30
> **cona said:**
> okay [Slim Odds]("http://ubuntuforums.org/member.php?u=100117")

but, how i can get this path /pentest/web/bing/?

i can just be in this path /pentest/web/.

I do not understand the question....

---

### Post by cona on 2011-09-30
just i need to be in this path /pentest/web/bing/.

i can not find that path, how can i get that path from shell, please?

---

### Post by Blasphemist on 2011-09-30
cd is the change directory command. Example-
```
cd /pentest/web/bing/
```
if the path referenced is from relative to root/

Tell us more of what you are seeing about this and might see that it is relative to /Home for instance.

---

### Post by cona on 2011-09-30
in fact i can get access to this path /pentest/web/, it is just the directory /bing/ that i can not find it with that path or other directories which belong to /pentest/ directory.

i need to get access to the /bing/ directory.

thank you...

---

### Post by Blasphemist on 2011-09-30
from the pentest/web directory you can use the list command to view its contents.
```
ls
```
if you don't see it there with the permissions you've established it must not be there.

---

### Post by cona on 2011-09-30
thank you very much and thank for every one!

---

### Post by mmsmc on 2011-09-30
i missed the last page :/ never mind

---

