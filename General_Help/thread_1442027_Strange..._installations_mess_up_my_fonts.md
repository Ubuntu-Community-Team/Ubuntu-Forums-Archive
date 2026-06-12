---
title: "Strange... installations mess up my fonts?"
date: 2010-03-29
forum: General Help
---

### Post by Cranio on 2010-03-29
Now that's strange... sometimes I lose some of my fonts.

Or better: after certain operations (still not sure, but it seems to me that this happens when I use Synaptic or install something from the GUI), some fonts get wrecked and appear on GNOME only as unreadable sets of boxes.

Only a bunch of fonts are affected, like DejaVu or Monospace or BitStream Vera Sans, while the vast majority just work fine - but as you see they're system fonts so some dialogs become unreadable, and some softwares complain about having issues. For example, I launched *gedit* from shell and read:
```

Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Bitstream Vera Sans 8'

(gedit:9704): Pango-WARNING **: font_font status is: <unknown error status>

(gedit:9704): Pango-WARNING **: scaled_font status is: out of memory
```

I came iup with a rather clumsy workaround with this script:
```

#!/bin/sh
sudo cp -rv ~/fonts/* /usr/share/fonts/
fc-cache -rv
```

but as you can see it's far from an ideal solution.

How can I fix this? The fonts are still there, but in some way the OS cannot use them anymore.

---

### Post by stinkeye on 2010-03-29
Make a link to your fonts so root can use them as well
```
sudo ln -s ~/.fonts /root/.fonts
```

Can also do the same for themes and icons.
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
```

---

