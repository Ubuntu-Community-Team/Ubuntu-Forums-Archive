---
title: "Cups + Brother prints in reverse order"
date: 2006-06-14
forum: General Help
---

### Post by Mr.Mechano on 2006-06-14
Hi there!

I've dist-upgraded from 5.10 Breezy to 6.06 Dapper and my multifunction Brother MFC-425CN now prints in reverse order and without upper margin.

I've clean reinstalled from an Alternate Dapper 6.06 CD and reinstalled the printer driver following Brother website instructions.
Now the upper margin if ok, but the printer continues to print in reverse order from last to first page.

Has anyone had similar problem with Brother or other printers and the new cups 1.2?

--
Mr. Mechano
(move your mind)

---

### Post by Mr.Mechano on 2006-06-19
[QUOTE=Mr.Mechano]Hi there!

I've dist-upgraded from 5.10 Breezy to 6.06 Dapper and my multifunction Brother MFC-425CN now prints in reverse order and without upper margin.

I've clean reinstalled from an Alternate Dapper 6.06 CD and reinstalled the printer driver following Brother website instructions.
Now the upper margin if ok, but the printer continues to print in reverse order from last to first page.

Has anyone had similar problem with Brother or other printers and the new cups 1.2?

--
Mr. Mechano
(move your mind)[/QUOTE]


Ok here solution from Brother support (Japan).

--------------------
[HTML]Dear Sir/Madam,

We could make this issue happen at our side too.

The "reverse order print" you said is actually correct
due to its original specification of the CUPS.
The CUPS you had been using so far was not supporting it.


If you want to change it, please do the following.

1.Open the file MFC210C.ppd which is located under the directory
"/etc/cups/ppd/".

2.Delete the line "*DefaultOutputOrder: Reverse".


Best regards,
Brother Solutions Center
[/HTML]

---

