---
title: "Downgrade to 9.04?"
date: 2009-12-01
forum: General Help
---

### Post by ndmp on 2009-12-01
No easy way of saying this, but 9.10 is worthless. I get at least one complete system freeze a day which suggests that there are serious kernel issues (and is FAR worse than anything Microsoft has ever put me through). Is it possible to go back to 9.04 without reformatting and reinstalling?

---

### Post by doas777 on 2009-12-01
short answer, no.
contrary to popular belief, there is no GOOD way to go from jaunty to karmic without format/reinstall either.

I recommend using a different home partition so that you don't have to back up during rebuilds.

---

### Post by Jive Turkey on 2009-12-01
I rolled back to Jaunty after less than a day with Karmic, my laptop runs ok with it but Jaunty seems so much more polished and works better on my desktop. I reccomend deleting some of the "." folders in your home partition before reinstalling 9.04.  particularly the ~/.gnome* and ~/.gconf ones as there are some incompatibilities.

I have to say I'm pretty disappointed with 9.10 too.

I should probably mention that deleting those files will render the current installation unusable via gui until you reinstall.

---

### Post by doas777 on 2009-12-01
9.10 is working out as well for me as jaunty or intrepid have. in fact, my problems right now, are with a jaunty samba server and a jaunty client. in totem and a number of other players, smb based video will occasionally just stop, and then 5 minutes later will restart, 5 minutes further into the ep. feh.

my initial boot with karmic was slow but I upgraded my existing ext2 partitions to ext4 and the problem went away.

---

### Post by ndmp on 2009-12-01
Is there any hope of a fix for this any time soon?

---

### Post by doas777 on 2009-12-01
> **ndmp said:**
> Is there any hope of a fix for this any time soon?
depends on the specific issue you are experiencing, and it;s cause. if it is a driver problem, prolly not.

---

### Post by ndmp on 2009-12-03
I'm just going to have to switch to a different distribution then, I am far too busy right now to cope with a broken laptop.

---

