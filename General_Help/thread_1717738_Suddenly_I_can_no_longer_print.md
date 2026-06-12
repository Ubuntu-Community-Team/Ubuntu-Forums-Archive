---
title: "Suddenly I can no longer print"
date: 2011-03-30
forum: General Help
---

### Post by Objekt on 2011-03-30
I have no idea what happened, but as of around a week ago, I can no longer print in Ubuntu 10.04.

The printer is a Brother MFC-7440N connected to my LAN.  I have never had a problem before printing to it from any of my computers, regardless of whether they were running Windows XP, Windows 7, or Ubuntu 9.10 or 10.04.  I am still able to print from Windows 7, so I'm reasonably sure there's nothing wrong with the printer or network configuration.

But I can't get it to print at all from Ubuntu.  I already tried reinstalling the drivers and re-setting it up in CUPS - no change.  Every time I try to print a test page, the printer does nothing, and "Document Print Status" shows the job as eternally "Pending."

If I go to the CUPS printer page ([http://127.0.0.1:631/admin](http://127.0.0.1:631/admin)), the job status shows as "Paused - "Unable to locate printer 'MFC-7440N'!"

I don't know why CUPS thinks it can't locate the printer.  When I was setting up the printer in CUPS, CUPS properly detected it on the network, no problem.

I can see the printer in the CUPS administration page, and even change settings.  The one thing I cannot do is get it to actually print!

Like I said, the printer works fine through Windows, so I think this is an Ubuntu problem, not a printer problem.  Any ideas?

eta:
When I open "System->Administration->Printing," there's an icon of the printer with a green-circle check mark, as if everything is OK.  But if I right-click, the "Enabled" box is not checked.  Checking it myself has no apparent effect.

---

### Post by Objekt on 2011-04-06
What, nobody has EVER had this problem before?  Really??

update:
Found this thread from late last year: [http://ubuntuforums.org/showthread.php?p=10428811#post10428811]("http://ubuntuforums.org/showthread.php?p=10428811#post10428811")

Someone else had almost exactly the same problem.  Things did not work for me again until I selected "App Socket/HP Jet Direct" and entered the printer's IP address.  After that, I was able to print a test page (and anything else I needed to print).

It just doesn't make sense that printing stopped working, even though I did nothing to cause it.  I can only guess that one of the numerous updates in the last few months broke something.

---

