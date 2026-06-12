---
title: "BCM4312 on Ubuntu 9.10"
date: 2009-11-09
forum: General Help
---

### Post by howcanireachthesekids on 2009-11-09
This problem is really annoying me :(
Here is the situation

[LIST]
[*]I have installed Ubuntu 9.10 with Wubi and i use Windows 7 as well
[*]I have a [*_HP Pavilion dv6-1020el _*]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01667985&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&lang=en&product=3885212")
[*]It has a Broadcom BCM4312 card
[*]The card worked on Ubuntu 9.04 but on 9.10 just doesnt work by default :mad:
[*]The card works when using the Live CD
[*]Doesn't work when using the installed ubuntu OS
[*]I have no other means of internet access in using Ubuntu, but only via Wireless
[/LIST]
How to get this problem fixed ? anyone ?

I tried removing the dkms package, then reinstalled it, so then i could install the 
**[SIZE=3]bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb[/SIZE]**

I could get the above package installed successfully and then rebooted but still the card driver is not working :(
In the Hardware Drivers, it only shows the B43 STA driver, and when i click the activate button and insert my root password it will just not activate it ! :mad:

I am out of ideas, this problem has gotten me down :( I do not know what to do, so i thought anyone here would help me ! I be grateful a lot
thank you guys :)

---

### Post by pastalavista on 2009-11-09
I believe, for your card, you need to install the 'b43-fwcutter' firmware package. It should be in the repositories and can be added from Synaptic Package Manager. I think it's on the live CD so make sure you have the CD-rom checked as enabled in Software Sources and the CD in the drive. Does your HP not have an ethernet port?

---

### Post by NFblaze on 2009-11-09
Ok I just broke my **** again, and finally just fixed it again.. and man is that a pain in the ***. I've never used the b43cutter. It may work so give it a shot...but it always seemed complicated for me, but I think we have similar laptops.
 

Let me just tell you what I did.

I went to Hardware Drivers and clicked remove from the Hardware Drivers section it did so. Though my wireless was still working, oddly enough.

So then,I went to Synaptic and I removed the bcmwl-kernel-source 5.10.9.9.+bdcom_**0ubuntu4**. I left bcmwl-modaliases in there, (I was trying to do it step-by-step.)

I restarted and my Wi-fi was gone.

So then I installed bcmwl-kernel-source 5.10.9.9.+bdcom_**0ubuntu1** deb file which is the only thing I had laying around on an external media drive from Karmic Alphas-Beta.

I went back to Hardware Drivers and tried to install the drivers from there. It didnt work.

I restarted. 

I went back to Hardware drivers and tried to activate the drivers again. It still didnt work. I tried running it from the cmdline and all that jazz end in end jockey-gtk would either hang in an infinite loop of nothingness. So I did ALOT of restarts everytime I thought it was hanging, be aware of that.

Once I exhausted that it wasnt going to install that way. I started poking around back in Synaptic. 

I made sure my DKMS package was installed which is something that has something to do with restricted drivers, I dont know the specifics but I know it needs to be there. It was there.

The only thing I could think of was maybe if I download the same version of my bcmwl-modalias [B]ubuntu4
[/B] maybe if I reinstall the update version of  5.10.9.9.+bdcom_**0ubuntu4** from a .deb file.

SO I downloaded the updated version of 5.10.9.9.+bdcom_**0ubuntu4**. 

 I installed it from the .deb file. and I watched the output one thing I did notice was that after it read the package, it was updating my DKMS and it did an update-initramfs (which I really dont know what they are). 

Anyhow, I restarted. 

I went to Hardware Drivers and clicked activate. Lo and Behold, it activated. I dont think I restarted but maybe I did. Anyway it's working again.

I just tried to remove it again and it gave me an error so most likely I have to restart again and try to remove it later again to see if I can repeat this again.


There is going to be alto of restarts.

---

### Post by smsmith050 on 2009-11-09
I am using a Compaq 6715. 
The hardware drivers app would not activate my BCM4328.
I used synaptic to uninstall all bcmwl packages. 
I installed the bcmwl-kernel-source from the 9.10 CD deb package.
I installed the build-essentials from the CD.
I rebooted, ran the hardware drivers app and the STA wireless driver showed up as activated.

---

