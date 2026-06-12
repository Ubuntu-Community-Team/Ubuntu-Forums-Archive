---
title: "Not able to use my Samsung MFC Network Printer"
date: 2012-05-01
forum: General Help
---

### Post by makol1995 on 2012-05-01
Hi all

Last weekend I installed the new Ubuntu 12.04. Everything went fine so fare except my Samsung printer: CLX-3185FN. This is a MFC network printer and scanner device.
The problem I have is as follow:
- Ubuntu does recognize the printer on my network. But in system settings --> printing my printer is marked with a red stop sign (see attachment).
- When I print a test page I get an ok message but the printer does never print anything.
- The Scanner is not recognized at all (see attachment).

Does anybody now how I can fix this?
Any help is appreciated

---

### Post by gordintoronto on 2012-05-01
I think the printer has been set up as being attached to your computer. (localhost)

When I set up my Brother network printer, I make sure the printer is on, I run Printers, I select add (+), I select Network Printer, I wait a few seconds for the printer to appear in the list, and I select it. After saying "OK" a few times, it works perfectly.

My printer is set up with a static IP address. I frequently play with new distros or versions, and this procedure always works.

---

### Post by amosek on 2012-05-02
Got exactly same problem with the same printer - everything was fine till I upgraded to 12.04 ..

The driver installs properly but the printer had red sign and there is no scanner

Anybody can help?

---

### Post by makol1995 on 2012-05-02
> **gordintoronto said:**
> I think the printer has been set up as being attached to your computer. (localhost)

When I set up my Brother network printer, I make sure the printer is on, I run Printers, I select add (+), I select Network Printer, I wait a few seconds for the printer to appear in the list, and I select it. After saying "OK" a few times, it works perfectly.

My printer is set up with a static IP address. I frequently play with new distros or versions, and this procedure always works.

Thanks for this input.
When I install my printer this way the printer works but not the scanner. Because this way Ubuntu uses the integrated printer diver which is shipped into Ubuntu.

But I taught the native driver from Samsung is the better chose. But I am not able to bring the printer with this driver to work.

---

### Post by amosek on 2012-05-03
Hi

Found a solution to get the printer working.
Just changed the protocol from ipp to ldp and it works OK.

Still no joy with the scanner .. xsane keep crashing with segmentation fault.

I'll keep trying.

---

### Post by amosek on 2012-05-12
This morning I managed to get my scanner working again.

Thats what I've done:

I edited /etc/sane.d/xerox_mfp.conf..

Located the line that describes my printer, commented out the usb xxxx yyyy line, and then added a line tcp a.b.c.d where a.b.c.d is the IP of the printer.

After this, xsane works like a charm!

---

### Post by scouser73 on 2012-05-12
> **makol1995 said:**
> Hi all

Last weekend I installed the new Ubuntu 12.04. Everything went fine so fare except my Samsung printer: CLX-3185FN. This is a MFC network printer and scanner device.
The problem I have is as follow:
- Ubuntu does recognize the printer on my network. But in system settings --> printing my printer is marked with a red stop sign (see attachment).
- When I print a test page I get an ok message but the printer does never print anything.
- The Scanner is not recognized at all (see attachment).

Does anybody now how I can fix this?
Any help is appreciated

Please follow the instructions set out here; [[COLOR="Red"]**Easy Linux Tips - Setting Up Samsung Printers**[/COLOR]]("https://sites.google.com/site/easylinuxtipsproject/samsungprinters")

I used the instructions to install my Samsung printer last week and it worked straight away.

---

