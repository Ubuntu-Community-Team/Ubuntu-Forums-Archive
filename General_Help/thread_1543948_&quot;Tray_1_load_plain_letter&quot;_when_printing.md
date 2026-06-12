---
title: "&quot;Tray 1 load plain letter&quot; when printing by OpenOffice Writer 3.2"
date: 2010-08-01
forum: General Help
---

### Post by snowboard975 on 2010-08-01
I use Ubuntu 10.04 and OpenOffice 3.2, and HP LaserJet 4100n.
The printer is filled with A4 papers because I use A4 papers when printing.
However, when I print a document whose page format is A4 in OpenOffice Writer 3.2, the printer outputs this error.

"Tray 1 load plain letter"

I checked the printer setting as A4 at the Ubuntu start button > System > Administration > Printing.
I also checked the page setting as A4 at OpenOffice Writer menu > Format > Page.
I also checked the paper size setting as A4 at OpenOffice Writer menu > File > Printer Settings > Properties.

However I don't have this problem in other programs such as Firefox or Adobe Reader when printing. 
This problem only occurs at OpenOffice and I cannot solve the problem although I intensely searched Google for answers.

Would you help me to solve this problem? 
Thank you in advance.

---

### Post by dcstar on 2010-08-02
> **snowboard975 said:**
> I use Ubuntu 10.04 and OpenOffice 3.2, and HP LaserJet 4100n.
The printer is filled with A4 papers because I use A4 papers when printing.
However, when I print a document whose page format is A4 in OpenOffice Writer 3.2, the printer outputs this error.

"Tray 1 load plain letter"

I checked the printer setting as A4 at the Ubuntu start button > System > Administration > Printing.
I also checked the page setting as A4 at OpenOffice Writer menu > Format > Page.
I also checked the paper size setting as A4 at OpenOffice Writer menu > File > Printer Settings > Properties.

However I don't have this problem in other programs such as Firefox or Adobe Reader when printing. 
This problem only occurs at OpenOffice and I cannot solve the problem although I intensely searched Google for answers.

Would you help me to solve this problem? 
Thank you in advance.

What is in /etc/papersize ?

---

### Post by snowboard975 on 2010-08-03
> **dcstar said:**
> What is in /etc/papersize ?

Ahh!! It was letter. I changed it to A4 and it solved the problem!!!
Thanks a million!!!

By the way, does that mean the paper setting in the OpenOffice is meaningless and it just follows the setting of /etc/papersize ?
Is this a a bug of OpenOffice or an intended function?

---

