---
title: "A VNC that works while logged out?"
date: 2010-09-15
forum: General Help
---

### Post by KolakCC on 2010-09-15
Hi, I've been using ubuntu for about 2 weeks now. I want to access my computer at home from work using the VNC protocol or the windows RDP protocol. 
There's just one problem though, I can't access it when my computer is on the "lock screen".
Which VNC server do you recommend for doing this?

---

### Post by spiky001 on 2010-09-15
if the screen is locked yo will always have problems, if you set a password to unlock screen it should work, thats how mine it done

---

### Post by KolakCC on 2010-09-15
So the best solution is just leave my computer on without automatic locking?

---

### Post by CharlesA on 2010-09-15
> **KolakCC said:**
> So the best solution is just leave my computer on without automatic locking?

No.

I would suggest looking into something like [FreeNX]("http://www.nomachine.com/select-package.php?os=linux&id=1").

---

### Post by spiky001 on 2010-09-15
mine logs in auto then screensaver is passworded if your just using vnc to acesses pc then that will be your only protection from other ppl as well, better off using port forwarding with ssh not leaving port 5900 open

---

### Post by Grenage on 2010-09-15
Doesn't RDP unlock the machine when you enter the username/password?  It does here...

FreeNX is excellent, but I've only used it on Linux machines.

---

### Post by spiky001 on 2010-09-15
do you need to use vnc, can you not move files with command line for that you can just use ssh

---

### Post by CharlesA on 2010-09-15
As already stated, it's not that smart to have VNC open to the internet. FreeNX uses SSH as the transport and works better then VNC.

You don't have to worry about being logged in.

---

### Post by KolakCC on 2010-09-15
I thought you had the option to put a password to connect?
I'll try FreeNX. Thanks!

---

### Post by CharlesA on 2010-09-15
> **KolakCC said:**
> I thought you had the option to put a password to connect?
I'll try FreeNX. Thanks!

If you use a strong password, it's not that bad, but vnc isn't encrypted like SSH is, so you'll be sending keystrokes and whatnot unencrypted over the internet.

---

