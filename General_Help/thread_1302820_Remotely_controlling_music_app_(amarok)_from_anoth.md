---
title: "Remotely controlling music app (amarok) from another linux box"
date: 2009-10-27
forum: General Help
---

### Post by juicyoner on 2009-10-27
I am pretty sure there is a way to accomplish this, but I don't have enough experience.

Here is the setup - I have a desktop running jaunty ubuntu. It has a huge hard drive of music and its hooked up to my stereo. I also have a netbook that runs remix. 

I am interested in controlling amarok (or any music application) running via my netbook.

One option would be to invoke an x-window session, but I think that would require too much of the CPU. I'd like something more lightweight.

Are there any way to login via a web interface? Or perhaps a program that could do this remotely?


Thanks in advance!

---

### Post by Giblet5 on 2009-10-27
I don't really follow what you have set up, but it sounds like you can use ssh to start amarok on system A with its interface displayed on system B.

From system B, terminal window:
```
ssh -zX systemA amarok
```

The music will play over on System A...

Great way to drive grandma insane...

---

### Post by Maheriano on 2009-10-27
I use NXClient. It lets me start a session on my laptop and control my desktop as if I were sitting at it. I think you mentioned this as too CPU intensive but it's not so bad.

But if anyone knows command line arguments to control Audacious then you could just SSH from your netbook or PDA.

---

