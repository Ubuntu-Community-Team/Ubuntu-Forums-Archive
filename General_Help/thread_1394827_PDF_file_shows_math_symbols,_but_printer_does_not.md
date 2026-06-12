---
title: "PDF file shows math symbols, but printer does not"
date: 2010-01-31
forum: General Help
---

### Post by karups on 2010-01-31
I have Ubuntu 9.10 installed and up to date.

I have an HP Laserjet 2200 connected via USB with 64MB of memory.  When I print page 2 of this document (for example)
[http://www.dspguide.com/CH6.PDF](http://www.dspguide.com/CH6.PDF)
the delta-symbol and minus-signs do not show up, although I see them in Adobe reader version 9.3.

I have tried several of the available drivers for the printer (including the "[recommended]" one) and none of them produce these symbols.

I'm guessing this is a font issue.  I don't know how to show you what font stuff I have installed.

I would appreciate any help in resolving this issue.

p.s.
Here is the printer command:
lpr -P HP_LaserJet_2200 -o Smoothing=PrinterDefault -o PageSize=Letter -o PageRegion=Letter -o InputSlot=Auto -o ManualFeed=False -o HPHalftone=PrinterDefault -o Resolution=600x1200dpi -o HPEconoMode=PrinterDefault -o Duplex=DuplexNoTumble -o HPOption_Tray3=False -o HPOption_Duplexer=True -o HPOption_PaperPolicy=PromptUser -o InstalledMemory=64MB

---

### Post by karups on 2010-02-03
bump

---

### Post by lyall on 2010-02-03
do you have the Greek fonts installed?
it would be a place to start

good luck and have fun learning

---

### Post by hawthornso23 on 2010-02-03
From looking at the font info in the file, the problem fonts are apparently included in the pdf as embedded subsets. This means all the font info for these symbols should be in the pdf already so you shouldn't need to have the font installed on your system. I can see the symbols when I display the file. As I don't have that font installed on my system, that confirms that at least some of the font info for these symbols is present.

I don't know the answer to your question. But it may not be a simple problem. It might be an issue with how the file was created or a bug specific to your model of printer. It is a pity my printer is currently out of action or I could check if it prints OK for me. In particular installing the font on your system is not guaranteed to help.

---

### Post by karups on 2010-02-04
> **lyall said:**
> do you have the Greek fonts installed?
it would be a place to start

good luck and have fun learning

I don't know -- how can I determine that?

---

