---
title: "after update grub can't find the kernal - help!!!"
date: 2010-02-05
forum: General Help
---

### Post by zachthejones on 2010-02-05
Okay, here's the setup, I had Windoze 7 on my wife's laptop, it started running crappy so I install Ubuntu 9.10 via Wubi (so it is not a partitioned dual-boot). I did the latest update, which I think included a kernel update. When I rebooted and chose Ubuntu from the windows dual boot window, instead of loading the GRUB I see an error message flash:
```
TRY hd0: NTFS no Wubi(something-or-other)
```
it flashed almost too fast for me to catch - it took about 10 reboots to figure out that much...

and then it goes to a screen that says
```
GNU GRUB version 1.97~beta4

sh:grub
```

I tried several different commands (you can prompt it to give you available commands by hitting TAB), but it said it couldn't detect a kernel.

Also, before I updated, I had tried to install iTunes via [these instructions]("http://www.linuxscrew.com/2008/12/15/use-itunes-in-linux-including-apple-music-store/"). iTunes seemed to have installed fine, but I hadn't tried it yet. I have no idea if that would have compromised something - it shouldn't have, right?

---

### Post by meierfra. on 2010-02-05
You  probably  have been hit a bug in Grub 2. See this link for  more details and the solution:

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by zachthejones on 2010-02-05
That did it! thanks so much! It's so nice to be back in Ubuntu...

---

### Post by meierfra. on 2010-02-05
> That did it
Great.

> thanks so much! 
You are welcome.


> I had Windoze 7 on my wife's laptop, it started running crappy so I install Ubuntu 9.10 via Wubi

That's a dangerous setup.   Since Wubi is on  a file in the Window partition, a Windows crash can damage your Wubi install. I'm currently working on a case where the Wubi file  has completely vanished, after a sudden shutdown caused by the laptop's    battery running out.

So make sure to back up all important data, and  start thinking about a regular Ubuntu install.

---

