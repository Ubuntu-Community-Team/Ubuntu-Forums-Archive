---
title: "Weird error when booting"
date: 2011-07-02
forum: General Help
---

### Post by Ryupower on 2011-07-02
Hello, a friend of mine installed **wubi** on his **windows 7**. He **installed software(like netbeans)**, **updated** it once, and then rebooted it. It worked fine. Then, for unknown reasons upon **boot**, it gave him a **black screen**, then it printed all the boot scripts until it ended with:
Code:
```

"ext4-fs sda6 re-mounted. opts errors remount-ro commit 600"
```

He can't boot it. It's the second time he had this issue (seems that he got rid of it only by reinstalling wubi completely.)
What's going on? (there seems to be not much reply on the wubi megathread.)
( I added bold for skimming :) )

---

### Post by drs305 on 2011-07-02
Have your friend boot an Ubuntu LiveCD and download/extract/run the boot info script from the following link. The instructions are on the page.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

It looks like there may be errors on sda6 and it's possible it can be corrected by running an fsck check on sda6, with sda6 unmounted. It could be an improper fstab setting or some other configuration problem.

Posting the contents of RESULTS.txt from the boot info script will give us a better idea of the computer's boot files.

---

### Post by Ryupower on 2012-01-23
This is way older now, but I just wanted to follow up: 
I just reinstalled the thing and got it over with. :/

---

