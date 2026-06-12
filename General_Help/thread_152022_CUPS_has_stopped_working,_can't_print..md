---
title: "CUPS has stopped working, can't print."
date: 2006-03-29
forum: General Help
---

### Post by chris_andrew on 2006-03-29
Hi, all.

I have had Breezy installed since it was released, and my printing was working like a dream.  I went to print to a local printer last night, and was told that I couldn't connect to the CUPS server (I think that's what it said).  As I say, this usually runs on the same box, so not sure why it has died.  Obvious thing to do is reboot, to restart the service, but am in the middle of a big job, and like my *uptime* figure!  

I tried to connect to localhost:641 (or whatever the man page said), but on this occasion (unsurprsingly) was not able to get authority to view the admin web page.

Could anybody tell me how to restart the service from a terminal window?

Many thanks,

Chris.

---

### Post by helpme on 2006-03-29
sudo /etc/init.d/cupsys restart

---

### Post by chris_andrew on 2006-03-29
That looks like exactly what I need.  Thank you, will let you know how I get on.

Cheers,

Chris.

---

### Post by chris_andrew on 2006-03-29
Hmm, that didn't work.  It did what it should have, and I also used the stop and start options.  Unfortunately, I still can't contact my CUPS server.  May have to go for a reboot, as big job finished, now.

Not the way I would have liked to have addressed this problem.

Thanks,

chris.

---

