---
title: "Free Space Shows Different number In Folders"
date: 2010-06-23
forum: General Help
---

### Post by eatmysticcyrice on 2010-06-23
Hi, I don't know how to explain this but the free space indicator in folders shows a different number than in Gparted. The Picture pretty much shows it all.

---

### Post by warfacegod on 2010-06-23
That's the system reserve. If you do the math you'll find that the difference should be just about 5%. Unfortunately for you there is nothing you should do about it. Your Home folder is on the same partition as Ubuntu. It would be very unwise to change the system reserve in your situation. If your Home was on a separate partition (a very good idea by the way) then we could get you fixed up with the "tune2fs" command. As it is, leave it alone.

---

### Post by warfacegod on 2010-06-23
If you would like to attempt moving your Home folder to a another partition, read this: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you do it post back and I'll help you with getting back that reserve.

---

