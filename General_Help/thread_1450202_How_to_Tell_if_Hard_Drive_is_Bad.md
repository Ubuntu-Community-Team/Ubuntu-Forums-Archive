---
title: "How to Tell if Hard Drive is Bad"
date: 2010-04-08
forum: General Help
---

### Post by bobkatevan on 2010-04-08
How can I tell if my Hard Drive is going bad. 

I had Windows installed and It never workede properly, sometimes taking up to 5 tries to boot, after installing 9.04 instead it worked alright but still had occasional errors. Now I upgraded to 9.10 and It takes 10 minutes after GRUB loads for the splash screen to load.

i recently defragged it using windows before I installed 9.04.

I think it might be the hard drive...

I'm using a Western Digital 160gb 7200 RPM 8mb buffer SATA hard drive

from what I know its around 5 years old. 

The mother board is made by biostar and may have been overclocked before we bought it.

if anyone could help it would be great, I'm thinkig of buying a new one soon

Thanks.

---

### Post by bhencetotozo on 2010-04-08
> **bobkatevan said:**
> How can I tell if my Hard Drive is going bad. 

I had Windows installed and It never workede properly, sometimes taking up to 5 tries to boot, after installing 9.04 instead it worked alright but still had occasional errors. Now I upgraded to 9.10 and It takes 10 minutes after GRUB loads for the splash screen to load.

i recently defragged it using windows before I installed 9.04.

I think it might be the hard drive...

I'm using a Western Digital 160gb 7200 RPM 8mb buffer SATA hard drive

from what I know its around 5 years old. 

The mother board is made by biostar and may have been overclocked before we bought it.

if anyone could help it would be great, I'm thinkig of buying a new one soon

Thanks.


Hello. This software boonie is to benchmark your harddrive.

1)sudo apt-get install bonnie++
2)bonnie++

if you search on google it will make it easy to understand it's result.

---

### Post by tgalati4 on 2010-04-08
sudo apt-get install smartmontools

sudo smartctl -a /dev/sda

Post the output:

---

### Post by aklo on 2010-04-09
If ubuntu

Administration->disk utility 
there is a SMART tools there...it will show you amount of bad sectors and temperator those sort of things.

If there is only 1 or none bad sector, your hard disk is still fine..if there are many then you have a problem

Of course bad sector doesn't mean a bad hard disk but at least this is the 1 thing i know how to check...

---

