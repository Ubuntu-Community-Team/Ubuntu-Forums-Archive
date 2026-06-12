---
title: "File Icons in Nautilus"
date: 2010-07-24
forum: General Help
---

### Post by gedumer on 2010-07-24
Ubuntu v10.04

I installed Notepad++ using Wine installer a few days ago. The editor allows you to register file extensions for example: .txt, .c, .cpp, etc. I did that with a couple extensions and discovered when I open Nautilus, The files with those extensions have the "Wine" icon associated with them... that is... the Wine icon now appears in the Nautilus file list. I don't want that... I want the original icons. I know I can change individual icons in the properties dialog, but I want to find where its stored globally in Linux to change "all" the files at one time permanently. The Notepad++ editor allows you to "unregister" the extensions, but it doesn't work... now I'm stuck with the Wine icon unless someone here can point me in the right direction.

Thanks

---

### Post by geoffjay on 2010-07-24
I'm not sure if this is correct but perhaps /usr/share/applications/mimeinfo.cache and ~/.local/share/applications/mimeinfo.cache is what you're after.

---

### Post by gedumer on 2010-07-24
> **geoffjay said:**
> I'm not sure if this is correct but perhaps /usr/share/applications/mimeinfo.cache and ~/.local/share/applications/mimeinfo.cache is what you're after.
You put me on the right track... ~/.local/share/icons contained the xpm files for the extensions in question. I would never have found that in a million years without your help!

Thanks geoffjay

---

### Post by geoffjay on 2010-07-24
Happy to help.

---

