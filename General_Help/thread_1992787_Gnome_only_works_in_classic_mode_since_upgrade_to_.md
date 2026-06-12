---
title: "Gnome only works in classic mode since upgrade to 12.04"
date: 2012-05-31
forum: General Help
---

### Post by Mrenief78 on 2012-05-31
As Title shows... Gnome has been working on my machine just fine until I upgraded today.
And now only works in classic gnome mode. If I try to Log Out and Log in with Gnome - it automatically starts in Gnome Classic.. Unity works fine too.
How can I get the new Gnome to work again? Any ideas?
Thanks

---

### Post by drpjkurian on 2012-06-01
you may have this issue if you are running lower version of graphics card

---

### Post by Mrenief78 on 2012-06-01
> **drpjkurian said:**
> you may have this issue if you are running lower version of graphics card

Yes, I believe that may be the problem, it's just interesting that it was working in the earlier ubuntu version 11.10 just fine.. but no more after upgrading to
12.04. Could there be anything else I should try?

---

### Post by Mrenief78 on 2012-06-30
[FONT=monospace]Had to uninstall all nvidia.
now works again in GS 3 and no more freezing.
I'm not sure what driver it's running on now..?
here is what I used.
[/FONT]sudo apt-get purge nvidia* sudo nvidia-uninstall

---

