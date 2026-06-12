---
title: "CUPS japanese text printing problem"
date: 2010-04-22
forum: General Help
---

### Post by innomotive on 2010-04-22
Hello.

Hello. I am facing a peculiar issue when printing Japanese text through CUPS (though I am not sure if this is the right forum).

I developed a Java application (that uses a graphical object to print to a PrinterJob class) that prints text (of Japanese characters) to a printer.

When I login in en_US/en_UK locale, the Japanese characters get printed from my Java app just fine. However, when I login in ja_JP and give a print job through my Java app, no Japanese text is printed at all. I get characters from only within the ASCII subset printed instead.

Any suggestions on how I can get the text printed properly?

I am using Serif and Courier New fonts in my app. Relevant details are:

In ja_JP,
a@a:/usr/share/cups/charsets$ fc-match serif:lang=ja
ttf-japanese-mincho.ttf: "Sazanami Mincho" "Regular"
a@a:/usr/share/cups/charsets$ fc-match sans serif:lang=ja
ttf-japanese-gothic.ttf: "VL Gothic" "regular"
a@a:/usr/share/cups/charsets$ fc-match courier new:lang=ja
n022003l.pfb: "Nimbus Mono L" "Regular"

Setup:
Operating System: Ubuntu 9.04
$LANG = ja_JP.UTF-8

Printer is a "Generic PostScript text-only printer"

---

### Post by innomotive on 2010-04-22
Not exactly solved...but workaround using jasperreports. Better that way anyway...

---

