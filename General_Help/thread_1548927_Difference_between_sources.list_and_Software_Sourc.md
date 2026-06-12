---
title: "Difference between sources.list and Software Sources information - normal?"
date: 2010-08-09
forum: General Help
---

### Post by zozza on 2010-08-09
Hello,

I downloaded Spideroak and installed it.  I notice when I look in my /etc/apt/sources.list file that Spideroak does not appear but in Software Sources / Other Sources it is listed. 

Is there a reason for this difference?  Is this normal?  I would have thought that whatever was listed in the GUI software sources should also be listed in sources.list?

Thanks.

---

### Post by deserthowler on 2010-08-09
there is a directory called sources.list.d that you might want to look at.

Earl

---

### Post by zozza on 2010-08-09
Thank you!!!

However, I am wondering why Spideroak does this?  Why not just put the update information in the /etc/apt/sources.list file?

  	 	 	 	 	 	  [FONT=arial, sans-serif]The code in /etc/apt/sources.list.d /spideroak.com.sources.list is:[/FONT]
[FONT=arial, sans-serif]
[/FONT]
[FONT=arial, sans-serif]deb [http://apt.spideroak.com/ubuntu-spideroak-hardy/](http://apt.spideroak.com/ubuntu-spideroak-hardy/) release restricted

[/FONT]

---

