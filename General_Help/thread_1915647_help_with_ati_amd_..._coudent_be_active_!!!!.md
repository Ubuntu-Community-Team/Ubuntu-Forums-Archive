---
title: "help with ati amd ... coudent be active !!!!"
date: 2012-01-26
forum: General Help
---

### Post by xaide12 on 2012-01-26
problem !!!!! 
 hello everyone ubuntu users ....... 
 i cant active (ATI/ ADM proprietary FGRX graphics dirver 
 +
 ATI/ ADM proprietary FGRX graphics dirver post released updates ) 
 after i restart ....... it ask me to active it again )....

---

### Post by dcstar on 2012-01-27
> **xaide12 said:**
> problem !!!!! 
 hello everyone ubuntu users ....... 
 i cant active (ATI/ ADM proprietary FGRX graphics dirver 
 +
 ATI/ ADM proprietary FGRX graphics dirver post released updates ) 
 after i restart ....... it ask me to active it again )....

Try this:

[http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem](http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem)

---

### Post by xaide12 on 2012-01-31
the system get crashed ...then i desinstall and install it again and again and again .......... after i try to fix the driver ... i tried it 9 times now ... with all the different ways  ..... you can see what i get when i restart the pc ... 
by the way ... i have hp dv6 with intel hd and ati mobility radeon hd 3670... i can switch between them easly with win7 .... ubuntu dont detect any one of them !!!!

---

### Post by Mark Phelps on 2012-01-31
> **xaide12 said:**
> i have hp dv6 with intel hd and ati mobility radeon hd 3670... i can switch between them easly with win7 .... ubuntu dont detect any one of them !!!!

That's because Switchable Graphics is an MS Windows feature.

It generally does not work very well in Linux:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by xaide12 on 2012-01-31
i am not a programmer and not a devloper .... i am just a user ... lets say little bit smart user .... just started usuing ubuntu the last week ... :)
Logically .... the system have to detect the hardwares ... then install the drivers .. then maybe switch between them 
how can i switch between 2 hardwares unknown to the system .... !!!! 
what i am looking for is installing the drivers ....

---

### Post by sunfromhere on 2012-02-01
Google told me that hp dv6 with switchable graphics has the same issues as mine (pavilion g7). HP really effed up, advertising one graphics, while not giving people the option to use GPU they want.

Here's the thing: HP says that the switchable graphics works automatically in Windows (don't have them, can't verify). You cannot select it manually with the BIOS version your laptop shipped with. They did produce a BIOS upgrade which gives you the option to manually select GPU in use, but most likely you will have to do this with Windows too.

Go to the hp site, and find the exact model of your laptop, f.e. this is [mine]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02884779&tmp_task=prodinfoCategory&cc=us&dlc=en&lc=en&product=5141935"). On the right you will see Support for this product -> Software and Driver Downloads, select language & OS (if you can select anything else but Windows) and then check if there are BIOS upgrades listed.

Probably they will offer you an .exe download, so in order to upgrade, you need Windows. After that you can select the wanted GPU in BIOS, and download the right drivers.

What I suggest - call HP. I called them. Ask in a polite manner why the BIOS upgrade is available only trough Windows. I'm hoping if they get enough calls they just might rethink it. Probably not, but hey, it's a 0800 number.

---

### Post by mastablasta on 2012-02-01
> **xaide12 said:**
> Logically .... the system have to detect the hardwares ... then install the drivers .. then maybe switch between them 
how can i switch between 2 hardwares unknown to the system .... !!!! 
....
 
 
that's not how linux works as Linux is not Windows.
 
Linux kernel on boot checks what you have and loads drivers for it. some coponents require proprietary drivers for better support (e.g. hardware graphics acceleration). In your case linux clearly found the intel cart and used the drivers it has built in for it. you now want to install them for ATI but as others have mentioned this gpu switching is not supported well under linux. there are some projects that started just recently to address this issue, but it will take time. 
 
the problem is with manufacturers that didn't provide linux drivers for graphics switching. 
 
logically if one wanted to run linux one owuld buy linux supported hadrware. with windows supported hardware it's best to run windows (often though linux will also work on same hardware).

---

### Post by sunfromhere on 2012-02-01
> **mastablasta said:**
> 
logically if one wanted to run linux one owuld buy linux supported hadrware. with windows supported hardware it's best to run windows (often though linux will also work on same hardware).

I can't say about dv6, but my pavilion g7 wasn't advertised as having switchable graphics. Take a look at the product specifications I linked in previous post (official hp product site). Under graphics it states Radeon HD 6470M and only that card. Could we say that HP is misleading it's customers?

---

### Post by mastablasta on 2012-02-01
yes in that case it was misleading the cusotmers (Edit: actually not propperly informed the customers of the second GPU). However, the intel GPU is part of the intel processor isn't it? G7 in my country uses this CPU: [http://ark.intel.com/products/55627/Intel-Pentium-Processor-B950-(2M-Cache-2_10-GHz](http://ark.intel.com/products/55627/Intel-Pentium-Processor-B950-(2M-Cache-2_10-GHz))
 
Graphics Specifications 
Integrated Graphics Yes 
Graphics Base Frequency 650 MHz 
Graphics Max Dynamic Frequency 1.1 GHz 
Graphics Output eDP/DP/HDMI/SDVO/CRT 
Intel® Quick Sync Video No 
Intel® InTru&#8482; 3D Technology No 
Intel® Insider&#8482; No 
Intel® Wireless Display No 
Intel® Flexible Display Interface (Intel® FDI) Yes 
Intel® Clear Video HD Technology No 
Dual Display Capable Yes 
Macrovision* License Required No 
 
to bad though... i had my eye on this one (not that i have the money for it at the momnet9. but looks lika a nice maschine at descent price (the g7).

---

### Post by sunfromhere on 2012-02-01
> **mastablasta said:**
> yes in that case it was misleading the cusotmers (Edit: actually not propperly informed the customers of the second GPU). However, the intel GPU is part of the intel processor isn't it? G7 in my country uses this CPU: [http://ark.intel.com/products/55627/Intel-Pentium-Processor-B950-(2M-Cache-2_10-GHz]("http://ark.intel.com/products/55627/Intel-Pentium-Processor-B950-%282M-Cache-2_10-GHz"))
 


This is a presumption that the customer should know the parts of a processor. :D

Still, I'm satisfied with the laptop. I will do the BIOS upgrade in the next couple of days, so I can manually change the GPU. Then it's game testing time!

---

### Post by xaide12 on 2012-02-01
honestely i find it a good misleading ...... anyone wants to have 2 gpu in stand of 1 .....:D
this is the message i get it says (it is recommended to close all applications. the system is about to change the graphics processor to optimize the lifetime of battery against performance. it is normal that your screen flickers or goes out for a few seconds when a change of processor is being )

and is this the laptop i have ( [dv6]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02679011&tmp_task=prodinfoCategory&cc=fr&dlc=fr&lang=fr&lc=fr&product=5050897") ) ...

some  missunderstand me ..... so this is what i want 
the ubuntu ..... didnt know any one of the grafique cards .. no intel hd and no ati .

i tried all what i found here ... 
[http://askubuntu.com/questions/78906...ve-the-problem]("http://askubuntu.com/questions/78906/ati-amd-proprietary-fglrx-graphics-install-fails-how-can-i-resolve-the-problem")

then the system crash .. any solutions pls... to fix at least one of the cards  ????

---

