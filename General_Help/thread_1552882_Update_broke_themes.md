---
title: "Update broke themes"
date: 2010-08-14
forum: General Help
---

### Post by blikkboks on 2010-08-14
I just installed ubuntu on my eee 901. 

Everything worked fine before I installed a lot of updates. After i restarted all the themes dissapered and there was an error saying:
 "This theme will not look as intended because the window manager theme 'clearlooks' is not installed". What happened?

---

### Post by worksofcraft on 2010-08-14
The themed reside in a folder named /usr/share/themes

You can open it in Places file manager or use "ls" at the command line. These is what is in that folder on my computer:

```

$> ls /usr/share/themes
AgingGorilla	   Default			  Industrial	       Raleigh
Ambiance	   Dust				  Inverted	       Redmond
Atlanta		   Dust Sand			  Metabox	       Simple
Bright		   Emacs			  Mist		       ThinIce
Clearlooks	   Esco				  New Wave
ClearlooksClassic  HighContrastInverse		  New Wave Dark Menus
Crux		   HighContrastLargePrintInverse  Radiance

```

---

### Post by blikkboks on 2010-08-14
Hmm... It looks like all the themes are there. But in the appearance settings there are none. What should I do?

```

ls /usr/share/themes
AgingGorilla       Default                        Industrial           Raleigh
Ambiance           Dust                           Inverted             Redmond
Atlanta            Dust Sand                      Metabox              Simple
Bright             Emacs                          Mist                 ThinIce
Clearlooks         Esco                           New Wave
ClearlooksClassic  HighContrastInverse            New Wave Dark Menus
Crux               HighContrastLargePrintInverse  Radiance


```

EDIT: Solved it by adding the themes manualy.

---

