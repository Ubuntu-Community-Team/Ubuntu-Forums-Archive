---
title: "Font change in Virtual Consoles"
date: 2010-10-04
forum: General Help
---

### Post by donniesito on 2010-10-04
Good afternoon everyone!

I have seen this question asked a number of times, and researched on the web for the answer, but nothing seems to work. I want to change the FONT & FONT SIZE of the virtual consoles, but can't figure out what's not working.

I have tried editing grub and changing
```
GRUB_CMDLINE_LINUX_DEFAULT=""

to

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
```

All that did was change it so my consoles display in 80x25, which as you all know looks like hell.

That behind me, I tried editing the /etc/default/console-setup:

```
# The codeset determines which symbols are supported by the font.

# Valid codesets are: Arabic Armenian CyrAsia CyrKoi CyrSlav Ethiopian

# Georgian Greek Hebrew Lao Lat15 Lat2 Lat38 Lat7 Thai Uni1 Uni2 Uni3

# Vietnamese.  Read README.fonts for explanation.

CODESET="Lat15"



# Valid font faces are: VGA (sizes 8, 14 and 16), Terminus (sizes

# 12x6, 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBold (sizes

# 14, 16, 20x10, 24x12, 28x14 and 32x16), TerminusBoldVGA (sizes 14

# and 16), Fixed (sizes 13, 14, 15, 16 and 18), Goha (sizes 12, 14 and

# 16), GohaClassic (sizes 12, 14 and 16).

FONTFACE="Terminus"

FONTSIZE=20x10


```

No matter what I tried, I couldn't get the font to change..  I even tried just naming the fontface to Terminus16  just to see.. Nothing

Any help here would be appreciated -- thanks in advance! If I figure something out, I'll post an update.

---

### Post by donniesito on 2010-10-04
I hate to do this, but *bump*.

---

