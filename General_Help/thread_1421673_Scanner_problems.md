---
title: "Scanner problems"
date: 2010-03-04
forum: General Help
---

### Post by kerbyn on 2010-03-04
OK. So I've been using Ubuntu 9.10 'in anger' for a couple of weeks now and overall I'm impressed. However, a couple of days ago my old Epson C46 (which had been working fine under Karmic) died, and I had a look for a replacement.

I decided on a Canon MP270 because Canon seemed to have gone to the trouble of providing Linux drivers on their website. I even phoned Canon and they confirmed it should work fine.

Today the AIO arrived and I downloaded the printer and scanner drivers from Canon. I could't get the install.sh files to run - tried ./ sudo and sh etc, no joy. Anyway, I used the package manager to install the .deb files and that seemed to go OK.

The printing side of things works fine but I can't get the scanner recognized by Xsane.......

It's not the end of the world because I have a Lide 60 to fall back on but it's just annoying that what should work, doesn't....

Any ideas?

---

### Post by pricetech on 2010-03-04
I'd contact Canon again.  If they said it would work, then I'd hold them to it.

---

### Post by rnerwein on 2010-03-04
hi
have you tried: scanimage -L  to have a look if the scan device is recoginzed ?
man scanimage
ciao

---

### Post by kerbyn on 2010-03-04
scanimage -L doesn't find it either... :(

---

### Post by kerbyn on 2010-03-04
I've got a bit further with this...

I've got the install.sh file to run with this command:

sudo ./install.sh

but it gives me an error almost straight away which reads:-

"Error! Cannot specify package management system."

Anyone know what this means or how to get around it?

Thanks.

PS - I notice that the software was tested on 9.04. Is there a difference in the package management system between 9.04 and 9.10?

---

### Post by kerbyn on 2010-03-04
Mystery solved!

I must have installed the software correctly using the package manager in the first place. It just wasn't evident that I had. I just needed to create a launcher with the command line "scangearmp"... and bingo, I have Canon's GUI which enables scan to PDF among others.

Also, I can scan from within apps like Gimp (File, Create, Scangear MP).

Fantastic!! :p

---

