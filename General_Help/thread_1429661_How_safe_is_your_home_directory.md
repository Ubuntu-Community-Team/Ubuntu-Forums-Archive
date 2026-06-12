---
title: "How safe is your /home directory?"
date: 2010-03-14
forum: General Help
---

### Post by pickarooney on 2010-03-14
I loaded a live CD of linux Mint to see if I could reproduce a Jaunty problem in it and realised I couldn't access my music files as they were in my /home folder which is, of course, not publicly viewable. So I used sudo and was able to access, read, write, delete in my home folder. If it hadn't been my own account I would have been able to do the same with anyone else's account or indeed on another computer. 

What should users do to ensure their /home accounts can't be hacked with a live CD and the sudo command?

---

### Post by Slim Moe on 2010-03-14
Put it on a separate, encrypted partition.

---

### Post by denver on 2010-03-14
You can always encrypt it. Karmic offers this option when installing. I for one prefer LUKS, but the default solution works just as well. If more then one person accesses your computer and you don't really trust them, then this would best for you.

As a side note, as long as someone has physical access to your computer, they can always load they're own operating system and get to your files. Of course, you can always break they're legs if you catch them ;) (what..to drastic?).

---

### Post by blueridgedog on 2010-03-14
Your home directory is safe, unless you have lost physical access control over your PC and have your BIOS setup to allow booting from external media.  Failing that, you can encrypt if you are worried.  If I was worried, the first thing I would do is remove the ability to boot from external media and put in a password for modifying the BIOS.

---

### Post by Enigmapond on 2010-03-14
> **denver said:**
>  Of course, you can always break they're legs if you catch them ;) (what..to drastic?).

Well yes, a bit. I would start with just the fingers but if that proved ineffective then yes, the legs would be the obvious next step... :D

---

