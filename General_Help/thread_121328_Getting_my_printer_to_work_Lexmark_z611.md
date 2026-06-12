---
title: "Getting my printer to work Lexmark z611"
date: 2006-01-24
forum: General Help
---

### Post by rippon on 2006-01-24
I followed this thread: [http://www.ubuntuforums.org/showthread.php?t=83456](http://www.ubuntuforums.org/showthread.php?t=83456)
and I got the driver installed and the and it shows the printer (Lexmark Z611), but then I go to print it goes int o a "Paused" state. When I looked at what was going on I got this:

> Status: Paused: Unable to open USB device "usb://Lexmark/Z600%20Series": No such device

Any help is appreciated.

---

### Post by akiro.yamamoto on 2006-01-25
From the post you sited someone had a similar problem....
They switched it to /dev/usb/lp0 and changed the permissions as needed and that seemed to work...

---

### Post by rippon on 2006-01-25
Nope, I tried moving it there but it still doesnt work.
Anyone else have any thoughts on this issue?

Thank You.

---

### Post by rippon on 2006-02-01
Still have not found a fix :(

---

### Post by rplantz on 2006-02-01
I don't know about the Lexmark, but here's what I did with my Epson all-in-one and Samsung laser printer. (Assuming Gnome.)

1. System->Printing
2. Remove all printers (except "New Printer"). Highlight the printer and use Printer->Remove Printer.
3. Plug in your printer and turn it on.
4. Under Printers (from System->Printing) use Printer->Add Printer.
5. Select Use a detected printer.

As I recall, the next screen implies that you might want to install a driver, but it also provides a suggestion. I simply chose the suggestion. Again, I'm working from memory here, but it seemed a bit confusing to me -- almost too easy. But it worked very nicely from me. Even installed the scanning part of my all-in-one.

---

### Post by rippon on 2006-02-03
[QUOTE=rplantz]I don't know about the Lexmark, but here's what I did with my Epson all-in-one and Samsung laser printer. (Assuming Gnome.)

1. System->Printing
2. Remove all printers (except "New Printer"). Highlight the printer and use Printer->Remove Printer.
3. Plug in your printer and turn it on.
4. Under Printers (from System->Printing) use Printer->Add Printer.
5. Select Use a detected printer.

As I recall, the next screen implies that you might want to install a driver, but it also provides a suggestion. I simply chose the suggestion. Again, I'm working from memory here, but it seemed a bit confusing to me -- almost too easy. But it worked very nicely from me. Even installed the scanning part of my all-in-one.[/QUOTE]
Thanks, but I still get the same thing.
I give up!

---

