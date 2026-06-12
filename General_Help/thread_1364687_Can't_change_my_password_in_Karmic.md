---
title: "Can't change my password in Karmic"
date: 2009-12-26
forum: General Help
---

### Post by RubberChipmunk on 2009-12-26
After running Windows 7 RC since May, which had replaced Jaunty as the primary operating system on my computer, I missed Ubuntu a bit too much, so I did a fresh install of Karmic. I put in an insanely long password, having forgotten how many times I would have to put that password in. So, I tried changing it. And the change stuck for about an hour, then it was if I had never changed it. I have changed it five times since then, and each time the change did not stick for more than half an hour. I am using the System > Administration > Users and Groups dialog to change my password.

Why can I not change my password with this method, and what do I need to do to permanently change it?

---

### Post by john newbuntu on 2009-12-26
To change it permanently, open a terminal (application->accessories->terminal) and type "passwd" without quotes.  Follow the prompts.

---

### Post by NFblaze on 2009-12-26
*passwd -d *

in the terminal

---

