---
title: "Grub2 sucks - has anyone got it to do what it's supposed to?"
date: 2010-07-23
forum: General Help
---

### Post by J V on 2010-07-23
Why does grub2 suck so much? Apparently I'm supposed to be able to set it to immediately boot unless it detects a shift being held, and no matter how many of the 20+ config files I shred to pieces it just won't do it...

Is there any way to do this? (All the guides are wrong and all the answers I've gotten just link to the guides)

Is there some super-bug on launchpad? There should be...

---

### Post by ronnielsen1 on 2010-07-23
> **Uninstalling GRUB 2**

  
**Reverting to GRUB Legacy**

 If a user chooses to return to  GRUB legacy (0.97), these steps will remove GRUB 2 and install GRUB. 

What I did but I liked grub better

---

### Post by prodigy_ on 2010-07-23
Yeah, Grub2 is garbage.

Try [this thread](http://ubuntuforums.org/showthread.php?t=1485072). There's also a couple of releated Launchpad bugs: [444495](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/444495) and [428443](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/428443). Maybe you'll find something useful there...

---

### Post by w1z4rd on 2010-07-26
Grub2 sucks balls.

Its terrible for a new user like me. Now I have a ton of kernels in my grub menu (yeah I know I can uninstall them, but I dont really want to), and I cant customize the names or themes.

Really terrible :(

---

### Post by ronnielsen1 on 2010-07-26
> Its terrible for a new user like me. Now I have a ton of kernels in my  grub menu (yeah I know I can uninstall them, but I dont really want to),  and I cant customize the names or themes.

When I reverted back to grub, I found 2 puppy linux installs I haven't seen for a while

---

### Post by Vaphell on 2010-07-26
you can customize stuff with some tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

grub2 at least will never let you hose your config - if you mess up in the editable files it won't build new config in the grub-update phase, while with old menu.lst you could simply save it in broken state and nothing would ever complain... until next boot

---

### Post by philinux on 2010-07-26
> **J V said:**
> Why does grub2 suck so much? Apparently I'm supposed to be able to set it to immediately boot unless it detects a shift being held, and no matter how many of the 20+ config files I shred to pieces it just won't do it...

Is there any way to do this? (All the guides are wrong and all the answers I've gotten just link to the guides)

Is there some super-bug on launchpad? There should be...

I just changed the timeout to zero in the file /etc/default/grub. Then sudo update-grub
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
**[COLOR="Red"]GRUB_TIMEOUT=0[/COLOR]**
```

---

### Post by J V on 2010-07-26
Yeah only when I do that (on single OR multi-os systems) the only way to get grub back is to change it back, shift doesn't work (Which means you have to chroot if you want to get back into a hosed system)

---

### Post by -kg- on 2010-07-26
I read somewhere (launchpad, I think) that will work if you change timeout to 1 instead of 0.

<Edit> I think I might have found the solution to the problem:

[http://ubuntuforums.org/archive/index.php/t-1406559.html]("http://ubuntuforums.org/archive/index.php/t-1406559.html")

---

### Post by J V on 2010-07-26
Nope, tried that too, and unless grub sees the difference between recovery version and normal version (Or memtest) as another OS (Which should be a bug anyway) it's not doing what it should be...

---

### Post by lidex on 2010-07-26
This didn't help:
[http://ubuntuforums.org/showpost.php?p=8826924&postcount=8](http://ubuntuforums.org/showpost.php?p=8826924&postcount=8)

---

### Post by wojox on 2010-07-26
Grub2 rocks. [Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by egalvan on 2010-07-26
> **J V said:**
> Why does grub2 suck so much? Apparently I'm supposed to be able to set it to** immediately boot unless it detects a shift being held, **and no matter how many of the 20+ config files I shred to pieces it just won't do it...

Is there any way to do this? (All the guides are wrong and all the answers I've gotten just link to the guides)

Is there some super-bug on launchpad? There should be...


I installed Lucid, with GRUB2.
When I boot:
GRUB2 automatically boots Lucid if no key is pressed.
GBUB2 pops up the menu if I hold the SHIFT key.

---

### Post by J V on 2010-07-27
Still no joy... is grub just arbitrary?

---

### Post by egalvan on 2010-08-13
Three more Lucid installs...

all on empty drives...

GRUB2 works as advertised.

---

### Post by drs305 on 2010-08-13
J V,

Do you have any other OS's on your machine or have you disabled /etc/grub.d/30_os-prober? The keystatus check is embedded in a conditional in 30_os-prober and if the conditions aren't met the keystatus check may not be performed.

---

