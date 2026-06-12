---
title: "Printer resolution change has no effect since upgrade to 9.10"
date: 2010-01-10
forum: General Help
---

### Post by john.quinn on 2010-01-10
I have a Canon BJC-250. Since upgrading from 9.04 to 9.10, my print resolution got very bad. When I try to adjust to the best resolution (720 X 300), there is no difference. It is almost unreadable.
I'm stumped. I know I have an ancient printer, but it was working OK in 9.04...

---

### Post by dcstar on 2010-01-10
> **john.quinn said:**
> I have a Canon BJC-250. Since upgrading from 9.04 to 9.10, my print resolution got very bad. When I try to adjust to the best resolution (720 X 300), there is no difference. It is almost unreadable.
I'm stumped. I know I have an ancient printer, but it was working OK in 9.04...

Version upgrades are always problematical compared to fresh installs, try deleting the printer and letting it auto-detect and install again.

---

### Post by john.quinn on 2010-01-11
> **dcstar said:**
> Version upgrades are always problematical compared to fresh installs, try deleting the printer and letting it auto-detect and install again.
Thanks, David. I had tried deleting and reinstalling earlier, and I tried it once again after reading your response. However, I see no change in behavior. Adjusting the print resolution still seems to have no effect.

---

### Post by john.quinn on 2010-01-17
**Solution**

I had to switch drivers. 

_From:_ 
CUPS+GutenPrint v5.2.4 
[U]
To:[/U]
Canon BJC-250 Foomatic/bjc600

It's weird because everything I researched on the web said to use the GutenPrint driver. Oh well. There is one weird behavior - cancelling a print job does not form feed - the partially printed page just sits in the printer. I can get around this by pushing the "Resume" button on the printer.

---

