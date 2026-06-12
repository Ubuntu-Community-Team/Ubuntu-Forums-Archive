---
title: "problem updating Grub2 after theme change"
date: 2010-01-11
forum: General Help
---

### Post by DXM31 on 2010-01-11
I changed the pic for the theme in 05_debian_theme but when I got to update-grub I get this:
Generating grub.cfg ...
/etc/grub.d/05_debian_theme: line 43: syntax error near unexpected token `fi'

I have looked at a sample debian_theme file mine looks the same except for the name of the pic.
the 'fi' is the one after the EOF
When I pasted in the image name I put .tng so I back spaced that out and there is still a '.' after the image name.
Can I just restore the 05_debian_theme file without rebuilding the grub?
Thanks

---

### Post by DXM31 on 2010-01-11
I fixed it.
I loaded up the live cd, copied the 05_debian_theme file, backed up the old one, chmod'd the copied one, made changes, and it worked.

---

