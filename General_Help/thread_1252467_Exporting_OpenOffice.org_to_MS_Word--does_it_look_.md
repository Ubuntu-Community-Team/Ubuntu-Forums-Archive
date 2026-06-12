---
title: "Exporting OpenOffice.org to MS Word--does it look okay?"
date: 2009-08-28
forum: General Help
---

### Post by SoylentSteak on 2009-08-28
I know it's possible to export word processor documents from OpenOffice to MS Word, but my question is, does it come out looking alright?

I may be working as a freelance translator in the future, and most clients require their documents to be delivered in MS Word format. I don't want to install Windows just for that.

---

### Post by blueridgedog on 2009-08-28
I save OpenOffice files as word format files (*.doc) frequently and have never had an issue or a complaint.  I have also carried such files back and forth to work and edited them in word with no appearance issues or other problems.  I have written most of my recent graduate class assignments and mailed them to the professors who ask for word format without objections.

---

### Post by uylug on 2009-08-28
> **blueridgedog said:**
> I save OpenOffice files as word format files (*.doc) frequently and have never had an issue or a complaint.  I have also carried such files back and forth to work and edited them in word with no appearance issues or other problems.  I have written most of my recent graduate class assignments and mailed them to the professors who ask for word format without objections.

Well. I did have a couple issues. Spacing changed often in numbered lists and text seemed to take up more space on Excel than it did on OpenOffice so it did cause some problems to me but it happened once so...

---

### Post by SoylentSteak on 2009-08-28
Nothing that would really disappoint a client, though?

---

### Post by Hagar Delest on 2009-09-02
It depends on the complexity of the document and the OOo version. For example, there were big troubles with tables in exported .doc with 3.0.1 and 3.1.0. Seems to be ok now with 3.1.1 (except some corner cases with documents made with previous versions).

Make some trials first and be prepared to switch to switch to MS Office. NB: you can still install a dual boot.

---

### Post by elewis on 2009-09-02
If you want to guarantee the look to the documents, export them to PDF. There is an icon in the OpenOffice.org tool bars in the writer, calc and impress applications to do just that. Everyone can read PDF. Microsoft formats are notoriously unstable, it seems that every couple of years they change their formats, so a "Word 2007" format is probably not the same as a "Word 2008" or "Word 2009" &c. As a result, export will always be somewhat inconsistent. That is the beauty of PDF, it is portable and shares well and it is a documented format unlike Microsoft.

---

### Post by SoylentSteak on 2009-09-02
The problem is most clients specifically request MS Word. I really would hate to go to the expense and trouble of buying Windows and setting up a dual boot just for that. :(
I'm trying my very best to be able to do this all from Linux, but clients are picky, and the world of freelance translation is competitive. It's all about who can produce the best documents for the cheapest price to the client, so I have to be in top form.

---

### Post by ad_267 on 2009-09-02
I wouldn't risk it. There can be spacing issues that make the documents appear different between the two applications. Eg something that's exactly four pages in OO.o might spill over into the fifth page when you open it with Word.

If a document uses a spaces and tabs for laying out text that will get messed up easily too.

---

### Post by SoylentSteak on 2009-09-02
What about WINE? Does that tend to look decent? I know there's a separate WINE section for that, but I didn't see a justification for another thread.

---

### Post by ad_267 on 2009-09-02
> **SoylentSteak said:**
> What about WINE? Does that tend to look decent? I know there's a separate WINE section for that, but I didn't see a justification for another thread.

The problem with WINE wouldn't be about the document looking good, it would be a matter of the application running correctly. If Word works fine in Wine then the documents will definitely turn out ok.

According to the Wine application database most verions of MS Word should run well: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=10](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10)

---

### Post by Vince N on 2009-09-02
2nd Recommendation for wine.  If you absolutely HAVE to work with MS Office then you can get around needing to install a whole second OS for it.

If you happen to have a copy of windows around you could also always boot it to a VirtualBox session and run MSOffice in that.

To be honest though I've done tons of work with Open Office and the newer versions play pretty nice with Microsoft Word.  Course there's nothing saying a newer version of MS Office is going to to play nice back.  You know how MicroSoft is.

---

### Post by ad_267 on 2009-09-02
Yeah +1 for Virtualbox if you have a copy of Windows, and as long as your computer isn't too ancient. You could always use OpenOffice and just check your documents in Word once you're done.

---

### Post by HermanAB on 2009-09-02
OOo and Word work together OK for simple documents.  Complex documents with hundreds of pages will have problems though.  The most important thing is the fonts.  If you want the doc to look the same in Word, then you absolutely have to use Microsoft True Type fonts.

Round trip conversions, where there are multiple contributors working with Word and OOo will have trouble - don't do this.  

I usually write a new doc in OOo and then export it to PDF for distribution to MS Windows clients.  That avoids all the usual problems.

---

### Post by SoylentSteak on 2009-09-02
Thanks for all the help. I think I'll give WINE a try.

---

### Post by Slim Odds on 2009-09-02
> **Hagar de l'Est said:**
> NB: you can still install a dual boot.

A VM (VirtualBox) would be a far simpler solution.

---

### Post by blueridgedog on 2009-09-03
> **SoylentSteak said:**
> Thanks for all the help. I think I'll give WINE a try.

A commercial implementation is crossover office.  It comes with support and will run most office 2003 applications.

---

### Post by Hagar Delest on 2009-09-03
> **Slim Odds said:**
> A VM (VirtualBox) would be a far simpler solution.
Perhaps. I don't know, I've never used a VM. I would fear some troubles with installation of complex applications like MS Office but I can't tell for sure.

---

### Post by Katalog on 2009-09-03
> **HermanAB said:**
> OOo and Word work together OK for simple documents.  Complex documents with hundreds of pages will have problems though.  The most important thing is the fonts. ** If you want the doc to look the same in Word, then you absolutely have to use Microsoft True Type fonts**.

Most definitely true. If you use a font that Word doesn't recognize and then it has to substitute a different font when opening the OOo document, then all kinds of hilarity ensues. I edit a lot of my MS Word documents from work in OOo Writer and have very little trouble, you just have to be kinda picky about formatting and fonts.

---

### Post by Vince N on 2009-09-03
> **Hagar de l'Est said:**
> Perhaps. I don't know, I've never used a VM. I would fear some troubles with installation of complex applications like MS Office but I can't tell for sure.
 
The VM should be fine as long as the program dosen't require 3D Accelerated graphics.  MSO  VirtualBOX is usualy pretty good at automaticly detecting the best hardware specs for the virtual machine, once thats done to load the Windows CD in the drive, set the VM up to use that CDROM and then boot the VM.  At that point it's just like installing windows and MS Office in any other PC for the most part.

---

