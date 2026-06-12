---
title: "Various segfaults and/or crashes"
date: 2011-07-23
forum: General Help
---

### Post by nereid on 2011-07-23
Hi folks,

I have some curious errors and crashes since yesterday. 

Firefox crashes without saying anything or just freezes. Thunderbird also crashed once without any reason, as far as I could discern.

Compiz is another candidate. Either it segfaults and sends me back to the GDM login screen or it crashes in another way, resulting in a flickering window with an unreadable error message (just an empty window with the nautilus icon in the menu bar, background image stays the same, Unity or any other compiz things are gone). I even had some real X segfaults mixed in.

What really annoys the hell out of me is, that I can not find a reason for this. The last package I have installed was the update for logrotate and memtest86 told me, that I do not have any errors in my RAM.

I would be happy, if anybody has any idea, where this comes from. Thanks to the various programs I can not really pin it down (besides faulty RAM, which memtest86 denied).

Thanks in advance for any hints.

---

### Post by lovinglinux on 2011-07-23
Looks like faulty memory, but if you say it is fine, then I don't know what else could be causing this. Do you have the latest video card driver installed?

---

### Post by nereid on 2011-07-23
Thanks for the answer, I am currently using the NVIDIA binary drivers 270.41.06.

I tried to use the recently released version, but that just gives me the known XID Nvidia errors (freezing X or at least making it so slow, that it appears, that X is frozen), requiring killing X or restarting.

On the other hand, things were quite fine for the rest of the day ;) (keeping fingers crossed).

---

