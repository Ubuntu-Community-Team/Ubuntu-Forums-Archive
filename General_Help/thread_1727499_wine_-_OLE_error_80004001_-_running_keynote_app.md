---
title: "wine - OLE error 80004001 - running keynote app"
date: 2011-04-12
forum: General Help
---

### Post by dragonfly41 on 2011-04-12
I've just installed Wine .. 

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

and started testing my first app .. an organiser keynote-nf, used in windows.

[http://code.google.com/p/keynote-nf/](http://code.google.com/p/keynote-nf/)  

Since there is no installer I just copied this folder into Program Files.

I then launched by right clicking on keynote.exe and I started to use this app, creating nodes etc.

But when I try to paste content I hit the error .. [B]OLE error 80004001
[/B]
I'm not the first to see this ..

[http://www.winehq.org/search/?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=OLE+error+80004001&siteurl=forum.winehq.org%2F#1017](http://www.winehq.org/search/?cx=partner-pub-0971840239976722%3Aw9sqbcsxtyf&cof=FORID%3A10&ie=UTF-8&q=OLE+error+80004001&siteurl=forum.winehq.org%2F#1017)

but what is the fix?

Is this question better asked on the wine forum?

---

### Post by Mark Phelps on 2011-04-12
You have to install apps in Wine, you can't just copy the executable and expect that to work.

And, looking at the WineHQ page for keynote, if you're using the version indicated there, you'll be lucky to get anything to work:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=248]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=248")

---

### Post by dragonfly41 on 2011-04-12
Thanks for the heads up on that .. this is disappointing since keynote is a neat organiser and it happens to be the first I tried.

But how does wine deal with programs which just run (in windows) when clicked .. no installation needed?

Should (simple) apps be launched via command line in Terminal?

---

### Post by dragonfly41 on 2011-04-13
I raised this question on the KeyNote-NF forum and was advised to add msftedit.dll from c:/Windows/System32 folder into KeyNote-NF directory ..

> You might try copying your msftedit.dll from your windows xp system 
 directory c:\windows\system32 to your working directory (installation) of 
 your keynote.exe file. 
  There is no installation or registration needed for msftedit.dll just needs 
 to be in the same directory. 

Alan KragI tried that tip (although taking the dll from Vista and not XP) and the OLE error was no longer seen .. but the text in the KeyNote nodes was invisible!

I noticed another error .. "module not found - msls31.dll".

After I added that second dll KeyNote-NF ran nicely in ubuntu.

I can run macros.

I'll send an update to the winehq forum.

---

### Post by Mark Phelps on 2011-04-13
> **dragonfly41 said:**
> ...But how does wine deal with programs which just run (in windows) when clicked .. no installation needed?

Should (simple) apps be launched via command line in Terminal?
Wine is a set of DLL files that were rewritten to replace the Windows OS kernel calls with Linux kernel calls.  It's not a set of Windows programs, per se. And , more importantly, it's not an emulation of MS Windows.  So, stuff that comes with MS Windows is not necessarily going to be there with Wine.

I don't use Wine anymore -- tried it for six months, found it to be all but worthless.  So, I don't know which (if any) MS apps are installed by default.  But generally, you have to install an MS app in Wine before you run it.

---

