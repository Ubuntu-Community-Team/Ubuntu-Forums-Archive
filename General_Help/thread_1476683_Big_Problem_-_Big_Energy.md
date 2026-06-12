---
title: "Big Problem - Big Energy"
date: 2010-05-08
forum: General Help
---

### Post by Cardale on 2010-05-08
[http://www.theinquirer.net/inquirer/news/1610079/new-ubuntu-eats-power-windows](http://www.theinquirer.net/inquirer/news/1610079/new-ubuntu-eats-power-windows)

I guess Ubuntu has a little power issue.  What can I do about this?

---

### Post by darolu on 2010-05-08
According to the article: Install the Nvidia propietary driver. I don't know if this affects other computers the same way, ie. laptops without nvidia gpus.

---

### Post by P4man on 2010-05-08
As much as I usually like phoronix articles, this one is terrible.
For starters the numbers for either OS are unbelievably high. 30-40W for a netbook? My old 15" notebook with 2 hour batterly life doesnt draw that much from the wall unless its charging the battery. Cant be right. Did they even remove the battery?

Then they dont mention any specifics, like LCD brightness. Ubuntu sets LCD brightness to 100% on AC, windows doesnt  (75% I read elsewhere) . Did they adjust that? That alone could make the difference. No mention of desktop effects, no investigation if cpu scaling was working properly, if laptop mode was enabled.

I could go on.

Its certainly possibly ubuntu has a power consumption issue, in general or on specific notebooks (and perhaps nvidia related?0 but this article is not showing that to me. Its not showing me anything other than that  it deserves some proper investigation.

---

### Post by Cardale on 2010-05-08
I expect as much, but wanted to make sure.  I do have a couple desktops that run ubuntu and I need to save money on the power bill.

---

### Post by quadproc on 2010-05-08
I didn't see any mention of CPU usage percentage.  Many people have found that there is presently some problem in 10.04 that causes the cpu to spin and generate heat.  This power comparison will be more useful after the 10.04 power bug gets fixed.

quadproc

---

### Post by Cardale on 2010-05-08
Any word on how long this might take?

---

### Post by P4man on 2010-05-08
If you mean the Xorg memory leak, it is fixed already (it was before the release). Doesnt hurt checking your cpu usage though, open a terminal and run "top"

---

