---
title: "UUID in Custom GRUB2 Script"
date: 2011-12-28
forum: General Help
---

### Post by RMOP on 2011-12-28
I created a script, 15_Boot_Something_Else containing the following:

menuentry "Boot Non-Ubuntu OS" {
set root=(hd3)
chainloader +1
}

After making it executable and updating grub, this adds a working menu item to Grub2. I had to play with it a bit, however, as the referenced HDD shows as /sdc, which I thought would be represented as /hd2 in the script above. That didn't work, so I incremented the value by one and the (hd3) did the trick.

***Should it have been possible to use a set root=UUID or some such instead of using the (hdx) notation?*** I suppose I WILL try just adding a new menuentry to the same script and try the subsitution, but I'd rather know what I'm doing than guess!

Thanks.

---

### Post by rubylaser on 2011-12-28
Yes it is possible to use UUID.  I'd suggest you take a look at the [Ubuntu manual ]("https://help.ubuntu.com/community/Grub2")for configuring menu items with UUIDs.  It covers it pretty well.

---

### Post by RMOP on 2011-12-28
> **rubylaser said:**
> Yes it is possible to use UUID.  I'd suggest you take a look at the [Ubuntu manual ]("https://help.ubuntu.com/community/Grub2")for configuring menu items with UUIDs.  It covers it pretty well.

Thanks for the encouragement. I've been in and out of that manual repeatedly, but haven't found quite what I'm looking for. But, as the manual itself declares "Page too long" so I may well have missed it. I'll continue to revisit it. But I have to say, Grub2 is seriously unfriendly.

---

