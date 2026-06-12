---
title: "Opening MS Word Docs in OpenOffice - Formatting Changes"
date: 2011-02-18
forum: General Help
---

### Post by Shepherd X on 2011-02-18
I noticed that files that were written in MS Word 2003 change when opened in Open Office 3.2.1 This usually involves tables, lists, and image placement, as well as page margins and boundaries. It sometimes makes it annoying when reading files saved in MS Word .doc format that other people send me. Does anyone know if there is an extension to fix this? Or settings that can be changed? Also, was this addressed in version 3.3.0 of OpenOffice? Has anyone tried it on LibreOffice?

I don't want to install VirtualBox, Windows, and Office to read Word files properly. I dislike MS.

---

### Post by mikewhatever on 2011-02-18
Unfortunately, the inconsistent formatting stems from the fact that MS Office format specifications aren't open, so that only MS can fully support them. I don't think there is any meaningful way to address it.

---

### Post by oldfred on 2011-02-18
Often the biggest issue is fonts. Even similar fonts will have slight space differences that then can change a line length. If non-standard fonts are used it will always be a problem. Even in windows, you can have one user specify a special font that another user does not have, and Word will use one close but not identical. But most windows systems have all the standard fonts.

Have you installed the ms fonts?

apt-get install msttcorefonts

---

### Post by Shepherd X on 2011-02-18
Yeah, I have them installed.

This problem isn't really and Ubuntu/Linux problem. I had the same problem when I used to use OpenOffice on MS Windows. The formatting of documents created in Office 2003 would change, which was very annoying. Even when I was a MS Windows user, I didn't like installing MS Office (especially all the post-2003 versions) because of how it would slow down my system.

But I was wondering if there was a solution to the problem via OpenOffice settings.

Thank you for the replies.

Long live Linux and Open Source Software!

---

### Post by AlphaLexman on 2011-02-18
> **Shepherd X said:**
> This usually involves tables, lists, and image placement, as well as page margins and boundaries. 
I would check the anchor position of the tables, lists and images. As I recall MS has default anchor positions, i.e. relative to a character, paragraph, margin or page. Of course if every MS anchor was absolute by default, OOo could import a lot better.

---

