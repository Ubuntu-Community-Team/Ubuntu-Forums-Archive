---
title: "Nautilus elementary crashes on Wastebasket, Computer  and Network locations."
date: 2011-04-15
forum: General Help
---

### Post by Mr_VeRiTy on 2011-04-15
Hi, so months ago I installed nautilus elementary and it worked fine, but cover flow didn't work. Months later I used the command:
```
echo "export CLUTTER_VBLANK=none" | sudo tee -a /etc/environment

```Which got it working, BUT now I can't visit Computer, Wastebasket and Network location or nautilus crashes (it the window just disappears.) Is nautilus doing this because of the command? If so how do I reverse it?

EDIT: Also, I now have to mount drives in Disk Utilities or they wont show up in nautilus (It's behaving almost exactly as if I were using "gksu nautilus" except it doesn't display a "Nautilus cannot open [Network |Computer| Trash] locations.") EDIT2: Actually it's not showing those warnings in root nautilus either...

---

