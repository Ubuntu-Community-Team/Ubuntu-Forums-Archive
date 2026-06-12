---
title: "best free diagnostic, recovery, and repair software?"
date: 2011-04-28
forum: General Help
---

### Post by RememberWhenItRained on 2011-04-28
I have several CDs of diagnostic and recovery software (most of which are dated) but never seem to have them around when i could use them the most. Then it hit me: use a flash drive. i usually carry two flash drives around with me, so i loaded one 4GB with diagnostic/repair tools from PortableApps.
So far I have CCleaner, John the Ripper, Recuva, an antivirus, and SIW (System Info. for Windows). I still have plenty of space left and was wondering what you all's favorites were, or what i might add. I'm looking to have somewhat of a suite, something for any occasion (within reason, of course.)

I think everything right now i have is PC-based. i just want a suite of tools in case anyone has a non-hardware issue (i seem to be the go-to computer guy for some people(and im still a beginner)) that i can keep handy on my flash drive. any suggestions?

---

### Post by dragonfly41 on 2011-04-28
For windows .. [www.sysinternals.com](www.sysinternals.com)

further suggestions .. Parted Magic (suite of utilities) and Super Grub2

---

### Post by RememberWhenItRained on 2011-04-28
> **dragonfly41 said:**
> For windows .. [www.sysinternals.com]("http://www.sysinternals.com")

further suggestions .. Parted Magic (suite of utilities) and Super Grub2
hmm, sysinternals looks like it might have a bit of a learning curve. As far as Parted Magic, can i put that on the same flash drive as the rest of my utils even thought it boots from the drive? In other words, if i have PM on my flash drive, will it still show the rest of the contents on the drive when booted in PM?

---

### Post by dragonfly41 on 2011-04-29
Try unetbootin to create your custom USB with mix of utilities ..

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

this thread discusses integrating Parted Magic with ubcd ..

[http://www.ultimatebootcd.com/forums/viewtopic.php?t=1350](http://www.ultimatebootcd.com/forums/viewtopic.php?t=1350)

---

### Post by RememberWhenItRained on 2011-04-30
> **dragonfly41 said:**
> Try unetbootin to create your custom USB with mix of utilities ..

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

this thread discusses integrating Parted Magic with ubcd ..

[http://www.ultimatebootcd.com/forums/viewtopic.php?t=1350](http://www.ultimatebootcd.com/forums/viewtopic.php?t=1350)
will the unetbootin installer erase my existing programs?

---

### Post by dragonfly41 on 2011-04-30
Installing unetbootin ...  [COLOR=Blue]sudo apt-get install unetbootin
[/COLOR]
Then launch from Applications > System Tools > Unetbootin

Read the manual .. note the warning about ticking the box "show all drives" since you might easily overwrite the wrong partition.

Usually unetbootin is used to create a bootable USB formatted from scratch .. so 

Copy your library of utilities into some temporary / backup folder

use unetbootin to create the bootable USB

copy over other utilities as you find them.

Remember that you can also format and multi-partition your USB with GParted.

So optionally you can create an extended partition with multiple logical partitions.   e.g. one dedicated to Parted Magic.

You could then switch between different partitions on your bootable USB.

---

### Post by winh8r on 2011-04-30
Hi,

One of the best tools I have found is PhotoRec which you can read about [http://www.cgsecurity.org/wiki/PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") . It does a very thorough job of recovery of a variety of file types which can be specified by the user.

---

### Post by Smokin Whale on 2011-04-30
Ultimate boot cd can be used on a USB.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by ronnielsen1 on 2011-04-30
No one has mentioned Hirens boot cd. It has tons of utilities

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

---

### Post by RememberWhenItRained on 2011-04-30
> **ronnielsen1 said:**
> No one has mentioned Hirens boot cd. It has tons of utilities

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)
good call; i am hoping to have as much utils on this 4GB drive to be able to solve most problems that arise, without being too redundant as to what the software can do. (unless it works differently, i'm trying to avoid having two different programs that do the same thing so i can save space.)

---

### Post by Blasphemist on 2011-04-30
Here is more to look into.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

[http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/#more-3157](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/#more-3157)

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by RememberWhenItRained on 2011-04-30
> **Blasphemist said:**
> Here is more to look into.

[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

[http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/#more-3157](http://www.pendrivelinux.com/casper-rw-creator-make-a-persistent-file-from-windows/#more-3157)

[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Main_Page)

[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

this is why i love this community: so helpful!

and Pikes Peak? I'm jealous.

---

### Post by Blasphemist on 2011-04-30
And, it's got a pretty fresh snow cover and more coming tonight and this weekend!

---

### Post by RememberWhenItRained on 2011-04-30
> **Blasphemist said:**
> And, it's got a pretty fresh snow cover and more coming tonight and this weekend!
this warrants a picture. anyway, enough derailing from me.

---

### Post by RememberWhenItRained on 2011-04-30
> **ronnielsen1 said:**
> No one has mentioned Hirens boot cd. It has tons of utilities

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)
the ZIP folder should be able to just be extracted straight to the drive without affecting functionality, right?

---

