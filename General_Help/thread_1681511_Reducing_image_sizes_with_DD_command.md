---
title: "Reducing image sizes with DD command?"
date: 2011-02-04
forum: General Help
---

### Post by gb210461 on 2011-02-04
Hi Guys
 
I have an image file that is 4009754624 bytes or 4.009'ish Gb in size. This image was created by using the DD command and copying bit for bit from a notional 4Gb USB key.
 
I have another USB key which is 4001366016 bytes or 4.001'ish Gb in size which I want to get the saved image onto.
 
So the original image is slightly but significantly a bit larger than the new destination USB key.
 
The original image was created from a USB drive that has two partitions. The first partition is the boot partition and the second partition is encrypted. This encrypted partition was created at install of Ubuntu 10:10 by using the Advanced Installation. It shows up as Entended, Encrypted and LVM2 Physical Volumn whne viewed from the Ubuntu Disk Utility application.
 
The problem I seem to be having is that no two 4Gb USB keys are the same size to the last byte as varying amounts of space seem to be being taken up by their respective firmware.
 
Is this the best place to locate this post or can someone suggest where else would be more appropriate? 
 
So can it be done? 
 
If not any other ideas?
 
Regards, Gary

---

### Post by tredegar on 2011-02-04
Yes, you can compress it.

In the gui, R-click the image file, Compress, choose your compression method, Compress.

---

