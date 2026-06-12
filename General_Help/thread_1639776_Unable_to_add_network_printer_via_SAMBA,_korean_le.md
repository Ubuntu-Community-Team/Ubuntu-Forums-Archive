---
title: "Unable to add network printer via SAMBA, korean letters"
date: 2010-12-07
forum: General Help
---

### Post by Senplanet on 2010-12-07
Hello,

I use ubuntu 10.10 in my Lab. I tried to add network printer from local network (windows). Unfortunately the workgroup is named by Korean letters and samba seems that cannot recognise this letters. Instead of Korean characters it shows only this kind of &#9508;ÙÔ&#9562;»µ&#9488;¼©¢Ã.... However I can find the printer in the list of SMB Browser, but when I choose the printer the final smb link looks like this: 

smb:// %E2%94%A4%C3%99%E2%5%9A%C2%%B5%EBC%E2%96%92%C2%A9%C2%A2%C3%83/PC1/HPLaserJ2035

So when I hit the bottom Forward it just stuck. 
I did not tried yet, but I guess the similar problem will be with the sharing folders between other computers on this workgroup.

How can I enable samba to recognise Korean letters in a network or is there something what I can do? (if I cannot change the workgroup name)

I really appreciate any of your suggestions

---

