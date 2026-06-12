---
title: "Splash image on shutdown"
date: 2011-03-10
forum: General Help
---

### Post by LinuxHUP on 2011-03-10
I am wanting to throw a splash image on shutdown. How do I do it ?
I am using CentOS 5

---

### Post by lithopsian on 2011-03-10
I could tell you how to do it in Ubuntu :)

---

### Post by LinuxHUP on 2011-03-10
that would help. but not any third party tools.
directfb would be good. I am not sure the exact sequence of the shutdown process to put my script call.

---

### Post by WorMzy on 2011-03-10
Ubuntu uses Plymouth. Personally, I'd recommend you avoid it like the plague.

Have a look at splashy (which uses directfb). You may need to compile your own kernel if Cent's doesn't have a bootsplash patch applied. Never done it myself though (I use Arch), so I can't help you there.

---

### Post by LinuxHUP on 2011-03-10
I am not much aware of the logic or sequence of steps that happen when you do a shutdown.
I have a script/program that renders the bootsplash image during boot.
It is called in the init script.

Also is it possible to get away with the messages dumped on the screen
when you do shutdown.
like 
```

....
Sending all processes TERM Signal [OK]
....
Umounting filesystems [OK]
Halting...

```

---

### Post by WorMzy on 2011-03-10
Try adding "quiet" to your kernel parameters in whichever boot loader you use.

---

### Post by mmsmc on 2011-03-10
how do you add a splash image on ubuntu?

---

### Post by LinuxHUP on 2011-03-10
would adding the directfb executable I have to the S01Halt script work ?
It doesn't seem to.

---

### Post by LinuxHUP on 2011-03-10
> **WorMzy said:**
> Try adding "quiet" to your kernel parameters in whichever boot loader you use.

tried that. doesnt work.

---

