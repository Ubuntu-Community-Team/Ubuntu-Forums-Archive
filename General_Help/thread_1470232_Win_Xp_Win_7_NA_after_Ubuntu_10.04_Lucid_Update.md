---
title: "Win_Xp Win_7 NA after Ubuntu 10.04 Lucid Update"
date: 2010-05-02
forum: General Help
---

### Post by sandman3838 on 2010-05-02
Hello

I just updated my Ubuntu 9.10 to 10 through Update Manager.

So far so good as far as Ubuntu is concerned unfortunately I'm unable to access Win_XP or Win_7 from Grub.  Just a blinking cursor?  :confused:

Before I had some issues and "meierfra" with "drs305" helped out greatly but I'm not sure if they have updated to Ubuntu 10.04 Lucid?

Please take a look at the information in the attachment.  It was from a script file that Meirfra had me run before.

Thank you all.  :P

---

### Post by bcbc on 2010-05-02
You installed grub2 in the bootsectors of your windows partitions. Remember that popup that asked you to select where to install grub? Did you check everything? It looks that way.

So, meierfra has a [fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") that you'll have to apply to each windows partition you need to boot.

Edit: since you have two windows installs, you probably boot one windows from the other (that's the default for windows). At any rate, I don't know your setup, but you might have to take this into account when fixing it. XP is on /dev/sdc1 and windows 7 is on /dev/sdc5

---

### Post by sandman3838 on 2010-05-02
Opps!  Yes I did check everything....
It said that if I was unsure that I should check everything.
Nuts!

How hard is it or is it even possible to revert back to Ubuntu 9.10 Karmic and re-install Ubuntu 10.04?  Should I even consider it?

---

### Post by bcbc on 2010-05-02
You're not the only one caught by that misleading message :(

OK - do **not** reinstall 9.10. The damage has been done and it's done to your windows partitions - so reinstalling ubuntu will not help at all, and just introduces the potential for more issues.

First,  if you haven't already, back up your data. It's still accessible, just not bootable. So boot ubuntu and back up the windows partitions.

Then, you can try meierfra's testdisk option. Otherwise, you could try separate repairs for XP and Win 7. Honestly, I do not know as I haven't had to do this myself, but meierfra's page has helped a number of people fix their broken Windows 7 installs.

---

### Post by wilee-nilee on 2010-05-02
> **sandman3838 said:**
> Opps!  Yes I did check everything....
It said that if I was unsure that I should check everything.
Nuts!

How hard is it or is it even possible to revert back to Ubuntu 9.10 Karmic and re-install Ubuntu 10.04?  Should I even consider it?

You can't revert back, and a reinstall of Lucid I don't think will work due to the distribution of grub into MS. The link given by the other post will probably work if used as suggested. This will get the MS bootlaoder able to boot the 2 MS OS, then you could delete  lucid and reinstall or load grub to the MBR in well I am not sure where actually. You can save the whole thing as it is it just will take a little work, go slowly and ask for help.

---

### Post by bcbc on 2010-05-02
> **wilee-nilee said:**
> then you could delete  lucid and reinstall 
@sandman3838
If you repair with the testdisk option, it will not affect the ability to boot ubuntu and no reinstall is necessary. If you repair your windows boot sectors, you will also have no problem.

If you are following a guide to repair windows that replaces the MBR on your drive (the one that boots first, i.e. /dev/sdd), in that case you will have to reinstall grub2, not lucid. 

The only reason to remove Lucid is if you wish to revert to 9.10, but I can't see any reason for doing this.

---

### Post by wilee-nilee on 2010-05-02
> **bcbc said:**
> @sandman3838
If you repair with the testdisk option, it will not affect the ability to boot ubuntu and no reinstall is necessary. If you repair your windows boot sectors, you will also have no problem.

If you are following a guide to repair windows that replaces the MBR on your drive (the one that boots first, i.e. /dev/sdd), in that case you will have to reinstall grub2, not lucid. 

The only reason to remove Lucid is if you wish to revert to 9.10, but I can't see any reason for doing this.

Thanks for confirming that, I didn't word that correctly. I wasn't sure about whether grub was still active, I have never used testdisc, I just use the bootrec.exe commands. I appreciate the education. ;)

---

### Post by bcbc on 2010-05-02
> **wilee-nilee said:**
> Thanks for confirming that, I didn't word that correctly. I wasn't sure about whether grub was still active, I have never used testdisc, I just use the bootrec.exe commands. I appreciate the education. ;)

Cool. It's not out of the realm of possibility that an install will be needed at some point in the repair, but I've seen cases where this is the first thing tried and it can make the problem worse. The thinking goes - I broke it installing, maybe I can fix it reinstalling - but unfortunately that's not right. So I just wanted to clarify that to the OP, not intended as a criticism at you :)
We're all learning.

---

### Post by sandman3838 on 2010-05-02
Very Cool!
Very Cool!

That link "meierfra has a fix "
Did it!

Everything is up and running.
You guys were great.

Hey what do you think about that new Ubuntu Violet/Purple splash screen when you closing or starting up.  I wish they had left it alone.  Ha!  Anyway I'm complaining too much.    Again thank you both.

---

### Post by bcbc on 2010-05-02
> **sandman3838 said:**
> Very Cool!
Very Cool!

That link "meierfra has a fix "
Did it!

Everything is up and running.
You guys were great.

Hey what do you think about that new Ubuntu Violet/Purple splash screen when you closing or starting up.  I wish they had left it alone.  Ha!  Anyway I'm complaining too much.    Again thank you both.

Sweet!!

Yeah I don't like the purple much either. You can install different themes - I like the solar theme - from synaptic (search on plymouth), but the login screen is still purple. Someone will figure out how to fix it and post it eventually.

---

### Post by wilee-nilee on 2010-05-02
> **bcbc said:**
> Cool. It's not out of the realm of possibility that an install will be needed at some point in the repair, but I've seen cases where this is the first thing tried and it can make the problem worse. The thinking goes - I broke it installing, maybe I can fix it reinstalling - but unfortunately that's not right. So I just wanted to clarify that to the OP, not intended as a criticism at you :)
We're all learning.

Since we have this new release, and lots of new users, the word has gotten around, It seems that the install, or upgrades have some confusing parts like install grub in all partitions and anywhere it will fit (pun). This is causing problems for people with multi OS. Some don't understand partitioning or pre-partitioning for a manual install, so things can get very convoluted when a user tries to fix it before asking for help.

@sandman, none of this refers to you other then it is great that everything is up and running again.

---

### Post by rpaster1 on 2010-05-04
> **bcbc said:**
> You installed grub2 in the bootsectors of your windows partitions. Remember that popup that asked you to select where to install grub? Did you check everything? It looks that way.

So, meierfra has a [fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector") that you'll have to apply to each windows partition you need to boot.

Edit: since you have two windows installs, you probably boot one windows from the other (that's the default for windows). At any rate, I don't know your setup, but you might have to take this into account when fixing it. XP is on /dev/sdc1 and windows 7 is on /dev/sdc5


I had the same problem as sandman and used BCBC's recommended fix, and it is now working fine.

THANK YOU!!!

---

