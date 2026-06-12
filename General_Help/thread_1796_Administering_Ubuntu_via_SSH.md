---
title: "Administering Ubuntu via SSH"
date: 2004-10-23
forum: General Help
---

### Post by ions on 2004-10-23
I put Ubuntu on my neighbours machine and wish to keep it up to date via SSH.

I've been using the commands:

```

sudo apt-get update
sudo apt-get dist-upgrade

```

Anything else I need to be aware of?

ps: I'm really enjoying Ubuntu!  1st of many posts I hope!

---

### Post by FLeiXiuS on 2004-10-23
I would be aware of new kernels / warty versions.

sudo apt-get upgrade

That'll upgrade all of the packages for you.  Have fun!  Just keep in mind that security plays a big part of administering over ssh.  Keep things locked down!

---

### Post by ions on 2004-10-23
So  I should use upgrade instead of or in addition to what I already have?

---

### Post by FLeiXiuS on 2004-10-23
[QUOTE=ions]So  I should use upgrade instead of or in addition to what I already have?[/QUOTE]
In addition with what ur already doing.

---

### Post by ions on 2004-10-23
Thank you! :)

---

### Post by ions on 2004-10-26
[QUOTE=FLeiXiuS]In addition with what ur already doing.[/QUOTE]
 Running this set of 3 has caused the machine to lose network connections.  No net.  No ssh.  Yet to get in front of the box and check it out.

---

### Post by ions on 2004-10-26
If I try and ping an IP I get this:  connect: network is unreachable

---

