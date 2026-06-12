---
title: "Frozen, no key combinations work"
date: 2011-02-27
forum: General Help
---

### Post by syntr on 2011-02-27
hi
I use Ubuntu through Wubi, and none of the key combinations in the Wubi Guide ever do anything...I don't have a SYSRQ key on my laptop so I can't even do most of them :(

how do I safely reboot Ubuntu when it freezes (which is often)? Trying to be proactive...

---

### Post by Habeouscorpus on 2011-02-27
If you have a Prnt Srcn key, that's your SysReQ. Mine doesn't either, but my Print Screen is still mapped to SysReq and Prnt Srcn. 

Sometimes you just have to poke it in the eye, and reboot.

EDIT: Actually, what constitutes "freeze"? What are you doing when this happens? What is your computer like (system specs)?

---

### Post by syntr on 2011-02-27
> **Habeouscorpus said:**
> If you have a Prnt Srcn key, that's your SysReQ. Mine doesn't either, but my Print Screen is still mapped to SysReq and Prnt Srcn. 

Sometimes you just have to poke it in the eye, and reboot.

I figured this was it because that's what it usually is, but it didn't do anything either...I substituted prnt scrn for sysreq and no reboot. I don't want to lose my ubuntu install on my netbook :(

---

### Post by Habeouscorpus on 2011-02-27
When it locks up, try hitting Ctrl+alt+F1. If you get a command prompt, login with your info, and type ```
 sudo shutdown now 
``` Which is a very graceful shutdown.

---

### Post by syntr on 2011-02-27
> **Habeouscorpus said:**
> When it locks up, try hitting Ctrl+alt+F1. If you get a command prompt, login with your info, and type ```
 sudo shutdown now 
``` Which is a very graceful shutdown.

Yeah, tried this lol. No terminals would come up.

I think what I'm really asking is how to make SYSRQ map to PrntScrn on my keyboard.

---

### Post by Habeouscorpus on 2011-02-27
Yikes, why is it panicing so much? 


Here's a link: [http://ubuntuforums.org/archive/index.php/t-354969.html](http://ubuntuforums.org/archive/index.php/t-354969.html)

It shows how to remap keys.

---

### Post by syntr on 2011-02-27
> **Habeouscorpus said:**
> Yikes, why is it panicing so much? 


Here's a link: [http://ubuntuforums.org/archive/index.php/t-354969.html](http://ubuntuforums.org/archive/index.php/t-354969.html)

It shows how to remap keys.

No clue
right before I was in Openoffice typing a report (I disabled Wifi to do so to avoid procrastinating) but I needed to look something up so I turned it back on, opened Chromium and started to type in the search bar and everything froze...I think it had something to do with re-enabling Wifi...really odd.

---

### Post by Habeouscorpus on 2011-02-27
Did you do anything out of the ordinary to get the wifi working? i.e, drivers, mods, magic...

---

### Post by syntr on 2011-02-27
> **Habeouscorpus said:**
> Did you do anything out of the ordinary to get the wifi working? i.e, drivers, mods, magic...

No, it worked OOTB
The only thing I can think of is that I used the hardware WiFi key to disable it. Next time I'll try 'disconnect' (after using xmodmap, of course...)

---

### Post by Habeouscorpus on 2011-02-27
Haha, yeah, make sure you can recover!

Also, you may want to boot to a live disk and do a fsck. (file system check)Just to make sure everything's kosher.

---

