---
title: "Openoffice restore emergency"
date: 2011-02-21
forum: General Help
---

### Post by vacco on 2011-02-21
My computer lost power and shut down. I had just saved the .odt document I was working on in Openoffice and thought I was safe, but when opening my document again, I got a restore dialog. I clicked OK, and now my 1/2 page document is 12 pages of # and other jibberish.

Is there any way to get my document back?

---

### Post by AlphaLexman on 2011-02-21
Hopefully you haven't re-saved the file or anything! First make a backup of the original odt file. Second, in a terminal, check the filetype with file:```
file /path/to/file/filename.odt
```
If it returns 'filename.odt: OpenDocument Text' you're in luck!
Thirdly, try to open the file with 'Archive Manager' from the Applications, Accessories menu. If you don't see gibberish here save everything into a new location and post your results.

Good Luck!

---

### Post by vacco on 2011-02-21
file returns data as file type.

Archive manager is unable to open the file, as is gedit.

---

### Post by emarkay on 2011-02-21
Don't you have  the OO "Save AutoRecovery" enabled (I use 5 minutes)?  If so it's in your backup folder as old as the last time increment. If not, well, now's a good time to enable this! :)

I also, as a long time user, save incrementally, - doc1,.odt, doc2.odt, doc3.odt than the last good one I rename to doc.odt.

If OO recovery didn't work, that's your best hope, and you may have just a corrupted file.  You can try to import the file or open it with a text editor, but those are all "last gasp "ideas.  Sorry

FWIW, I got a 20 minute UPS for about a hundred bucks and it's saved me more than once!

---

### Post by Hagar Delest on 2011-02-21
Sadly, nothing to do: [22 page term paper replaced with pound signs](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=17677).

Check also the temporary folder of the system (see in OOo Tools>Options>OOo>Paths). If there are folders like sgmlf.tmp with a file having the same name inside, make a copy of that file, rename it in .odt and cross your fingers.

---

