---
title: "going to 64bit"
date: 2010-12-03
forum: General Help
---

### Post by winjeel on 2010-12-03
I have a regular Dell D520 with 32bit 10.04, and wondered if it's possible to start using the 64bit version of 10.10. Do I need any special architecture to run 64bit? Is there any advantage in a regular laptop running 64bit?

---

### Post by TBABill on 2010-12-03
Yes you can run 64 bit with the D520. Phoronix did a test on 32 bit, 32 bit with the PAE kernel and 64 bit (all Ubuntu) and 64 bit won in terms of speed in every category, sometimes by huge margins other times small. No problems I have encountered with 64.

---

### Post by Asmodai on 2010-12-03
> **TBABill said:**
> Yes you can run 64 bit with the D520. Phoronix did a test on 32 bit, 32 bit with the PAE kernel and 64 bit (all Ubuntu) and 64 bit won in terms of speed in every category, sometimes by huge margins other times small. No problems I have encountered with 64.
Are you sure? It seems that the D520 has a Core Duo T2500, which does not support 64-bit according to Wikipedia.
Even if it did: while the 64-bit version has a slight speed advantage, 64-bit programs use more memory. Since the D520 has only 1 GB RAM, it would be a bad idea.

---

### Post by winjeel on 2010-12-03
Thanks.  :) I updated my ram to 4Gb, not knowing that Windows XP and 10.04 (32bit) only used 2.9Gb. I do a lot of photography, so I need the ram to handle large files.

---

### Post by NightwishFan on 2010-12-03
If you are sure your hardware is capable and you have a lot of cpu heavy workloads (video encoding, editing) then you may see an advantage using 64-bit even with 1gb ram. Though the simple answer is 32-bit is supported and there is not much noticeable difference. I say save using 64-bit perhaps if you get a new machine.

Edit: Install the pae kernel to use all of your ram.
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by efflandt on 2010-12-03
If you try booting 64-bit CD or USB iso on a computer that is not capable, the boot will stop right there with an error that you are trying to install 64-bit on an i686, and go no further.  So all it would cost you to try it would be about 20 cents for a CD or the time it takes for Startup Disk Creator to write to USB flash.

But if it is a T2500, even Intel says it only does 32-bit [http://ark.intel.com/Product.aspx?id=27236](http://ark.intel.com/Product.aspx?id=27236)

---

### Post by winjeel on 2010-12-04
> **NightwishFan said:**
> If you are sure your hardware is capable and you have a lot of cpu heavy workloads (video encoding, editing) then you may see an advantage using 64-bit even with 1gb ram. Though the simple answer is 32-bit is supported and there is not much noticeable difference. I say save using 64-bit perhaps if you get a new machine.

Edit: Install the pae kernel to use all of your ram.
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I tried this, and my system still tells me that I've only got 2.9Gb available (I have installed two 2Gb cards).

> **efflandt said:**
> If you try booting 64-bit CD or USB iso on a  computer that is not capable, the boot will stop right there with an  error that you are trying to install 64-bit on an i686, and go no  further.  So all it would cost you to try it would be about 20 cents for  a CD or the time it takes for Startup Disk Creator to write to USB  flash.

But if it is a T2500, even Intel says it only does 32-bit [http://ark.intel.com/Product.aspx?id=27236](http://ark.intel.com/Product.aspx?id=27236)


Thanks for the idea.

---

### Post by dcstar on 2010-12-04
> **winjeel said:**
> I tried this, and my system still tells me that I've only got 2.9Gb available (I have installed two 2Gb cards).


If the hardware only is designed for 4GB maximum RAM (and it doesn't matter if it 32 or 64 bit) then **all** the addresses of the other resources will have to be below 4GB and this will reduce the available RAM accordingly if you have the maximum installed.

Changing to 64 bit may only get a marginal increase in available RAM in this case, so a BIOS upgrade and/or changing some BIOS settings may be the only way to squeeze a bit move available RAM out of the device.

---

### Post by winjeel on 2010-12-04
Thanks

---

