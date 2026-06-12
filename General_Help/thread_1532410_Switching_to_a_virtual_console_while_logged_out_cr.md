---
title: "Switching to a virtual console while logged out crashes GNOME"
date: 2010-07-16
forum: General Help
---

### Post by Zorgoth on 2010-07-16
If I am logged out of GNOME and switch to tty1 and back, I get a stream of errors (which I can't copy...) on a black console.  If I am logged in I am fine.  This is very annoying because I would like to be able to log out of GNOME while I am running particularly memory-intensive scripts (they approach the limit of my 3.8 GBs of RAM).

---

### Post by Zorgoth on 2010-07-16
I have some more data on this; 

The blank window gives
```

(process:341): Glib-WARNING **: getpwuid_r(): failed due to unknown user id (0)

```
at the top and under that it looks like some daemons are trying to restart X (a bunch of things with [ OK ] at the end).

I can get a new X session by running sudo killall Xorg, but once I've done that, I can't even switch to a virtual console while logged in without crashing my GNOME.

---

### Post by iponeverything on 2010-07-16
I tried to recreate this on 10.04 and was unable to do it. 

I logged out of the gui, switch to tty1 logged in, switched back to gdm and back to tty1 without issues. 

Can you provide more information on how to recreate the issue?

---

### Post by Zorgoth on 2010-07-16
I am encrypted; I am using the encryption from the alternate CD for everything but /home, which policy forces me to encrypt with Truecrypt.  Another person who reported a similar bug was also encrypted, so maybe that has something to do with it.  I have an ATI radeon hd 2400.

---

### Post by iponeverything on 2010-07-17
I have encrypted lvm from alt disk. 

What version are you running? You are short on useful details. 

As for the job -- just put into the background and hand it off to init.

```

Ctrl-Z
bg
disown %1

```

---

### Post by Zorgoth on 2010-07-17
I'm using 10.04.

And what were you talking about here:

As for the job -- just put into the background and hand it off to init.

```

Ctrl-Z
bg
disown %1

```

---

### Post by digitalcitizenx on 2010-07-17
Simply switching to a tty doesn't necessarily kill the Gnome session.

When you start your tty session, first run this command to stop gdm and free up your memory for your processes:

 ```
sudo killall gdm
```

Then when you are finished simply run:

```
startx
```

I believe that will work to help you with more memory, but doesn't address you original issue - sorry :^)

---

### Post by iponeverything on 2010-07-17
> **Zorgoth said:**
> I'm using 10.04.

And what were you talking about here:

As for the job -- just put into the background and hand it off to init.

```

Ctrl-Z
bg
disown %1

```

When you run a job it owned by you, as you can see from top.  If you look at the job with pstree

```
pstree -up
```

You will see that the job that you started is rooted to your shell (it's child of your shell). When your shell dies, its children are harvested. Though disown, the parent shell "disownes" the child process and it is picked up by init -- the parent of all processes.

---

