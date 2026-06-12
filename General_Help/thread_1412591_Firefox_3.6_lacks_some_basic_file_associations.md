---
title: "Firefox 3.6 lacks some basic file associations"
date: 2010-02-21
forum: General Help
---

### Post by warnec on 2010-02-21
Hi. This problem is not related with Ubuntu in specific, but I assume that every Linux forum could be helpful, and ubuntuforums.org is propably the biggest one :D

My problem is that in the Firefox Preferences window, there is very small amount of filetypes and apps that are associated with them. There is RAR, for example, gzip, TAR, all kind of OO files like ODT, ODM, but some basic Windows-specific are lacking (ex. DOC, XLS).

I would like to know how to add them. I know there's a file named "mimeTypes.rdf" but I'm not experienced enough to edit it myself. I think it would help me very much if you could help me with that.

I'm attaching my mimeTypes.rdf.

Some filetypes i think I'd need most:

*PDF 
*DOC
*XLS
*PPT

Propably some more, but these are the basic ones I need. For PDF, it should be /usr/bin/okular, and for Word extensions, /usr/bin/soffice (AFAIK, OO.org can find what kind of file it is about to open and launch the appropriate one (like Calc, Writer))

---

### Post by warnec on 2010-02-21
nobody? :(

---

### Post by bodhi.zazen on 2010-02-21
How did you install firefox ?

I installed ff 3.6 by using the binary from mozilla and did not come across this problem.

I advise you simply add the associations you need as you go.

---

### Post by warnec on 2010-02-21
I use Archlinux and had Firefox already installed. I cannot add any more associations - I can only edit the ones there are already in the program in Settings. When I try to download a file which is not on the list (as .doc) it only lets me download it, not open. Then, when I open it by double-clicking in the Downloads window, it uses a rule caled "file" in my Firefox settings menu, which seems like a rule for all generic files where none of the other rules apply. So for example, I can set "file" to "/usr/bin/soffice" but .pdf files also are recognized as "file" and OpenOffice tries to open them. I cannot change that. 


I think the simplest way to solve that would be to add more mimetypes and rules, but as it turns out, it can only be done using this .rdf file.

PS.: I'll ask in the Arch forum.

---

### Post by lovinglinux on 2010-02-21
> **warnec said:**
> I use Archlinux and had Firefox already installed. I cannot add any more associations - I can only edit the ones there are already in the program in Settings. When I try to download a file which is not on the list (as .doc) it only lets me download it, not open. Then, when I open it by double-clicking in the Downloads window, it uses a rule caled "file" in my Firefox settings menu, which seems like a rule for all generic files where none of the other rules apply. So for example, I can set "file" to "/usr/bin/soffice" but .pdf files also are recognized as "file" and OpenOffice tries to open them. I cannot change that. 


I think the simplest way to solve that would be to add more mimetypes and rules, but as it turns out, it can only be done using this .rdf file.

I would try to delete the *mimeTypes.rdf*. Close Firefox before doing that. This will reset all file association settings and restore the default options.

---

### Post by llamabr on 2010-02-21
Uh huh.  Another editor suggested just adding them as you go.  What happens, for example, when you try to dload a .ppt file?  firefox should open a dialog asking what you want to do with it.  At that time, you can associate an app, and click 'always do this for files like this' and it'll set the mime type for you.

does that not work?

---

### Post by warnec on 2010-02-21
I'm shocked to say that, but it works **now.** Before, when clicking on a download link of a file with filetype not yet associated, I had only the radiobutton with "Download" option, no "Run with:", but **it is here now.**

I have already set PDF to Okular, and XLS,PPT,DOC to OpenOffice. I am truly astonished and have no idea why it worked now. Linux magic! :D 

(and these associations have appeared in Firefox Settings, so seems like the problem is solved.)

Sorry for taking Your time, but as said, I am 130% sure I had no option to open before. Glad it works now ;)

---

