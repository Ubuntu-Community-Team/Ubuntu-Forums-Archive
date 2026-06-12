---
title: "Any CLI .rtf editors ?"
date: 2011-08-27
forum: General Help
---

### Post by e24ohm on 2011-08-27
Folks,
I have been playing around with DosBox and MS Word 5.5 for DOS and thought the .rtf capability would be nice on a server. The latter would allow for flexibility and the ability to modify and build .rtf documents, which support bold and italic text.

However, since my servers do not have a GUI – DOSbox will not run. Is there a native Linux editor that will run from the CLI (GUI’less), which will support the functions of MS Word 5.5 for DOS?

Thanks.

---

### Post by ninjaaron on 2011-08-27
an RTF file is human-readable as plain text and can be easily edited in any CLI text editor. You will not be able to see the formatting, but you will see the tags, which you will have to insert manually. The console uses bitmap fonts rather than vector-based fonts (the normal kind), and I don't know of any way to modify that, so I doubt actually viewing rich text will be an option.

If you really need a WYSIWYG editor for RTF documents on your server machine, you might consider installing xorg and twm with a light RTF editor such as TextEdit.  You might also consider editing RTF on a normal workstation ;)

P.S. This is more of a support-related request.

---

### Post by doorknob60 on 2011-08-27
Dosemu works without X :) I don't know of any WYSIWYG editors though, just like vim and stuff, where you could probably edit rtf files if you wanted to, but maybe not what you're looking for. But yeah, give dosemu a shot.

---

