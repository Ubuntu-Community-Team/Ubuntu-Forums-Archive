---
title: "assigning icons to document types"
date: 2010-01-23
forum: General Help
---

### Post by RedRat on 2010-01-23
Recently I received a .docx document, the new Word format. I have no problem opening this document in Open Office, that part is fine. However, the document icon associated with .docx files is just a plain generic text type icon. How can I change the icon for all docx documents that I get?

I have done a search but the search gave me a site that does not seem to respond.

---

### Post by StuartN on 2010-01-23
> **RedRat said:**
> I have no problem opening this document in Open Office, that part is fine.

You could edit /usr/share/mime/packages/openoffice.org-common.xml to add the new extension, which should apply the existing document icon.

You could also write your own application link (e.g. [http://ubuntuforums.org/showthread.php?t=574586](http://ubuntuforums.org/showthread.php?t=574586)) and add a mime type in the file /usr/share/mime/types

---

### Post by RedRat on 2010-01-23
> **StuartN said:**
> You could edit /usr/share/mime/packages/openoffice.org-common.xml to add the new extension, which should apply the existing document icon.

You could also write your own application link (e.g. [http://ubuntuforums.org/showthread.php?t=574586](http://ubuntuforums.org/showthread.php?t=574586)) and add a mime type in the file /usr/share/mime/types
Took a look at the openoffice.org-common.xml file and the docx mime type is there. As I said, I have no problem in opening the file, I just want to change the global icon for docx files to something else. Neither of your suggestions seem to fit that bill.

It would seem to me that this should be fixable fairly easily. Perhaps in the themes manager, but I don't know that process. This can be done in Windows, so I would imagine it should be doable in Ubuntu, perhaps even easier.

---

