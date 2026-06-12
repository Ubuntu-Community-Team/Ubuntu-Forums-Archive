---
title: "Why does this lock my system?"
date: 2009-07-22
forum: General Help
---

### Post by scragar on 2009-07-22
[SIZE="6"][COLOR="Red"]DO NOT RUN THIS CODE, I KNOW IT LOCKS MY SYSTEM, I SIMPLY WANT TO KNOW HOW AND WHY IT LOCKS MY SYSTEM.[/COLOR][/SIZE]
```
sudo fuser -k /dev/*
```
From what I have read this would effectively lock all devices to root, in which case why does keyboard input no longer work? And the suspend button doesn't work either.

If anyone can explain any better how this works I would love to hear it.

And again:
[SIZE="6"][COLOR="Red"]DO NOT RUN THIS CODE, IT WILL LOCK YOUR SYSTEM.[/COLOR][/SIZE]

---

### Post by bacil on 2009-07-22
actually what it does is to kill all process that are accessing any of your devices

this is bit from man fuser
```

       -k     Kill processes accessing the file. Unless changed with -signal, SIGKILL is sent. An fuser process never kills itself, but may
              kill other fuser processes. The effective user ID of the process executing fuser is set to its real user ID before attempting
              to kill.

```

---

### Post by jerome1232 on 2009-07-22
probably because the keyboard is /dev/stdin I believe, /dev is where device files are stored, every device on your system will have a reference to it here.

---

### Post by wojox on 2009-07-22
Yes and you referenced everything with the wildcard /*

---

### Post by scragar on 2009-07-22
bacil I knew -k would kill the tasks currently using the devices, I wasn't expecting input to be refused afterwards.

jerome1232 I know there's a reference to the keyboard in /dev but that still doesn't help me work out why it stopped accepting input, surely if root established exclused access to the device Xorg, which is run as root, would continue to be able to access the keyboard, or am I missing something?

wojox Yeah, I know what wildcards do, I use them myself pretty much any time I use a terminal and want to save some typing( `e-*/I*Cave*1` is a lot easier than `e-[tab]I[tab]Az[tab]Cave[tab]1` and when I want to modify the line for another ebook it's even easier).

---

