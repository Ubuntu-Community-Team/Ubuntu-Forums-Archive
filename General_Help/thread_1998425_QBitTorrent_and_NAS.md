---
title: "QBitTorrent and NAS"
date: 2012-06-06
forum: General Help
---

### Post by Xtudent on 2012-06-06
Hi
I'm not very good at linux and I'm not very smart so try to explaine to me as if you speak to a five year old.

WHAT I TRIED TO DO
I have tried to get QBitTorrent to store both incomplete downloads and complete ones at my NAS (a Seagate GoFlex Home). This mainly do to the fact that it takes as much time to transfer it to my NAS after I completed a download as it took to download the file in the first place.

WHAT HAS HAPPEND
My first instinct was to simply copy search path by using the copy command and paste in to the correct field in QBitTorrent as follows:

"Save files to location:"
afp://USERNAME@GoFlexHome.local/USERNAME/GoFlex%20Home%20Public/Downloads/Complete
and
"Keep incomplete files in:"
afp://USERNAME@GoFlexHome.local/USERNAME/GoFlex%20Home%20Public/Downloads/Incomplete

This did just result in folders with the name ~/afp://USERNAME@GoFlexHome.local/... and so on was created. Not what I intended.

I then tried to figure out where the shares from the NAS was mounted. I got two alternatives AFP and SMB and I found the mountpoint for the AFP.

This resulted in the search path: /home/ACCOUNTNAME/.gvfs/AFP volume USERNAME for USERNAME on GoFlexHome/GoFlex Home Public/Downloads/Complete and the corresponding for Incomplete.

This worked fine for a short while. After wich it broke the link to the NAS and created a new folder in .gvfs with the same search path but had nothing to do with mounted NAS share.

MY SUSPISIONS
I think that if the mount gets broken QBitTorrent is unaware of the fact that it no longer is writting to the same location and instead creates the location at the specified path.

I guess that this can be avoided by altering the searchpath so that it includes both USERNAME and PASSWORD for the NAS share. But I guess this still requires that I make sure that it is mounted first. Something that tends to break as soon as I acces the NAS from another device.

I **** you not. If I so much as look at a videoclip or even browse the wrong folder from another unit Ubuntu goes bananas over both SMB and AFP shares on the NAS. All other units seem to handle it just fine but Ubuntu seems to have some sort of social fobia or something since it can't stand contact with other devices.

WHAT I WANT
Please tell me if there is a simplesollution to the problem. If it's to complecated I will not bother with it anyway.

---

