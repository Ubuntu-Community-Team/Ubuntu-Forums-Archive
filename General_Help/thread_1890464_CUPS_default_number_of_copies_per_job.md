---
title: "CUPS default number of copies per job"
date: 2011-12-03
forum: General Help
---

### Post by astrognome on 2011-12-03
I have a point of sale (POS) system that prints to a receipt printer.  For most, if not all, transactions, I would like to print two (2) copies of the receipt.  The printer has the option of cutting the paper after a completed job, and I would like to utilize this ability.  Using the POS system to print two copies submits the two copies as one job, thereby requiring me to manually cut the receipt between the two copies.

I have been searching for a server-side configuration in CUPS to take one print job and either print two copies and allow the cut option, or duplicate the job after the first one is complete.

Does anyone have any thoughts to a solution... other than scissors?

Thank you.
-astrognome =)

---

### Post by dandnsmith on 2011-12-03
You'll almost certainly have to send it as 2 jobs, and then configure the printer to do the cut between jobs - provided always that the drivers you use offer the capability (I know that my HP printer has some special facilities which are only available if the correct drivers are selected for the print queue)

---

### Post by astrognome on 2011-12-03
I was thinking that I would have to send it as two jobs.  Do you know of a way of having the CUPS server duplicate jobs automatically?

---

