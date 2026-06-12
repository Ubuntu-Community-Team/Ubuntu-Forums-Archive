---
title: "OpenOffice.org Question - Printing Labels Always Fails to Align Correctly - Why?"
date: 2011-01-04
forum: General Help
---

### Post by djpurity on 2011-01-04
I am running Ubuntu 64-bit 10.10 and OpenOffice.org 3.2. I thought this would be a very easy thing to figure out, since the settings to do labels are built right into the software.

I bought a pack of Avery Address Labels, the 48860 kind, which uses the Avery Template 5160. These are the 1" x 2-5/8" labels, with 30 labels per sheet (3 columns of 10 rows of labels).

It's common sense to go to **File->New->Labels** and bring up the label making GUI. It's easy enough to select from the menu which type of template I want to use: Avery 5160. This matches the format at first glance of what I want to do.

However, whenever I print these labels, the labels are ***way*** off. They _DO NOT_ match the actual layout of the Avery label sheet. For one, the printer is printing the labels almost like they are bunched up too high, because the further down the label rows you go, the higher the labels seem to print until they are printing right on the label above them, and soon they are not even aligned at all and are half on one row of labels and half on another. The last row printed has the bottom half of the label row empty because the label printed only the bottom half of the label but on the top half of the label.

I tried to manually download the [template]("http://www.avery.com/avery/en_us/Templates-%26-Software/Templates/Labels/Address-Labels/Address-Label-30-per-sheet_Microsoft-Word.htm?N=4294967207&refchannel=c042fd03ab30a110VgnVCM1000002118140aRCRD") from the Avery website and then create the template manually as well. I make the tables aligned perfectly to the labels in the Avery template (which is designed for a MS Word document), matching the label template exactly with a "ghost table" that overlays them in my OpenOffice.org document. I even create the margins of the page to match the margins of the actual label sheet.

If you were to look at the way this label sheet were looking, it should print on the label sheet _EXACTLY_. But still, I get the same problem: it seems that the sheet of labels I print gets scrunched up slightly upwards from the bottom. The top couple rows print okay, but you can see each row slightly move higher and higher until they are out of bounds and into the label above them, and soon they are totally off alignment.

But according to the screen where the template and table was manually created, it should print completely differently than they are printing. It almost is as if there is some setting that is forcing the printer to believe the page of paper is smaller than it actually is, and is printing to scale on a scaled down shorter page of paper. But the settings show a 8-1/2" x 11" page, _just_ like the label sheet.

If it helps, I am using a **HP wireless f4580 printer**. I am printing wirelessly, but I have downloaded and am using the HPLIP printer toolbox which is found in the Ubuntu Software Center as installed and active.

So does anyone have any ideas why the Ubuntu software or the OpenOffice.org software seems to be *shrinking* the label page to scale to a page about half an inch or inch shorter than it really is? Even when the actual dimensions of the paper and page in the configurations in OpenOffice.org show me that it is a regular piece of paper? 

I am *_so_* confused and am wondering if this is a linux issue, a print issue, or _both_ -- that linux is using a printer designed for a windows environment and perhaps just doesn't know the meaning of printing to exact dimensions??

HELP!!! ](*,)

:confused:

---

### Post by djpurity on 2011-01-04
Wow, okay I actually already solved this problem. I am so stupid. But this was something creeping in the back of my head so I checked it out, and I was right.

I am going to leave this post up here so that in the future if anyone else runs into this mistake, they can find the solution.

I went to the System->Administration->Printing and went to my printer and went to Preferences. Somewhere in the printer settings where it listed the kind of paper and all that, there was a setting that said "Print to Scale" and I had it checked. I think this caused the print job then to change the scale of the labels I was printing to fit some setting internal to the printer settings.

When I unchecked "Fit to Scale" and printed again, this time the page printed perfectly, and the labels all fit. Hooray!

I just can't believe I figured it out immediately after I posted a message about it. I can't believe I didn't figure that out BEFORE I posted this! How embarrassing! But I hope I can share this experience so that someone else out there may learn from it!

:-D

---

