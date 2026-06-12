---
title: "Printer Sharing (Installed wont work, but discovery does?)"
date: 2012-08-22
forum: General Help
---

### Post by cbanakis on 2012-08-22
I think this may be a unique problem, but hopefully someone has some experience, and a solution for it.

Trying to add a shared printer.

Using system-config-printer

If I add the printer, it is detected over the network, and installs with no problems.
But it does not work, all attempts to print result in error.

But if I turn on "Show shared printers", and select the printer that way, it works fine.

The problem with using it as is, is that we have 23 printers on our network.  So selecting the correct one, can be a problem.

I also tried turning on "Show Printers" then duplicating the discovered printer, and disabling "Show Printers"

the duplicate stays there, and all the others are removed, but the duplicate wont work correctly.

It is detected, and it prints, but prints random garblings of letters and numbers.  (Strange)

Does anyone know how I can have that printer, and only that printer listed on the computer, and have it working properly?

---

### Post by cbanakis on 2012-09-04
*Bump

---

### Post by dandnsmith on 2012-09-04
Whether it shows garbage on printing is usually a feature of the queue settings, which control what filters to use.
When you duplicate one of the shown printers, you probably don't duplicate the queue settings.
I can't, at the moment think how to suggest anything more - its something I'd have to experiment with, if I ever had it happen (when I've had problems giving garbage, it has always been because of incorrect queue settings, and its best to delete the queue and start again, as there is always something that gets missed)

---

