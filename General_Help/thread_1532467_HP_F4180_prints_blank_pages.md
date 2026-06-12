---
title: "HP F4180 prints blank pages"
date: 2010-07-16
forum: General Help
---

### Post by jackn on 2010-07-16
My HP F4180 only prints blank pages.
It can, however, print out a test page, so there's no issue with the ink or hardware, it seems.
Also, it used to print properly in the past.

I've run hp-check, but the program ends up with no warnings or findings.
Likewise, the HP appelet ends every print job with a 'completed' status, seeming to think all's well.

The only remote clue I've found so far: HP's troubleshooting tool noticed that the page format is 'letter' (small 'l') according to the printer settings in System>Printing, but 'Letter' (capital 'L') according to the Open Office printer properties dialogue box launched when trying to print.
The troubleshooter referred to this discrepancy as a possible 'alignment' issue.
Could this possibly account for the failure to print?
If so, how could the two page size descriptions be made identical (they come from drop down menus which I don't know how to access)?

Any other leads?
Thank you.

---

### Post by jackn on 2010-07-17
Bump.

---

### Post by AlphaLexman on 2010-07-17
Point your web browser to:
> [http://localhost:631/](http://localhost:631/)
If you are using CUPS (the default ubuntu printing service)...
Click on the Printers or Administration tabs and see if your printer is there.

---

### Post by jackn on 2010-07-17
Yes, my printer is listed in there.

I wasn't aware of the wealth of information and this east interface.
Thank you, AlexLexman.

It's pretty troubling: a sound printer which goes through the motions of printing, but which puts out only blank pages...

What can be done?

---

### Post by jackn on 2010-07-18
Bump.

---

### Post by AlphaLexman on 2010-07-18
I'm back.

Let's start with,

What are you trying to print?

[LIST]
[*]a text file
[*]a pdf file
[*]an OOo file
[*]a picture?
[/LIST]
Knowing this will help me find a solution...
Can you print to a file? a pdf? etc?

---

### Post by jackn on 2010-07-18
OK, issue solved...

While I was thinking there was some deep mystery here, it turns out to have been a color, instead of black and white, setting.
In the print dialogue box: properties > device > print quality should be set to 'normal grayscale' instead of 'normal color'.

I'm sorry for this oversight...
I've been without a printer for months now... I'm blushing properly.

Alphalexman, I'm sure that the attention and advice you gave me were helpful in my keeping up with the issue and by making me tweak around and play with various leads. Warm thanks.

---

