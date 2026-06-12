---
title: "OpenOffice Writer - need to print multiple data records on same page"
date: 2010-02-19
forum: General Help
---

### Post by gradysghost on 2010-02-19
Here's the basic situation:

I've got an OpenOffice Base database that I've registered with OpenOffice on the whole.  This database contains names and addresses.  I have already used this database to create a form letter, and that worked flawlessly.

But now I want to use those addresses for some labels.  Unfortunately, OpenOffice doesn't have a native labels template for Avery 18160 paper (Avery template 5160), so I downloaded the template direct from Avery.  The template is in Word Doc format, but it doesn't seem to matter if I do in .doc or if I convert it to .odt or if I create my own template using either the .doc or .odt as a guide.

The label paper has 30 labels per page.  I have a little over 30 records in my database that I need to print.  I would like one record (address) to print per label.  The problem is that I cannot seem to do this.  OpenOffice always prints one record on every label for the entire page.  In other words, if I have 33 records, the output from OpenOffice's form print function is 33 pages, each page containing one address repeated 30 times.

I can get around this by going through the OpenOffice label wizard, so I know that somewhere in OOo, the option is there to change how often OOo should get new records.  But like I said before, there are no label formats in the label wizard that will work for me, and I cannot seem to manipulate the output of the label wizard to match the formatting of my actual labels.

I have been testing by printing to a file instead of paper so I don't waste my labels.

Is there anybody who has encountered this problem and can help me?  Google and the OOo forums haven't been much help yet.

FWIW, I'm running Linux Mint 8 (derivative of Ubuntu 9.10), and the version of OOo is 3.1.1.  Thanks in advance.

---

### Post by cogier on 2010-02-19
I have had a quick look at Writer and if you go File>New>Labels and select the "Options" tab there is an option for "Entire Page" or "Single Label".

Hope that helps - but I have not tried it.

---

