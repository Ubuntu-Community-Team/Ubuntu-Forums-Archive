---
title: "Change document preview as icon in Acroread?"
date: 2009-12-20
forum: General Help
---

### Post by yeeshkull on 2009-12-20
Hi all,

I've searched but couldn't find any info on (or if it's possible) to prevent Acroread (or Envince) from showing the document preview as the icon of a .pdf file and have the system default to a simple icon instead.

(I'm using Acroread in Jaunty)

Thanks

---

### Post by hugmenot on 2009-12-20
Probably this gconf key: /desktop/gnome/thumbnailers/application@pdf/enable

---

### Post by yeeshkull on 2009-12-21
> **hugmenot said:**
> Probably this gconf key: /desktop/gnome/thumbnailers/application@pdf/enable

Thanks for the reply but no luck.  I went into gconf-editor (as user and also as root) and unchecked the enable box in the pdf key, but the thumbnail preview still shows.  I also saw that the key did not include Acroread.

---

### Post by hugmenot on 2009-12-21
> **yeeshkull said:**
> Thanks for the reply but no luck.  I went into gconf-editor (as user and also as root) and unchecked the enable box in the pdf key, but the thumbnail preview still shows.  I also saw that the key did not include Acroread.

evince-thumbnailer is the only program that generates these previews. there were other keys to, try disabling all of them. search for "evince-thumbnailer" "in keys".

---

### Post by hugmenot on 2009-12-21
maybe you also have to delete your .thumbnails folder.

---

### Post by yeeshkull on 2009-12-29
> **hugmenot said:**
> maybe you also have to delete your .thumbnails folder.

Thanks for the replies.

When I'm logged in as user it shows the thumbnail but when I switch to root (using root nautilus) the icon shows as an Acroread icon.

I've read something on other posts about deleting the thumbnails fold but then how will that effect the rest of my programs I wish to generate thumbnails for?

Thanks for the replies.

---

### Post by hugmenot on 2009-12-29
When you delete .thumbnails folder it clears out all thumbnails. But they will be regenerated the next time you browse the particular folders. I expect evince-thumbnailer to stop doing that if you disable it thumbnailing in gconf-editor.

---

### Post by yeeshkull on 2009-12-29
> **hugmenot said:**
> When you delete .thumbnails folder it clears out all thumbnails. But they will be regenerated the next time you browse the particular folders. I expect evince-thumbnailer to stop doing that if you disable it thumbnailing in gconf-editor.

Hugmenot,

Yes it worked, thank you so much for your help. 

:biggrin:

---

