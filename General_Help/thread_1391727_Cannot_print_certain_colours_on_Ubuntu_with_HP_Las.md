---
title: "Cannot print certain colours on Ubuntu with HP Laser Printer"
date: 2010-01-27
forum: General Help
---

### Post by ILMV on 2010-01-27
We have a load of machines running Ubuntu in our office, they are either on 8.04 or 9.10. We have a server which connects a HP JetDirect that connects to a HP 3550 Colour Laser printer using CUPS.

The problem we are having is we cannot print red, magenta or yellow at 100%, I've got a picture of the Ubuntu test page to demonstrate my problem:

[Picture of the offending printer test page.](http://archive.ilmv.co.uk/images/ubuntu-missing-colours.jpg)

This is obviously a pretty big problem as we are constantly receiving documents with these colours and cannot successfully print them off, we cannot just switch the grayscale, our business depends on being able to print colour (seems trivial but we handle lots of artwork).

We're using the recommended driver `HP Color LaserJet 3550 footmatic/pxljr (recommended)`, <strike>there is another driver in the list labelled `HP Color LaserJet 3550 footmatic/hpijs`. These are production printers so need to make sure any setting change won't kick is in the nuts.</strike> It would appear HPIJS is for HP Inkjets, makes sense I guess.


The problem doesn't occur in Windows.

Thanks! :popcorn:

**RESOLVED**

I've managed to solve the problem, I did indeed use the HPIJS driver (apparently for inkjets) but it seems to have worked, we're going to roll with it for now to see how we get on with it.

---

