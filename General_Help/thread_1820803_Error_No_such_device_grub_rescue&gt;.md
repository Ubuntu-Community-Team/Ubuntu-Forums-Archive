---
title: "Error: No such device grub rescue&gt;"
date: 2011-08-08
forum: General Help
---

### Post by Silverwolfxp on 2011-08-08
HI. I have a problem. every time i boot my laptop i get
error: no such device. [insert numbers]
grub rescue> 

I've tried many things to fix it and nothing has worked. I have a liveCD but it won't read it. and the only command i can do is 
grub rescue> ls
(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) (hd1) (hd1,1)

i cant do anything else i always get "unknown filesystem" or "unknown command"
I really don't know what to do anymore. I need to get back into Windows 7 because I have all my files on that...and if i do what my friend told me to do (wipe the hard drive) i'd lose EVERYTHING and I really dont want to go back and re download 3100 songs and rewrite all my music. So if you can help it'd be much appreciated.

Arigatou
~Silver

---

### Post by oldfred on 2011-08-08
Welcome to the forums.

You should be able to boot from grub rescue.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

But you need to be able to boot a CD to make repairs. Have you set BIOS to boot CD first and/or used one time boot key to select CD to boot first. Some systems seem to need both. 

Is CD still good? If damaged it may not boot.

Does CD drive need cleaning?

---

### Post by psusi on 2011-08-08
Can you describe your partition layout?  You appear to have two disks with several partitions.  You might try using ls in the grub rescue prompt on each of those listed partitions and see if one if them contains a /boot directory:

ls (hd0,1)/

Also enter the set command and see what the value of the prefix variable is.

---

### Post by pritam_par on 2011-08-10
This issue is solved here

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by psusi on 2011-08-10
> **pritam_par said:**
> This issue is solved here

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Please don't say the issue is solved when you aren't the OP.

---

