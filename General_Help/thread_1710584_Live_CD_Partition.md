---
title: "Live CD Partition?"
date: 2011-03-20
forum: General Help
---

### Post by snoopy-2009 on 2011-03-20
curious if its possible (i dont see why not) to extract the ubuntu livecd iso onto a small partition, with the purpose of booting that partition via an additional grub entry configured to do so?

im thinking of this much like a 'recovery' partition some systems are shipped with. where if somthing went wrong, (as long as its not a misconfiguration in which grub wont load...crap..thats not uncommon.. lol) it could be fixed using that partition instead of reinstalling the iso onto my USB flash drive whenever this happens.

---

### Post by Quackers on 2011-03-20
I don't have a link, unfortunately, but there is a guide around here to make a .iso image of your current installation. Try in Tutorials & Tips section of the forum, perhaps.

---

### Post by Rubi1200 on 2011-03-20
I do believe this is what our friend Quackers is referring to:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by snoopy-2009 on 2011-03-20
hmmm.. what r u suggesting? cloning my ubuntu partition? then just use one for a recovery tool?

---

### Post by mcduck on 2011-03-20
You don't really even need to extract the CD, Grub2 is able to boot directly from .iso images.

So you can create a small partition, install Grub on that partition and drop the disc image there. Same method as when creating a multi-boot USB stick: [http://www.panticz.de/MultiBootUSB]("http://www.panticz.de/MultiBootUSB")

---

### Post by snoopy-2009 on 2012-01-23
> **mcduck said:**
> Grub2 is able to boot directly from .iso images.



wow i still didnt know that -- and i feel im much more advanced now -- haha. thank you for your help. sorry i never said thanks. :)

thanks! :)

---

