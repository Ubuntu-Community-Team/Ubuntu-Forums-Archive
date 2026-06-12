---
title: "[Karmic] Open and Save very slow in OpenOffice"
date: 2009-11-14
forum: General Help
---

### Post by Earwicker on 2009-11-14
I've tried all the usual performance tweaks but no avail. I'm working with pure text documents of 8-12,000 words (no graphics or weird formatting), so all the .odt files are <100 kB - BUT, they are really slow opening and saving. It takes several seconds to open and save documents that take fractions of a second using Ooo 3.1 in XP. I suspect something is wrong, this should be lightening - any ideas?? Saving these documents should be virtually instantaneous.

I'm using EXT4, Athlon 4800, 32 bit Karmic, 2 GB RAM. Should be like muck off a shovel but it's slow and clunky, I don't know why but XP leaves it for dead with the same software on the same machine.

---

### Post by jnorthr on 2009-11-14
memory swap issues ? i looked here for tips to improve it : [http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu](http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu)
but the biggest improvement was turning off java, just forgot how i did that didn't i ?:???::???:

---

### Post by Earwicker on 2009-11-14
I already tried that, doesn't make any difference. These are small files, I can't imagine what the problem is... 

I've got to say that Karmic is not very good. I normally recommend Ubuntu to anyone who'll listen but this release is just one big bug.

---

### Post by jnorthr on 2009-11-14
i've decided to stick with 9.04 for a while till these issues are sorted. at least my wireless works and it's faster on an old dog like mine ;)

---

### Post by Earwicker on 2009-11-14
> **jnorthr said:**
> i've decided to stick with 9.04 for a while till these issues are sorted
Yeah, looks like it's back to XP for me. Again! Shame though.

---

### Post by Hagar Delest on 2009-11-14
Try the Sun version perhaps: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Shpongle on 2009-11-14
did you try tools in open office and adjust the memory , it makes a huge difference for me!!

---

### Post by Earwicker on 2009-11-14
> **Hagar de l'Est said:**
> Try the Sun version perhaps: [[Ubuntu] Installing OOo on Debian and Co.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68")
Ah, that's most interesting thanks, I'll try that later.

The OOo packaged with Karmic is really clunky and unpleasant, I can't believe they've released it in this state, given that OOo is pretty much the heart of a Linux installation.

Anyway, I'll install the Sun version later and see. All in all though this is pretty poor, everything from the installer to grub to individual packages is buggy as hell and performance is below par at best. What are you playing at, Mr Canonical, I thought you were going to sock it to Micro$oft?!

---

### Post by Earwicker on 2009-11-14
> **DillByrne said:**
> did you try tools in open office and adjust the memory , it makes a huge difference for me!!
Yep, no makes no difference (or at least doesn't solve the problem).

---

### Post by d4y on 2010-06-13
Same problem in Kubuntu Lucid, terribly slow Open and Save dialogs, it takes seconds to go to another folder. I've got Intel Core i5 with 4GB Ram, other apps "fly" so this slowness of OO is just awful. How could one of the most important packages be so unoptimized?

---

### Post by Hagar Delest on 2010-06-13
Have you tried the Sun version?

---

### Post by Jos_Michael on 2010-06-13
For those who like me have found loading a document a slow process using Open Office in Lucid I have come upon something that has mostly resolved the issue for me. Go in to Tools/Office/OOWriter and set the "Set update links when loading" to "never". I'm no learned computer guy, but while seeking the answer to the same question I looked a little further in the options and this seems to have resolved it for me. Now my documents are loading instantly. l think it stops the system from going out and checking the web for updates before loading. Perhaps one of you folks that really know this stuff can tell me if that's the case. All I know  is that it worked for me.

---

### Post by pannerrammer on 2010-06-16
> **Jos_Michael said:**
> For those who like me have found loading a document a slow process using Open Office in Lucid I have come upon something that has mostly resolved the issue for me. Go in to Tools/Office/OOWriter and set the "Set update links when loading" to "never". I'm no learned computer guy, but while seeking the answer to the same question I looked a little further in the options and this seems to have resolved it for me. Now my documents are loading instantly. l think it stops the system from going out and checking the web for updates before loading. Perhaps one of you folks that really know this stuff can tell me if that's the case. All I know  is that it worked for me.
This suggestion sorted one of my Lucid machines (which was taking 30+ seconds top open a simple document). Cheers

Strangely, my other Lucid box doesn't suffer from the problem at all (and I've not changed the settings from their defaults).

Edit: [ False dawn I'm afraid! Seemed to speed up, but next day just as slow. ]

---

