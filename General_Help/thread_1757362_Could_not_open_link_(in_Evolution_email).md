---
title: "Could not open link (in Evolution email)"
date: 2011-05-13
forum: General Help
---

### Post by cackerso on 2011-05-13
Hi new to Ubuntu forums.

I installed Evolution email.  Mostly it seems to work fine.  But when I click on a URL link in an email I get the error message:  Could not open link - no application is registered as handling this file"

Is there a fix for this?  Also since I'm new to these forum is there a guide for how best to use them?  Is there a way to mark posts as solved or unresolved, etc?  For example I searched to see if this error message came up before in the forums and I didn't see anything.  So maybe I didn't do it correctly?  How do I edit a post after I've already submitted it?

Anyway Thanks,

ackerso

---

### Post by ivanovnegro on 2011-05-13
> **cackerso said:**
> Hi new to Ubuntu forums.

I installed Evolution email.  Mostly it seems to work fine.  But when I click on a URL link in an email I get the error message:  Could not open link - no application is registered as handling this file"

Is there a fix for this?  Also since I'm new to these forum is there a guide for how best to use them?  Is there a way to mark posts as solved or unresolved, etc?  For example I searched to see if this error message came up before in the forums and I didn't see anything.  So maybe I didn't do it correctly?  How do I edit a post after I've already submitted it?

Anyway Thanks,

ackerso

Welcome to the forums!

You have to set Evolution as the default Email client under System Settings, go to System Settings-> Default or Standard Applications and set there Evolution, I think because you are using KDE, the default at the moment is Kontact or something like this.

Yes, it exists a guide, just look at the stickies on the forum or search it.
You can mark the threads also as solved.
To edit a post, click on the "Edit" button after submitting the post, its on the right side of your post.

Enjoy your stay.

Edit: The "Edit" button is on the bottom right of your post.

---

### Post by cackerso on 2011-05-14
Hi,

I tried your suggestion and it didn't seem to have any effect.  I even rebooted the system just to make sure.  I still get the same error message.

cackerso

---

### Post by dandnsmith on 2011-05-14
The message isn't right for it to indicate evolution not being the default handler for email - what you want is the thing to invoke the browser when you click on the url. Perhaps this is because you don't have a default browser?
I'm afraid that I don't know what else to suggest, except that there is a tab for applications (under firefox preferences) to decalre which application to use for various types of media found in links/web pages.

---

### Post by cackerso on 2011-05-15
Thanks, I'll give it a try with firefox.

---

### Post by drumz on 2011-05-18
Has anyone found a solution to this?  For me it's opening an attached PDF document.  I just did a clean install of Natty Narwhal, but prior to this double-clicking on the attachment opened it up fine in Acrobat Reader.  Reader is installed and working fine, and I've checked Evolutions preference settings but there's no where that I can find that I can set file type preferences.

On my previous install I had *both* Gnome and KDE installed, now I only have KDE so I wonder if there's some Gnome dependency that wasn't installed or correctly configured...

thanks!

EDIT:

Found a solution in this thread:  [http://ubuntuforums.org/showthread.php?t=1601476](http://ubuntuforums.org/showthread.php?t=1601476)

Using the "Software Manager" install the application named "File Manager". Once it's installed, launch File Manager and then try opening a PDF document.  A dialog will appear that then lets you associate PDF documents with Acrobat Reader.  Once you do that, they'll now open directly from Evolution without having to save it first.

---

