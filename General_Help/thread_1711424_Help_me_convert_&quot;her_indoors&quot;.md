---
title: "Help me convert &quot;her indoors&quot;"
date: 2011-03-21
forum: General Help
---

### Post by AmpersUK on 2011-03-21
I have almost persuaded my wife to move to Linux - I have been using it for a couple of years now.

The one thing holding her back is Avery Labels DesignPro5 which she uses for two charities she is involved in, for address lavels and doesn't want to type in hundreds of names and addresses all over again.

No, I am not asking you to type them in for her! ;-)

Is there any way I can get these addresses from the Avery database to gLabels? I note from gLabels I have a few options for importing.

However, I have been through the Avery software and there doesn't seem any exporting facilities.

Ideally I would like to get a CSV list.

Anyone got any ideas?

---

### Post by jdeslaur on 2011-03-21
You could try testing the label program with [wine]("http://www.winehq.org/download/deb")
or if you want to truly get wild...
Convert her windows machine (I'm assuming its windows) to a virtual machine and run virtualbox for when she needs specific windows programs.

---

### Post by AmpersUK on 2011-03-21
> **jdeslaur said:**
> You could try testing the label program with [wine]("http://www.winehq.org/download/deb")
or if you want to truly get wild...
Convert her windows machine (I'm assuming its windows) to a virtual machine and run virtualbox for when she needs specific windows programs.

Thanks, I must admit, WINE and Virtual Box had crossed my mind, but only as a last resort. I really would prefer to get shot of "anything Windows" completely.

Ampers

---

### Post by cipherboy_loc on 2011-03-21
Something slightly less wild is creating a virtual machine for her (using VirtualBox) and installing Windows and the programs that she need into it. Most Windows computer are full of bloat which makes VirtualBox slow.


Cipherboy

---

### Post by SeijiSensei on 2011-03-21
I looked at a manual for the Avery software.  It says that DesignPro stores addresses in dBase III .dbf files. OpenOffice Calc includes dBase among its supported import formats.  If you can find the .dbf file and open it in Calc, you can save it back out as .csv.

I've never used gLabels.  Maybe it can import .dbf itself?

---

### Post by pricetech on 2011-03-21
Open Office includes support for numerous Avery labels.  That might at least be a starting point.

> **AmpersUK said:**
> 
No, I am not asking you to type them in for her! ;-)


I was going to offer, but since you declined.  (just kidding)

---

