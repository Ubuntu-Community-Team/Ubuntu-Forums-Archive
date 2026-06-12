---
title: "trying to install dd-wrt on linksys router"
date: 2009-06-30
forum: General Help
---

### Post by mamamia88 on 2009-06-30
i am trying to install dd-wrt on my linksys wrt54g v8 using these instructions [http://www.dd-wrt.com/wiki/index.php/How_To_Flash_the_WRT54Gv8](http://www.dd-wrt.com/wiki/index.php/How_To_Flash_the_WRT54Gv8)

i had accessed my router and flashed that killer software and it said the longer i wait the better so i left it at rebooting router screen and took a shower.  when i came back i had a network interupted message and now the power light doesn't come on just the ehternet light.  i can no longer acess 192.168.1.1 please help me out here

---

### Post by t4thfavor on 2009-06-30
you have to tftp the rest of the firmware up there as in the last part of the tutorial I believe the killer just smokes the vxworks loader. Then you have to use the other app to load the redboot loader, and the actual firmware image. The network interruption is due to DHCP being off. Set a static IP, and run through the tutorial again.

FYI, your only at step 7

Why are you not on the DD forum? Seems a longshot that I would be trolling, and have some practical knowledge of firmware loading.

---

### Post by mamamia88 on 2009-06-30
i don't have an account over there and didn't look like there where many active members sorry

---

### Post by t4thfavor on 2009-06-30
Im not chewing you out, I just wondered why you were asking Ubuntu about DD. No problem, I'm always glad to help.

---

### Post by mamamia88 on 2009-06-30
thanks man i'm not quite sure how to set a static ip in ubuntu do i just edit wired connection and make one up?

---

### Post by t4thfavor on 2009-06-30
They told you which one to set in the tutorial, follow it to the T and make sure you get it right, or you will have a 60USD paperweight. 


I believe that to be step #1

Right click on you two little computers in the top right corner of your screen (NetworkManager) and click Edit Connections. Select the Wired tab, select the correct eth interface, select Edit, put in your password, Select IPv4 Tab, then in the dropdown list select Manual. From there plug in the supplied info from the dd tutorial, and continue.

---

### Post by mamamia88 on 2009-06-30
> **t4thfavor said:**
> They told you which one to set in the tutorial, follow it to the T and make sure you get it right, or you will have a 60USD paperweight. 


I believe that to be step #1

Right click on you two little computers in the top right corner of your screen (NetworkManager) and click Edit Connections. Select the Wired tab, select the correct eth interface, select Edit, put in your password, Select IPv4 Tab, then in the dropdown list select Manual. From there plug in the supplied info from the dd tutorial, and continue.

lol thats what i am doing.  and this router is already a paperweight i had sitting around just thought i'd  do this for fun i have all the numbers typed in correctly

---

