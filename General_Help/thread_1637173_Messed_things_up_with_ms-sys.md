---
title: "Messed things up with ms-sys"
date: 2010-12-04
forum: General Help
---

### Post by computerwiz on 2010-12-04
okay so i was trying to get rid of the grub mbr with ms-sys. first i put in ms-sys -m /dev/sda1 as this [tutorial ]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")told be so but it ms-sys told me i had to used the force command(-f), which i used but when i restarted the grub mbr was still there so then i realized i shouldn't have put a mbr on the partition. so i boot back into mint linux (cd) and noticed that the windows partition is no longer in the computer available and i can't manually go to it or mount it. so in a panic i try write the mbr on the actual hard disk with ms-sys --mbr /dev/sda which got rid of the grub mbr only to give me a "invalid Partition Table" error. Did i destroy the windows partition? is it savable at all?

---

### Post by computerwiz on 2010-12-04
bump

---

### Post by dandnsmith on 2010-12-05
I hesitated ove trying to reply to this post.
I know just enough to realise that I may only be able to offer comment.
One of the problems is the lack of relevant information about your installation - especially about the Windows setup. If you have a 'recent' PC which has Windows7, then the partition organisation can be different from those which I am used to, as Msoft changed the HDD organisation (in regard to position of partition boundaries and block sizes) to cater for a new style of booting (rather like Macs use) which can be used with more recent motherboards.

There are tools which say they can recover partitions and/or files, and they might do the job - but you'd be better off asking where the expertise in this field is. With an install CD for your Windows, I think you have the relevant tools to rewrite the boot code, and, possibly, the partition information.

In your shoes, I'd google to find the tools, and then read the pages carefully to see whether there are any references to how up-to-date they are, and plaudits from users.

---

### Post by karthick87 on 2010-12-05
Post your results of [[COLOR=DarkOrange]**Bootscript**[/COLOR]]("http://bootinfoscript.sourceforge.net/").

---

### Post by edgecombe_r on 2010-12-05
Hi,
I'm running Ubuntu 10.04 and Mythnet 0.24 - basically trouble free. I've just installed mythnetvision and mythnetvision-gui, which also appear to work OK - I can download stuff from TEDTalks and it appears in my Recordings. However, when I view it, it is wildly out of synch (vision:audio) which is OK - I can live with that - but it stops (displays "Paused") after about 10 seconds. Hitting P (via IR remote) gets it going - for about another 10 seconds or so - then pauses again. Sometimes it stops with "Play" displayed, and a P gets it going again.

Extensive googling hasn't uncovered any indication that anyone else is suffering from this.

So - any advice would be much appreciated. So far I haven't done any serious chasing for a cause/mechanism - not even sure where to start really.

cheers
rde

---

### Post by dandnsmith on 2010-12-06
> **edgecombe_r said:**
> Hi,
I'm running Ubuntu 10.04 and Mythnet 0.24 - basically trouble free. I've just installed mythnetvision and mythnetvision-gui, which also appear to work OK - I can download stuff from TEDTalks and it appears in my Recordings. However, when I view it, it is wildly out of synch (vision:audio) which is OK - I can live with that - but it stops (displays "Paused") after about 10 seconds. Hitting P (via IR remote) gets it going - for about another 10 seconds or so - then pauses again. Sometimes it stops with "Play" displayed, and a P gets it going again.

Extensive googling hasn't uncovered any indication that anyone else is suffering from this.

So - any advice would be much appreciated. So far I haven't done any serious chasing for a cause/mechanism - not even sure where to start really.

cheers
rde

Please **don't** hijack someone elses thread - especially on a totally different topic.
Start one of your own.

---

### Post by edgecombe_r on 2010-12-07
re hijacking. My apologies - it was unintentional. My first post and this was at the end of a frustrating search for "new post" or similar. I'll keep searching.

---

