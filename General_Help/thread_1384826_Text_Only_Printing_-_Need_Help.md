---
title: "Text Only Printing - Need Help"
date: 2010-01-18
forum: General Help
---

### Post by Barph633 on 2010-01-18
I really don't understand how this is so difficult, but I can't seem to find the answer anywhere, so I'm hoping that someone may be able to help me.  I am investigating switching to Linux for some work related applications, and one in particular is giving me a huge problem.

We have a web based application that has a single specific function to pop up a new web browser page with flat text control codes on it that we print to a thermal label printer.  In Windows, we select "Generic Text Only" as the print driver, and remove the header/footer from IE, and after a File/Print the output to the printer is the flat text from the page to the printer, which interprets the control codes and spits out the label.

I can't seem to get this to work in Linux (using Ubuntu 9.10, but could possibly use other flavors if needed, as we're also reviewing SLED 10 on thin clients), but I assume this would be the same kind of thing for just about any flavor of linux.

I've tried choosing the Generic Text Only and Generic RAW print drivers in Linux, and if I save the control codes in a text file and use lp or lpr I'm able to print the labels without problem.  If, however, I print through the GUI print function, it seems to convert the file to PostScript, which the thermal printer doesn't understand.

Any ideas how to get the GUI to output a flat ascii text print job?

---

### Post by Barph633 on 2010-01-22
OK, so in case anyone else has this problem, I wanted to post a follow up.  It turns out that this is simply not possible.  This may not be 100% technically correct, but this is my take on what's happening (and I'm sure it's close).

For any application that uses the gnome printing interface (libgnomeprint) there is no such thing as raw "text".  The entire job of libgnomeprint is to wrap everything up in postscript, and then let CUPS deal with it.

So, for example, if you print a text file, libgnomeprint turns it into a postscript, and if your printer is non-postscript then CUPS will use filters to convert it to the format that is needed by your printer (PCL for an example).  If you have a "RAW" or "Text Only" printer set up, then it will simply send the postscript directly to the printer, which will print garbage if it is not expecting postscript.

While this seems really limiting (heck, Windows has a better way of dealing with print jobs), it's just the limitation of printing in Linux.

Anyway, the solution for my situation was this:
We changed our process so that when the Firefox window pops up with the label code, instead of doing File/Print, we are doing File/Save, and saving it in the default directory (that we set).  We have a shell script that checks every 3 seconds to see if there is a file in the directory, and if so, it sends it to the default printer.  Since the shell doesn't use libgnomeprint, the lpr command will send only the text to the printer.

---

### Post by padmanto on 2010-03-29
Hi there,
Glad u've solved ur problem.

I just came across your posting when trying to print barcode using Zebra TLP2844 printer connected with USB from Firefox.

Finally found jZebra from [http://code.google.com/p/jzebra/](http://code.google.com/p/jzebra/)

This is a simple applet which can send EPL Command in raw  to my Zebra printer.

---

### Post by fatbuttlarry on 2011-07-07
Sorry to bump this thread, but as the author of jzebra (and a fellow Ubuntu user) this project is still very active.

We also have a mailing list for any technical questions!  Please follow the link provided by padmanto and we'll be happy to help!

-Tres

---

