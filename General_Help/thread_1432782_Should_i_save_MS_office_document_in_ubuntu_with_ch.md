---
title: "Should i save MS office document in ubuntu with changing its format?"
date: 2010-03-18
forum: General Help
---

### Post by macb on 2010-03-18
:KS hi i am a new user to ubuntu, i recently install hte ubuntu with windows xp.
now when i open the ms office document in ubuntu, edit them and save them ..then it asked to change the format of file...should i save it with the new format ?
                                        And after changing is this make effect on the document when i open in the in windows? plz tell me

---

### Post by howefield on 2010-03-18
If you want to use the same document on a windows machine, probably best to keep the file type as it was.

If you are using Openoffice, it is asking you if you want to save the file as an .odt which you may not be able to open in your windows machine, unless you also install openoffice in windows. Keep the original file format and you'll be safe enough.

---

### Post by srs5694 on 2010-03-18
For the most part, I agree with howefield; however, be aware that if the document includes complex formatting, it's conceivable that OpenOffice.org won't save it back in MS Office document format quite right. Personally, I'd save documents in *both* formats for a while, at least until I was confident that the types of formatting I normally do are saved properly in both directions. That way, if there was a problem I'd stand a better chance of recovering the document in some form with minimal fuss. This isn't likely to be an issue with simple document formats (typical letters and other straight text files with occasional italics or whatnot), just with complex formats (multi-column documents with embedded graphics and heavy use of styles, for instance).

---

### Post by Hagar Delest on 2010-03-20
Indeed. Remember that until recently, the MS Office formats (.doc, .xls, ...) were not documented. The import/export filters have been made by reverse engineering. So they may introduce some flaws. That's why it's so important to use true open and documented formats like ODF. It insures your data are safe.

NB: there are plugins to read ODF in MS Office, the Sun one is the better IIRC.

---

### Post by efflandt on 2010-03-20
There is a free Open Office version for Windows.  But if you also have MS Office, you may want to avoid setting Open Office as the default for MS Office file types in Windows (it asks you about that during OO installation).  Then you would work with either file type with the program that fully understands it, and then save the file as an MS Office type if someone else needs to be able to use the file.

But if you need someone else to just be able to read/print the file without changing it, you can save it as a pdf file (or use cups-pdf package to "print" a pdf file from any application).

---

### Post by Hagar Delest on 2010-03-20
> **efflandt said:**
> you may want to avoid setting Open Office as the default for MS Office file types in Windows (it asks you about that during OO installation).  Then you would work with either file type with the program that fully understands it, and then save the file as an MS Office type if someone else needs to be able to use the file.
The problem is that quite only MS Office understands correctly its OOXML file format. It's not even the flavor that has been ISO-certified. That's why it's important to work with _true_ open and documented formats like ODF!

Sticking to the MS Office format is just supporting their vendor lock-in policy.

---

