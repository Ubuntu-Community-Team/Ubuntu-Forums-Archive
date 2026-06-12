---
title: "Two printers. Two Ubuntu boxes. Two different answers."
date: 2011-04-20
forum: General Help
---

### Post by Roasted on 2011-04-20
I have two Ubuntu LTSP thin client servers set up in two of my buildings. In each of them there is also a Ricoh C2500 printer. I have added the printer to the high school's lab and the C2500 printer works there fine. I used an identical Ubuntu image on the 2nd server, which is in the Middle School. In that school, I cannot print. The printer will heat up as if it's about to print then just magically stop.

I've compared settings in CUPS to both servers. They're both identical. Same driver, etc. I've compared network settings on each printer. Also both identical. I rebooted the printer several times, no dice.

On the CUPS interface on the problematic server, it shows that the jobs are successfully printed. Yet they clearly never print, despite the printer heating up as if it was going to print fine.

Both of the printers were added with LPD, for what it's worth. I've also tried letting the print box auto populate the network printers in the area and adding it through there, but it too failed.

There has to be something... I just can't place where it's fouling out at the middle school level...

---

### Post by oldfred on 2011-04-20
If things are that identical is it the printer or the printer cable?

---

### Post by Roasted on 2011-04-20
> **oldfred said:**
> If things are that identical is it the printer or the printer cable?

Printer cable? These are network printers with static IP addresses assigned to them. They both work fine in Windows. One works fine in Ubuntu. The other doesn't work in Ubuntu. Yet they are otherwise identical.

---

### Post by Mark Phelps on 2011-04-21
Have you otherwise ruled out any hardware problems?

For example, does the printer have a self-test mode that you can try to confirm that it actually prints?

Also, and I know this is a lot of work, but have you tried actually switching printers to confirm that the non-working printer functions in the other location?

---

### Post by Roasted on 2011-04-23
> **Mark Phelps said:**
> Have you otherwise ruled out any hardware problems?

For example, does the printer have a self-test mode that you can try to confirm that it actually prints?

Also, and I know this is a lot of work, but have you tried actually switching printers to confirm that the non-working printer functions in the other location?

It prints fine on Windows, so hardware wise, it's fine.

They are each in buildings that are a few miles apart, so simply switching it isn't really feasible. Not to mention, it's pretty massive. I'd need a pickup truck with an open cab to move it.

Bottom line is. Both printers work. Fine. I just have NO clue why the one hates Ubuntu yet the other (same make/model) works fine...

---

