---
title: "System Removal"
date: 2012-03-30
forum: General Help
---

### Post by jim_deadlock on 2012-03-30
I'm buying a new SSD and I want to install my system onto it but use the /home and swap on my original HDD. I think I can manage this part easily enough but what I'm not so sure about is the best way to remove the system and MBR from the original HDD afterwards.

What I plan to do is simply delete all the root directories except /home and then remove the /dev/sda1 partition (see below). This seems rather messy though, it there a better way to do it?

[IMG]http://i932.photobucket.com/albums/ad168/jim_deadlock/hdd.gif[/IMG]

---

### Post by Bill Z on 2012-03-30
May take longer but it is safer if you backup stuff in your /home directory , format your disk then reload /home.

Maybe I am not understanding you completely.

---

### Post by jim_deadlock on 2012-03-30
Yes I think you're right that's probably a better idea thanks.

---

