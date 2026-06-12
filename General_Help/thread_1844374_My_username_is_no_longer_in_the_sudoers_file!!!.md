---
title: "My username is no longer in the sudoers file!!!???"
date: 2011-09-15
forum: General Help
---

### Post by Ron Jones on 2011-09-15
Here's the situation:

My PIX 501 died, and I'm attempting to use a Soekris 5501-70 card to install the embedded version of Pfsense on a Compact Flash card.

I had a bit of drama getting the image loaded onto the CF card, then getting minicom to let me attempt to communicate (still haven't gotten that straightened out yet).

Somewhere along the way, i have lost the ability to issue the "sudo" command. Now, I cannot make changes to my system, install software... etc.

Can anyone help me troubleshoot this issue?

Thanks,
Jones

---

### Post by sisco311 on 2011-09-15
You can fix it in the recovery mode:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

---

### Post by Ron Jones on 2011-09-15
That link did the trick, thanks!

For some reason, my username had been deleted from the admin group.

Jones

---

