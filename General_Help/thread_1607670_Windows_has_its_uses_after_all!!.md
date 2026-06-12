---
title: "Windows has its uses after all!!"
date: 2010-10-28
forum: General Help
---

### Post by johnhenry on 2010-10-28
I was doing a big backup system this morning (in Ubuntu 10.10) which was taking some time, when there was an urgent task I needed to see to, so I rashly stopped the backup with CTRL-C. Later I found that this left the recipient directory with an input-output problem, so I could not delete the truncated backup file (or any other file in the directory). I tried all sorts of chmod procedures etc., including using the usually very successful RESCUE CD from a USB pen, but nothing seemed to cure the input-output problem.

In the end, in desperation, I copied all the other files into a new directory, and then deleted the original directory from Windows 7. (I use a multiple boot system.) Windows obviously does not observe the same permissions as Linux, and it obeyed without demure! So all is now well.

I would very much welcome however any suggestions as to how I could have solved this problem from within Linux.

---

### Post by albandy on 2010-10-28
> **johnhenry said:**
> I was doing a big backup system this morning (in Ubuntu 10.10) which was taking some time, when there was an urgent task I needed to see to, so I rashly stopped the backup with CTRL-C. Later I found that this left the recipient directory with an input-output problem, so I could not delete the truncated backup file (or any other file in the directory). I tried all sorts of chmod procedures etc., including using the usually very successful RESCUE CD from a USB pen, but nothing seemed to cure the input-output problem.

In the end, in desperation, I copied all the other files into a new directory, and then deleted the original directory from Windows 7. (I use a multiple boot system.) Windows obviously does not observe the same permissions as Linux, and it obeyed without demure! So all is now well.

I would very much welcome however any suggestions as to how I could have solved this problem from within Linux.

did you run the remove and permission commands as root with sudo?

---

### Post by johnhenry on 2010-10-28
> **albandy said:**
> did you run the remove and permission commands as root with sudo?

Yes, indeed. I even thought of that this time.

---

### Post by johnhenry on 2010-10-28
Yes, indeed.

---

