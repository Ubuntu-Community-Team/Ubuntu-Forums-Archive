---
title: "How to use a short-cut to run last command on terminal ?"
date: 2012-07-15
forum: General Help
---

### Post by West201 on 2012-07-15
I currently have Ubuntu 10.04 LTS installed. On other Linux Distros I've used such as Fedora and Gentoo, The terminal by default with a short-cut, by pressing the "page up" botton I could re input the last command without having to retype everything again. 

Is there a way to enable this short-cut with Ubuntu 10.04 LTS ?

---

### Post by Pilot6 on 2012-07-15
Up arrow ;)

---

### Post by West201 on 2012-07-15
> **Pilot6 said:**
> Up arrow ;)

Oh man. Thanks a lot

I'm completely embarrassed

---

### Post by mc4man on 2012-07-15
you can also gain some use of page up/down in various ways 
What I do is create a file in home folder named .inputrc
```
gedit .inputrc
```
and place inside
```
"\e[5~": history-search-backward
"\e[6~": history-search-forward
```
Then the page up/down will display & navigate thru previous commands based on what you type in terminal, Ex. - 
su
will retrieve all sudo commands & anything else starting with su

---

### Post by Cheesemill on 2012-07-15
```
!!
```
Will run the last command again.

```
!a
```
Will run the last command that began with a.

```
!123
```
Will run the command numbered 123, you can list the commands and there associated numbers by running 'history'.

---

### Post by Vaphell on 2012-07-15
i'll add (because it was not obvious) that these ! things are very flexible

eg, if you run ```
some_cmd_requiring_root tons and tons of parameters
```
and it says access denied, you can simply repeat it with sudo with
```
sudo !!
```

---

