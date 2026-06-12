---
title: "how to print a &quot;test page&quot; from command line"
date: 2009-07-01
forum: General Help
---

### Post by loli22 on 2009-07-01
hi guys,

please, can you show me how to print a test page from command line.
i mean instead of pressing "Print Test Page" button in printer configuration GUI, i want to print the same thing using the terminal.

big thx guys.

PS: i'm not talking about printing any file, i'm talking about the exact file that get printed when you press the button
"Print Test Page"

---

### Post by rmhopper on 2010-10-11
OK.  I ran across your post because I needed to do exactly the same thing!  So I looked around until I found what I needed.

At least on my system, the Ubuntu print test page is located at /usr/share/system-config-printer/testpage-letter.ps (there is also an A4 version for you European dudes).  So the command line would be:

lpr -P "YourPrinterName" /usr/share/system-config-printer/testpage-letter.ps

Works for me!

I have a couple of rarely-used inkjets in my network, and I schedule this via cron once a week or so to keep the ink heads from drying out.

---

