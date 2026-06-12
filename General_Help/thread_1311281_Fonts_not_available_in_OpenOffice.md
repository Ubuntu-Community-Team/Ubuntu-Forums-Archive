---
title: "Fonts not available in OpenOffice"
date: 2009-11-02
forum: General Help
---

### Post by keta on 2009-11-02
The default monospace font in Ubuntu is Monospace (sic :mrgreen:), and it's used by many programs like gedit. For my surprise, I could not find the font in the drop-down menu in OpenOffice. I have had the same issue with OpenType fonts in another computer too.

Why doesn't OpenOffice recognize some fonts? What should I do to resolve this?

---

### Post by 013raptor on 2009-11-02
i'm having a similar problem.

[http://ubuntuforums.org/showthread.php?t=1311247](http://ubuntuforums.org/showthread.php?t=1311247)

---

### Post by Vaphell on 2009-11-02
i suspect that Sans, Serif and Monospace etc are 'aliases' of real fonts, probably of DejaVu family by default. See if they look the same. (dejavu sans, dejavu serif, dejavu mono)

---

### Post by keta on 2009-11-02
> **Vaphell said:**
> i suspect that Sans, Serif and Monospace etc are 'aliases' of real fonts, probably of DejaVu family by default. See if they look the same. (dejavu sans, dejavu serif, dejavu mono)

They look the same indeed, so I can use DejaVu Sans Mono in OpenOffice, thanks.

However, this would be a temporary solution, as the Monospace font exists in the folder /usr/share/cups/fonts. And the same happens with other fonts, somehow OpenOffice does not detect them.

---

