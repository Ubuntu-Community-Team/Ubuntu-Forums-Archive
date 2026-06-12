---
title: "Firefox icon missing after upgrade"
date: 2009-11-01
forum: General Help
---

### Post by Potters Son on 2009-11-01
Upgraded to Karmic this morning, but after the upgrade my Firefox icon appears to be missing. The .desktop files are still there in my panel and menu, but the icons themselves are missing. How can I fix it?

---

### Post by lovinglinux on 2009-11-01
Close Firefox, then go to "System >> Preferences >> Appearance >> Interface" and check "Show icons in menus".

---

### Post by Potters Son on 2009-11-01
No, that isn't my problem. I'm talking about the Firefox launcher - both the one in the Applications menu and in the panel. When I upgraded, the Firefox launcher's icon became a red DO NOT ENTER symbol on a gray background. The file that the launcher referenced to be the icon disappeared entirely, to my knowledge, or it was moved in the upgrade.

---

### Post by lovinglinux on 2009-11-01
> **Potters Son said:**
> No, that isn't my problem. I'm talking about the Firefox launcher - both the one in the Applications menu and in the panel. When I upgraded, the Firefox launcher's icon became a red DO NOT ENTER symbol on a gray background. The file that the launcher referenced to be the icon disappeared entirely, to my knowledge, or it was moved in the upgrade.

:oops: sorry. Did you edit the launchers before, for example to point to Shiretoko?

Anyway,  you could create a new launcher using **firefox %u** as command. If that doesn't work, then re-installing **firefox** and **firefox-3.5** packages should do the trick.

---

### Post by Potters Son on 2009-11-09
It's okay. I solved it by literally copying the icon from my friend's Firefox installation, and it's fine now. I can't believe that the firefox icon is just stored as a big png file. I'd've thought (and I think I just coined a contraction there) that it would have been an svg. Weird. So, all is well that ends well.

---

### Post by noobmike on 2009-11-10
> **Potters Son said:**
> It's okay. I solved it by literally copying the icon from my friend's Firefox installation, and it's fine now. I can't believe that the firefox icon is just stored as a big png file. I'd've thought (and I think I just coined a contraction there) that it would have been an svg. Weird. So, all is well that ends well.

So where exactly do you put the icon? In the .Mozzilla folder?
Also, does it need to be named a certain way?

---

### Post by poohman on 2009-11-19
Try right clicking on the icon, choose properties, where u can change the icon.

---

### Post by Potters Son on 2009-11-19
> **noobmike said:**
> So where exactly do you put the icon? In the .Mozzilla folder?
Also, does it need to be named a certain way?

The icon is (on my friend's, and therefore my, installation) at /usr/share/pixmaps/firefox-3.5.png

> **poohman said:**
> Try right clicking on the icon, choose properties, where u can change the icon.

Thanks, but the problem was that the icon simply wasn't on my filesystem. I did have to go through the properties to re-point the launcher to the new icon after I put it in /usr/share/pixmaps/, though. Thanks.

---

### Post by joho500 on 2009-11-20
Thanks, guys. Had the same problem. Found the Firefox icon in /usr/share/pixmaps.

Cheers,
Joost

---

### Post by gkinal on 2010-09-28
This is a recurring/consistent problem for me on EVERY upgrade of Firefox. WHY can't the launcher maintain (contain, link to, whatever) its icon ? 

It works on Firefox Windows, Firefox Mac upgrades. WHY NOT UBUNTU LINUX ?????


Should be a reported Firefox bug IMHO.
GVK

---

### Post by xiongnu on 2010-11-18
> **Potters Son said:**
> No, that isn't my problem. I'm talking about the Firefox launcher - both the one in the Applications menu and in the panel. When I upgraded, the Firefox launcher's icon became a red DO NOT ENTER symbol on a gray background. The file that the launcher referenced to be the icon disappeared entirely, to my knowledge, or it was moved in the upgrade.

i have the exact same problem after upgrading to ver 3.6.  can someone tell me where to find the icon?  it's not in /usr/share/pixmaps/ folder

---

