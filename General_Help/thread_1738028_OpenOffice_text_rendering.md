---
title: "OpenOffice text rendering"
date: 2011-04-24
forum: General Help
---

### Post by allywilson on 2011-04-24
Hi all,
       This is perhaps the wrong forum for posting this question, apologies if it is.

My OpenOffice installation has a weird problem. Random words appear to be rendering incorrectly within the GUI itself. However, it isn't limited just to the GUI, but will do the same to words in documents as well.

Info...
Maverick 10.10
Dual-core PentiumD
Nvidia GeForce 6200 (driver: 260.19.06)
RAM: 3GB

See attached for an example...

Anyone seen this before?

---

### Post by r-senior on 2011-04-24
> **allywilson said:**
> My OpenOffice installation has a weird problem. Random words appear to be rendering incorrectly within the GUI itself. However, it isn't limited just to the GUI, but will do the same to words in documents as well.
I used to get that on 10.10. There's an anti-aliasing setting that you can turn off in the preferences. Unfortunately I can't remember the exact option - something like "screen font anti-aliasing". The fonts end up looking poor, but it gets rid of those graphics errors.

The problem goes away on 11.04 with LibreOffice.

---

### Post by allywilson on 2011-04-24
I've just installed LibreOffice and it's the same...

EDIT: I'll try to find the anti-aliasing option (I tried disabling Java as well).

---

### Post by r-senior on 2011-04-24
> **allywilson said:**
> I've just installed LibreOffice and it's the same...
Interesting. That could suggest that it's the Nvidia drivers, rather than OpenOffice itself, which is what I had always assumed.

---

### Post by cipherboy_loc on 2011-04-24
Did you recently update to the 260.x drivers? Try reverting back to the 179.x driver series. 


Cipherboy

---

### Post by allywilson on 2011-04-24
Thanks, I'll try reverting the driver (the issue has always been there since I clean installed a few months ago), if it was the issue I'll let you know.

Ally

---

### Post by allywilson on 2011-04-25
It's fixed, thank you very much guys.

I upgraded to Natty last night, then I had the compiz white window issue on all windows, so I reverted to nvidia's 173 drive. 

I no longer have the white window issue nor the strange text rendering issues in openoffice/libreoffice.

Thanks again :-)

Ally

---

