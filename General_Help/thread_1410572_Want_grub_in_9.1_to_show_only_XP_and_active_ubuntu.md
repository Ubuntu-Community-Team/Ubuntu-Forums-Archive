---
title: "Want grub in 9.1 to show only XP and active ubuntu"
date: 2010-02-18
forum: General Help
---

### Post by DnDer on 2010-02-18
I'm installing this for someone else who will never use or need to use any other option than "boot windows" or "boot ubuntu." Having anything else in grub will just confuse them.

I can't figure out how to configure the new grub2 file properly in /etc/default/grub, which is what replaced the old list file - that's what google tells me, anyway.

What do I need to do to make only 2 OSs show up on this?

---

### Post by Girya on 2010-02-18
> **DnDer said:**
> I'm installing this for someone else who will never use or need to use any other option than "boot windows" or "boot ubuntu." Having anything else in grub will just confuse them.

I can't figure out how to configure the new grub2 file properly in /etc/default/grub, which is what replaced the old list file - that's what google tells me, anyway.

What do I need to do to make only 2 OSs show up on this?

check out removing entries caveat: haven't tried this myself yet but i'm going to try as soon as I post;)

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by DnDer on 2010-02-18
Read it, didn't understand it. :( Also read the readme in /etc/geub.d/ and it didn't make a lot of sense, either.

First time I've ever attempted something like this, so I know nothing about what I'm doing.

---

### Post by DnDer on 2010-02-18
Down to 4 entries...

generic 2.6.31-19, generic recovery 2.6.31-19, xp home, nt/2000/xp (which was never on the netbook to my knowledge... maybe that's the recovery console...)

If I could just stack them in generic 2.6.31-19, xp home as my first two choices, then I'd be golden.

---

### Post by Girya on 2010-02-18
ok, this is what i did:

**warning this will break your system if you make a mistake so be very sure you know what you are doing and you are willing to live with the consequences if you do make a mistake**

1) open up a terminal and type:

```
uname -r
``` 

this is the kernel you want to keep: on my machine its 2.6.31-19-generic it may be different on your machine.

so in synaptic package manager search "linux-headers" and and right click on the headers that **aren't** the output from uname -r. and click on "mark for complete removal"

then search linux-image and do the same thing you just did for the header files (mark for complete removal) then click apply and reboot and you should just have memtest xp and ubuntu in grub. to get rid of memtest 
paste this command into a terminal 

```
sudo chmod -x /etc/grub.d/20_memtest86+
```

this is just a temporary fix because as soon as a new kernel is released you'll have that entry in the grub menu.

---

