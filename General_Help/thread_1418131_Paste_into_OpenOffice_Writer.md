---
title: "Paste into OpenOffice Writer"
date: 2010-02-28
forum: General Help
---

### Post by Robbyx on 2010-02-28
I am looking for an ubuntu panel widget or a script that pastes what ever is in the scratchpad into a new openoffice text document. Has anyone seen such a panel button?

---

### Post by junapp on 2010-02-28
> **Robbyx said:**
> I am looking for an ubuntu panel widget or a script that pastes what ever is in the scratchpad into a new openoffice text document. Has anyone seen such a panel button?

something like glipper?
[http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)

Or your middle mouse button?

edit: or are you wanting a button to create the new document as well?

---

### Post by Robbyx on 2010-02-28
Sorry I have not made my request clear. I want the script to start up openoffice text and then paste in the scratchpad. I am therefore wanting the new doc to be created in the same process.

---

### Post by junapp on 2010-02-28
> **Robbyx said:**
> I want the script to start up openoffice text and then paste in the scratchpad. I am therefore wanting the new doc to be created in the same process.

If you installed xclip (sudo apt-get install xclip), you could probably create a launcher which launched something like:
```

xclip -o > /tmp/somefile.txt && ooffice -writer -o /tmp/somefile.txt

```

There is probably a way to pipe or redirect that without actually having to have that temp file (some more knowledgeable bash person can enlighten me on that one as I couldn't quite figure it out quickly enough).

---

### Post by junapp on 2010-02-28
the other option might be to look into how to run a macro (excuse my windows lingo) upon opening oofffice. I'm sure there must be a way to have a script which simply pastes the contents of the clipboard in your default template, then have it called somehow from the command line.

---

### Post by Robbyx on 2010-02-28
> **junapp said:**
> the other option might be to look into how to run a macro (excuse my windows lingo) upon opening oofffice. I'm sure there must be a way to have a script which simply pastes the contents of the clipboard in your default template, then have it called somehow from the command line.

I have just posted a question in the OOsupport web site, about how to auto run a macro on startup. I created one that just pastes the content of the scratchpad.

Thanks everyone for your help.

---

### Post by junapp on 2010-03-01
this is a bit dated, and you'd likely use oowriter instead of soffice, but the rest may still function correctly - have not tried it.

[http://www.oooforum.org/forum/viewtopic.phtml?t=2619](http://www.oooforum.org/forum/viewtopic.phtml?t=2619)

---

### Post by Robbyx on 2010-03-01
Thank you. The reference was very helpful. I ran 

oowriter "macro:///Standard.Module1.Paste_on_start"
 


Do you know why I get the Basic runtime error. Property or method not found. The error comes when  I run the macro from the command line?

This is the line that causes the error message to pop up:
document   = ThisComponent.CurrentController.Frame

> REM  *****  BASIC  *****

Sub Main

End Sub


sub Paste_on_start
rem ----------------------------------------------------------------------
rem define variables
dim document   as object
dim dispatcher as object
rem ----------------------------------------------------------------------
rem get access to the document
document   = ThisComponent.CurrentController.Frame
dispatcher = createUnoService("com.sun.star.frame.DispatchHelper")

rem ----------------------------------------------------------------------
dispatcher.executeDispatch(document, ".uno:Paste", "", 0, Array())


end sub

---

