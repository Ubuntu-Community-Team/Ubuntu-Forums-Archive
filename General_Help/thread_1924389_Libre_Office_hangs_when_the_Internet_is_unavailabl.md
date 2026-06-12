---
title: "Libre Office hangs when the Internet is unavailable"
date: 2012-02-12
forum: General Help
---

### Post by Paddy Landau on 2012-02-12
I have discovered a bizarre problem.

Whenever the Internet is unavailable (because my router says so -- there are times that Internet access is restricted), Libre Office hangs when trying to open a document.

If Internet access is made available, Libre Office will respond again.

Any idea what I can do to fix this?

I have Ubuntu 11.04, fully updated, and Libre Office version 3.3.4 (the standard one from the standard repositories).

---

### Post by Ms. Daisy on 2012-02-13
Weird. I can't reproduce it on my 11.04 system.  I unplugged my ethernet on the desktop and was able to open the application Libre Office 3.3.4 as well as open an existing Libre Office document.

Is it all documents or only certain ones?

What do your logs say when you're trying to open the document?

The question I'm left with is "what would make Libre Office dependent on an Internet connection?"  That's behavior I would expect from a malicious document (given that my knowledge of such things is barely beginner).

---

### Post by Dangertux on 2012-02-13
Is the document you're opening by any chance calling an internet resource? IE maybe a picture that's at a webserver or sometihng like that?

If not it could just be checking for updates and waiting to time out before it opens your document.

Hope this helps.

---

### Post by haqking on 2012-02-13
> **Dangertux said:**
> Is the document you're opening by any chance calling an internet resource? IE maybe a picture that's at a webserver or sometihng like that?

If not it could just be checking for updates and waiting to time out before it opens your document.

Hope this helps.

+1

Probably an update.

See here [http://help.libreoffice.org/Common/Check_for_Updates_1](http://help.libreoffice.org/Common/Check_for_Updates_1)

---

### Post by Ms. Daisy on 2012-02-13
Well please ignore my paranoia then! 

Hmm... I don't have any options to update Libre Office like haqking's documentation shows. But I do have the Update Manager running automatic updates for supported software. That must disable the update from within Libre Office.

---

### Post by Andrew_P on 2012-02-13
I installed LibreOffice 3.4.5 a few days ago and just ran a test by disconnecting from the network via the panel applet (not by physically pulling the plug).  LibreOffice Writer starts up fine and appears to run normally.

I did, however, install the optional local LibreOffice Help package.  Did you?  Maybe the software is checking for access to the online help and is thus very slow in coming up.

---

### Post by Paddy Landau on 2012-02-14
Thank you for all the suggestions.

It seems the answer is as some of you  suggested, i.e. searching for an update.

Here's why I have come to that conclusion:

[LIST]
[*]If I have Internet access, watching System Monitor shows that there is Internet access as it loads the requested document.
[/LIST]

[LIST]
[*]If I disconnect the Internet by pulling the Ethernet cord or by disabling Internet access via the applet (hence Ubuntu realises that it is off-line), Libre Office does not hang.
[/LIST]

[LIST]
[*]However, if the computer is connected but the router disallows access, Libre Office hangs. Well... I discovered it doesn't hang indefinitely but finally responds after 40 seconds. Obviously, it is trying to access the Internet, not continuing until it has realised that the site is unavailable.
[/LIST]
So the question now becomes: How do I disable that automatic search? *Or* how do I reduce the timeout?
> **haqking said:**
> See here [http://help.libreoffice.org/Common/Check_for_Updates_1](http://help.libreoffice.org/Common/Check_for_Updates_1)Unfortunately, that link does not help. It says to look in Tools > Options > Libre Office > Online Update, but I do not see Online Update there, nor can I find Online Update anywhere (including within the Help).

I have found a workaround: Enable Systray Quickstarter. That's OK if you have sufficient memory, but if memory is tight, that's not desired.

I shall mark this thread as solved, because my question has been answered. Thank you all for your contributions.

---

