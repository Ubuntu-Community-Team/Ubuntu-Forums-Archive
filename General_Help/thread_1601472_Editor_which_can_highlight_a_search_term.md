---
title: "Editor which can highlight a search term"
date: 2010-10-20
forum: General Help
---

### Post by Tex-Twil on 2010-10-20
Hello,
I'm looking for a simple text editor which could highlight all occurrences of search term in the opened text file.

This is a feature that I particularly like in the Windows Notepad++ editor where any selected word is automatically highlighted in the rest of the document.



cheers,
Tex

---

### Post by Hippytaff on 2010-10-20
I would imagine nano, vim or emacs have this function, but don't quote me :-)

---

### Post by M4570D0N on 2010-10-20
You mean like when you open a file in gedit, click on "find" (ctrl+f), and type in a search term and it highlights every occurrence of that term?;)

---

### Post by Tex-Twil on 2010-10-20
> **Hippytaff said:**
> I would imagine nano, vim or emacs have this function, but don't quote me :-)
I supposed too but I'd like to have a GUI editor.

I just tried wine notepad++.exe and it's working well but a native editor would be better of course.

Tex

---

### Post by Tex-Twil on 2010-10-20
> **M4570D0N said:**
> You mean like when you open a file in gedit, click on "find" (ctrl+f), and type in a search term and it highlights every occurrence of that term?;)

It sounds like it :) But I have KDE.

---

### Post by gmargo on 2010-10-20
In **vim** (or **gvim** for the gui version), set the "hlsearch" option to have all pattern matches highlighted.  Set the "incsearch" option for an incremental search as you type the search pattern.

---

