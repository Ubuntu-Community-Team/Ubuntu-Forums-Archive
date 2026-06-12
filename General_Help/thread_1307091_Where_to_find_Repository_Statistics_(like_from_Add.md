---
title: "Where to find Repository Statistics (like from Add/Remove Programs)"
date: 2009-10-30
forum: General Help
---

### Post by ninjatiger422 on 2009-10-30
I very much liked the statistics that were available on the now-removed "Add/Remove Programs" software. Remember with the 5 stars? The more stars, the more popular the software was. It helped me find hot new software.

Where can I find these statistics? I know people opt-in to provide them w/ the Software Sources tool, but I can't find them anywhere online or in any other tool (including the new Ubuntu Software Center.)

---

### Post by ninjatiger422 on 2009-10-30
Anyway, one place is the old program.

```

sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install gnome-app-install

```

After you run that go to System > Administration and you should see it.

I hope this gets integrated into Ubuntu Software Center in the future.

---

