---
title: "Command Line Pipes and Opening Files"
date: 2010-07-12
forum: General Help
---

### Post by hailholyghost on 2010-07-12
Hi all,

I've been using Ubuntu for about 4 years now and have usually managed to avoid the command line.  I've been spoiled by the GUI!

One of the first issues I've had with the CLI is that I have to remember how to open a file by the program to open it with.  If it's a flash video, its not much of an issue (just % vlc video.flv) but what if I don't know or remember how to open it?

I tried "% open file" and "% openvt file" but that didn't work at all haha.

:popcorn:I'm a grad student in chemistry and am using AMBER m.d. which requires extensive use of the CLI, so I'm trying to become more fluent.
I've tried to learn pipes, and tried a very basic

% pwd | nautilus

to try to open a file browser in the current directory.  The command "nautilus" unfortunately doesn't have a manual page!  But it is usually worked

% nautilus /your/directory/here

so I figured piping the output from "pwd" to "nautilus" would open a file browser of the directory I was currently in.  Alas it just opened the home directory!  I figured there was something basic I was missing so I asked the resident Ubuntu Guru and he was just as mystified.

Would anyone be able offer any pointers?

Thanks so much!:P
-Dave

---

### Post by RiceMonster on 2010-07-12
try this:
```
nautilus `pwd`
```

If you use back ticks, it will use the output of the command within the back ticks. Not all programs will accept data through pipes.

---

### Post by Telengard C64 on 2010-07-12
> **hailholyghost said:**
> 
% pwd | nautilus


That just redirects standard output of the *pwd* command to standard input of *nautilus*. AFAIK Nautilus does not use standard input, but accepts command line arguments. You may obtain the result I think you are seeking with something like this:

```
nautilus "$PWD"
```

or

```
nautilus "$( pwd )"
```

---

### Post by TheForumTroll on 2010-07-12
```
nautilus .
```

---

### Post by tgalati4 on 2010-07-12
```
ls -la | more
dmesg | more
cd && cat .profile
history | more
```

---

### Post by nmaster on 2010-07-12
> **hailholyghost said:**
> 

I tried "% open file" and "% openvt file" but that didn't work at all haha.



open works in OS X.  in ubuntu use gnome-open.

```
gnome-open file
```

---

