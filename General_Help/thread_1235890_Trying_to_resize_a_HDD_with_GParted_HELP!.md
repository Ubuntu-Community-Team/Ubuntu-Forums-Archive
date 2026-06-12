---
title: "Trying to resize a HDD with GParted HELP!"
date: 2009-08-09
forum: General Help
---

### Post by GRAYgoose12 on 2009-08-09
trying to resize 50 gb off of the first hdd to put onto the XP partition! its greyed out...how do i precede? this is my only hdd that has the xp partition and ubuntu partition on it.
[IMG]http://tinypic.com/view.php?pic=2ymdnxk&s=3[/IMG]
I actually have Jaunty right now 9.04

---

### Post by phillw on 2009-08-09
All re-partioning runs the risk of losing data..

Have a good read of this article, it explains the hows and whys of using gparted.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

After backing up, I did an 'on the fly' resizing of my Vista, ext3 and swap partitions.... Yeah, I was nervous,
but I had a FULL backup ... 

Oh, and to do a good, solid backup ....

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup+restore+Ubuntu)

Is also an excellent article

For adding XP / Vista to Linux, or vice-versa

[http://apcmag.com/howto_search.htm?q=Keyword&catid=198](http://apcmag.com/howto_search.htm?q=Keyword&catid=198)

Will explain it all.

Regards,

Phill.

---

### Post by GRAYgoose12 on 2009-08-09
I didn't ask about the risks i know them, don't want to add vista or xp...just want to resize...

---

### Post by merlinus on 2009-08-09
Are you running gparted from the live cd?  If you are wanting to shrink your linux partition, this is the only way to do it, as it has to be unmounted first, as well as turning swapoff.

You also might post a screenshot.

---

### Post by phillw on 2009-08-09
> **GRAYgoose12 said:**
> trying to resize 50 gb off of the first hdd to put onto the XP partition! its greyed out...how do i precede? this is my only hdd that has the xp partition and ubuntu partition on it.
[IMG]http://tinypic.com/view.php?pic=2ymdnxk&s=3[/IMG]
I actually have Jaunty right now 9.04

Okay - boot with a GParted live disk & slice away.

Just bear in mind, if you mess up - bye, bye data.

Linux will do as it is told, by you.

If you read the 1st article, it will show you what to expect. As your hard-drive will then it at your mercy, please do have a think before you press the button to commit your changes !!

BTW, when i resized my partitions, windows was not a happy bunny (BSOD), I believe this is a common occurance, after a re-boot, it worked out its new file size & was happy.

It should all go well, my re-slicing did, just be careful !!!

Regards,

Phill.

---

