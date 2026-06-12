---
title: "When printing from a remote computer page size is ignored"
date: 2009-09-11
forum: General Help
---

### Post by javierrivera on 2009-09-11
This my the original setup:

- A windows terminal server.
- A couple of computers running Ubuntu 8.04 and 8.10 as clients.

The clients are in different cities, and connect to the server via internet. They run mainly firefox, thunderbird and a remote windows app via rdesktop. This app is really running on the Windows Terminal Server.

The app prints a couple of things in two different paper sizes A4 and A5. The users just select the paper size on the windows print dialog and it's done.

Printers are shared in CUPS. In windows they are created as net printers using ipp. The driver on windows is always an Apple PS printer.

Now I add a new computer (200 Km away from me BTW) running Jaunty (9.04). It now ignores the paper size in the windows printer dialog, and tries to print the output in the default value selected on the client (Ubuntu) computer.

I have checked the cups error_log after setting it at debug level. It seems to read the PPD and pass the default size in it as a parameter to the ps2pdf filter. I can provide a clean version of the file if someone likes.

I have used an ugly workaround, I just created to printers in the client, with different paper sizes, of course I need to create two printer in windows too.

Has anybody a better workaround?. Should I open a bug?. Is this really a bug or does it make sense (after all usually the remote computer knows which paper the printer has)?.

---

