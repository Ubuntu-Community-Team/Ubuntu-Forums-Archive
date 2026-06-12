---
title: "Hylafax install issue"
date: 2009-07-15
forum: General Help
---

### Post by epsolon77 on 2009-07-15
I am trying to reach anyone who has attempted to install Hylafax from the repositories to see if there is a bug in whatever version is in the repository.

I have been fighting with the default install of Hylafax installed using the Apt-Get command on 8.04.  Faxing works GREAT, however confirmations show up as a PDF document with the .ps extension.  When you look at the attachment in a text editor, the first line is %PDF-1.4, so I know it is a PDF.  While tracing through the Notify script I was able to isolate the issue to before the Notify script is called, which means it is being imporperly converted in the main faxing system.  I was able to work around this issue by simply telling the conversion script that when it detects the file as a PDF to be converted to a PDF to copy the file to a temp directory and rename with the PDF extension.  

I am by no means an expert at coding, but I know enough to be dangerous, which is why I want to know if anyone else has experienced this problem.  It has done this to me on two different installs.  This does not, however, rule out human error on my part.  Please let me know either where I can look for the conversion process in the main Hylafax scripts, or let me know if you have had this issue as well.  If many have had this problem I will look further into where the bug should be submitted.

---

