---
title: "Ubuntu 12.04 fails to boot after kernel update"
date: 2012-06-15
forum: General Help
---

### Post by Shamino on 2012-06-15
I updated to linux-image-3.2.0-25-generic (via the update manager) and now my Ubuntu would not start - when I choose that kernel in Grub, the screen would just go off and I cannot tell if it has boot or not (I think it does not - the boot sound does not play)

However, the previous kernel image, 3.2.0-24 works perfectly.

Has anyone else encountered this problem?

I am running this Ubuntu 12.04 on an Acer Aspire 5755G.

---

### Post by drs305 on 2012-06-15
Haven't experienced it, but try editing your Grub menuentry by pressing "e". 
1. Cursor to the end of the linux line and backspace to remove everything from "quiet" to the end. 
2. Add *nomodeset*
3. Press F10 or ctrl-x to boot.

If it boots, you probably need to reinstall your video driver.

---

### Post by Yce on 2012-06-15
This happend to me too, but with a headless server. The boot menu shows up and black screen then nothing, but if I hit the first menu item (kernel 3.2.0-25-generic) it loads, and then kernel panic (if I disable eth interfaces in bios), or it can't get any ip from router, looks like IP-Config freezes, or goes in an infinte loop. Tried your solution but no luck.

Please help!

update: with only one eth interface, it gets ip and then tries to get some nfs mount (?! I have none...)

---

### Post by drs305 on 2012-06-15
> **Yce said:**
> This happend to me too, but with a headless server. The boot menu shows up and black screen then nothing, but if I hit the first menu item (kernel 3.2.0-25-generic) it loads, and then kernel panic (if I disable eth interfaces in bios), or it can't get any ip from router, looks like IP-Config freezes, or goes in an infinte loop. Tried your solution but no luck.

Please help!

update: with only one eth interface, it gets ip and then tries to get some nfs mount (?! I have none...)

Sorry my suggestion didn't help. It prevents modules from being loaded but mostly helps when a video driver is causing the problems. The *nomodeset* switch prevents a problem video driver from being loaded until a working one can be installed.

---

### Post by Yce on 2012-06-15
Hm, it looks like ubuntu wants to boot from an nfs share.

prints out this: [http://i46.tinypic.com/u3jnc.jpg]("http://i46.tinypic.com/u3jnc.jpg")

---

### Post by Shamino on 2012-06-18
> **drs305 said:**
> Haven't experienced it, but try editing your Grub menuentry by pressing "e". 
1. Cursor to the end of the linux line and backspace to remove everything from "quiet" to the end. 
2. Add *nomodeset*
3. Press F10 or ctrl-x to boot.

If it boots, you probably need to reinstall your video driver.

That did not work. However, it did randomly boot once, but then the audio was not working.

So I am guessing I should report this problem somewhere...

---

### Post by Bushflyr on 2012-06-18
FWIW, I've been having the same problem. vmlinuz-3.2.0-25-generic fails to boot on a headless server. When I select -24 from the grub menu it works perfectly. 

I've tried to roll back and reupdate from -24 but it still hangs. 

There doesn't seem to be anything in dmesg (it's from the next "good" boot) and dmesg.0 is empty. So for some reason it's not saving the messages from the bad boot.

The last message displayed on the hung boots is 

```
system_call_fastpath+0x16/0x1b
```

and it's always the same, so there is definitely some sort of bug or hardware conflict in there.

---

