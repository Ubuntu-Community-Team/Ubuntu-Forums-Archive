---
title: "I upgaded to ubuntu 10.4, no wireless internet now"
date: 2011-03-14
forum: General Help
---

### Post by kevinwmiller on 2011-03-14
I recently installed ubuntu 10.4LTS, I have no wireless internet.

I have a Toshiba Protege R705

No idea whats up, everything else works fine.

---

### Post by kevinwmiller on 2011-03-14
Ok, I found my card.  My card is an intel 82577LC Gigabit network connection.

I found a website that lets me download the driver, but I dont know how to install it without using the package manager.

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3244&DwnldID=15817&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%c2%ae+82577+Gigabit+Ethernet+PHYeng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProdId=3244&DwnldID=15817&ProductFamily=Ethernet+Components&ProductLine=Ethernet+Controllers&ProductProduct=Intel%c2%ae+82577+Gigabit+Ethernet+PHYeng)

Is the location of the driver.  Im at a loss

---

### Post by kittkatt on 2011-03-14
Try popping in a LiveDVD of 10.10 to see if driver support for your card has been added to the kernel yet

---

### Post by highspider on 2011-03-14
when you've downloaded the file Right click it and extract it.
   There should be a read me file in it  aka README or INSTALL

 The norm is a configure file 
should be something like this  BUT READ THE INSTRUCTIONS FIRST

```

./configure
make
sudo make install

```

---

