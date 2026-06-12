---
title: "RAID5 Array capacity?"
date: 2012-03-02
forum: General Help
---

### Post by Teh_Messiah on 2012-03-02
I have a file server running Xubuntu 10.10 64bit.
It has a Dell RAID card in it which has a raid array size limit of 2TB.
I have a [Silicon Image SIL3114]("http://www.siliconimage.com/PRODUCTS/product.aspx?id=28") 4 port raid card in my old server which I want to put into the new server.
It has the ability to make arrays up 131,072 TB.
It says on the documentation for the card that some linux OSes have a drive size limit for arrays of 2TBs.

I want to put 4 2TB sata drives on the card in a RAID5 array to make an effective 6TB array!

I'm doing this since my current 2x 2TB arrays in my new server are nearly full!

So what is the limit of Xubuntu for array drive size?
Will it accept a 6TB array?

---

### Post by Teh_Messiah on 2012-03-07
Anyone?
Someone?
I discovered that xubuntu doesn't recognise the array created by this sil3114 card!
I had to use mdadm.

---

