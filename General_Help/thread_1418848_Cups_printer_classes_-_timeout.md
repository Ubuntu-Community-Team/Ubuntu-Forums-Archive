---
title: "Cups printer classes - timeout?"
date: 2010-03-01
forum: General Help
---

### Post by bazzer on 2010-03-01
Hi - have a cups server, three printers installed. One by USB, and two network printers. The network printers are in a class, and one or the other is available at once - that is, only one of the printers will be connected to the network at one time.

If you print to the class, printing takes about 12 seconds to start, and the 'correct' printer prints. If you print to the member of the class that is available, it starts in around 4 seconds.

I've searched in all the CUPS documentation for a timeout value for swapping between unavailable and available class members but the only values I've found are for network browsing of available printers.

Can anyone help?

---

### Post by bazzer on 2010-03-01
Think I have narrowed my search down to this: [http://www.cups.org/str.php?L3307]("http://www.cups.org/str.php?L3307")
What I need to know is how I can get my CUPS configuration to accept a timeout value for CUPS-Get-Devices.

HELP!

---

