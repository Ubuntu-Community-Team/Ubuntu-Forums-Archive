---
title: "Missing images in pdf"
date: 2012-04-14
forum: General Help
---

### Post by Henne91 on 2012-04-14
Hey!

In some pdf files I open on my up-to-date Ubuntu Oneiric some (not all!) images that are included in the pdf are not displayed. The pdf was created by somebody using an Apple laptop.

Some images are shown but some are not, however all the images seem to be in the pdf file. I converted one of these files to a picture (some time ago, I think I was using a command line tool) and was then able to see all the images when opening the picture file.

Can anybody help me to solve this problem? Any hints if there could be missing any package or what could cause this?

How can I get debug messages (maybe also from poppler or what it is called)? When I start evince from the terminal it just gives me the following error:

"(evince:23864): Gdk-CRITICAL **: gdk_window_get_pointer: assertion `GDK_IS_WINDOW (window)' failed"

But this does not seem to have anything to do with my problem, does it?

I also tried different pdf viewers than Evince that are available via Ubuntu Software Center but they didn't work either. (e.g. zathura, ePDFViewer)

If you need any more information, please let me know!

Thanks in advance,
Hendrik

---

### Post by Henne91 on 2012-05-10
This is still an issue for me! I tried Adobe Reader and it shows the images so they are in the file.

Another thing I'll be trying is opening the affected files in Evince under Windows and see if this makes any differences.

Can anybody tell me how to find out if it's Evince which is causing the problem or another package like libpoppler or anything else?

---

### Post by sudodus on 2012-05-10
If you try another pdf viewer, for example xpdf, and have the same issue, then it is a library, otherwise it is evince itself. (I don't know, but I guess it is problem with a library.)

Generally, it is hard to tell if the problem is that the file contains some non-standard feature, or maybe some feature not yet included in your linux version.

---

### Post by Henne91 on 2012-05-22
Is there a way to find out what library evince uses and to get debugging information from this library on what the problem is? If so, how do you do it?

---

### Post by sudodus on 2012-05-22
> **Henne91 said:**
> Is there a way to find out what library evince uses and to get debugging information from this library on what the problem is? If so, how do you do it?

Try via this link
[[COLOR="Red"]_https://live.gnome.org/Evince_[/COLOR]]("https://live.gnome.org/Evince")

---

