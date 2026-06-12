---
title: "Ubuntu won't boot - wubi"
date: 2010-05-12
forum: General Help
---

### Post by ebola1717 on 2010-05-12
I installed ubuntu via wubi about 2 months ago, at 9.10 or whatever was the current release.  Then I upgraded to the current build (10.04?).  It was running fine until a few days ago, when it stopped booting.  I got it to boot once since then, and it ran fine as far as I could tell, but usually it doesn't boot.  

When I select Ubuntu, it shows the little flashing text cursor, and quickly shuts off and restarts.  There's some error message that flashes before it shuts down, something along the lines of "error: command not found" or"file not found", but it's too quick to read.  I don't get prompted with grub or anything.

My upgrade didn't go perfectly smoothly, and which might have something to do with it.  While it was "preparing for memtest86+", it got stuck, and I interrupted it to let it continue installing.  It looked like it was fine, other than some peculiarities when it was booting and shutting down (a lot of text was briefly displayed, and it seemed to load a bit slower).

Any help you can provide would be appreciated.

---

### Post by steveneddy on 2010-05-12
From a link in my sig:

> Because the installation requires an intact functioning Windows system, it is recommended to **install Ubuntu in this manner for short-term evaluation purposes only**. **[COLOR="Red"]A permanent Ubuntu installation should be installed in its own partition[/COLOR]**, with its own filesystem, **[COLOR="red"]and should _not_ rely on Windows[/COLOR]**.

---

### Post by ebola1717 on 2010-05-12
hmm... i guess I should have read everything through more carefully.
I guess my next step should be to create a partition for ubuntu and install it there.  Is there anything in particular that I need to do to uninstall wubi, and is there an easy way to migrate my data, programs, and settings  from my current set up to the new partition?

---

### Post by steveneddy on 2010-05-13
I would back up /home from the Wubi install and do a clean install on a new partition.

You will probably still have to reinstall the applications after installation though.

---

