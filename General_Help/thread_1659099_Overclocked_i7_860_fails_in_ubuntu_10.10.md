---
title: "Overclocked i7 860 fails in ubuntu 10.10"
date: 2011-01-03
forum: General Help
---

### Post by phil128 on 2011-01-03
Hi all.

I've managed to get a stable intel i7 860 to 4Ghz (watercooled) within windows 7. The problem I'm having is that when I boot into ubuntu 10.10 I get and error "Dereference kernel pointer?!". Now when restore my system clocks back to normal I can boot into linux with no trouble.

Has anyone had problems like this before?

Thanks

---

### Post by Vermind on 2011-01-03
Hi,
I never had problems like this. Perhaps you could write down the exact message that you get? You could change the kernel options and remove splash and quiet so you can see the console output. To try to fix this, you could add stuff like noapic nolapic noacpi or other stuff, google for linux kernel boot options for more.

---

