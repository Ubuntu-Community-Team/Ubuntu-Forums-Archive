---
title: "system-config-printer overrides duplex setting"
date: 2012-03-20
forum: General Help
---

### Post by taps on 2012-03-20
At some point recently (after upgrade to Oneiric, but not immediately), I have been unable to determine duplex setting from the application (mainly LibreOffice and acroread, but also others). Every print job follows the default setting from system-config-printer, regardless of what is set by [Printer] Properties in the application.

Obviously, this is not a fatal bug, since I can always open up system-config-printer before each print job and set it as I like it. However, I would rather not.

The same problem replicates on my 32-bit desktop, 32-bit netbook and 64-bit desktop. All have the latest updates, including the latest CUPS.

I really have no idea as to how to go about trying to investigate this further, let alone solve it. Any suggestions?

Thank you.

EDIT: The same problem occurs with both HP OfficeJet Pro L3680 and RICOH Aficio SP 3410SF.

---

### Post by kurt18947 on 2012-03-20
I don't know but will be following this thread.  I run into the same thing with Brother printers & envelopes (paper size/type).  HP seems to have their own printer subsystem.  I wonder if they have the same problem?

---

### Post by taps on 2012-03-22
Anyone?

---

### Post by taps on 2012-03-29
What, no one has any idea? Please help if you can. Thanks.

---

### Post by plucky on 2012-03-29
Try the CUPS interface from Firefox.

Type into the address bar ```
http://127.0.0.1:631/
``` and make the changes there.

Good Luck

---

