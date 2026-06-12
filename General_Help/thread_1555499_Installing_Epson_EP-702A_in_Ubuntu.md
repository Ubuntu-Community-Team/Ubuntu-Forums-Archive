---
title: "Installing Epson EP-702A in Ubuntu"
date: 2010-08-18
forum: General Help
---

### Post by zaphod777 on 2010-08-18
Hello everyone,
I have an Epson EP-702A printer / Scanner all in one printer. I have actually had it for a while but could never get it working in Linux. Well today I had some extra time on my hands and finally got it working. I am posting my results to help out everyone else with this printer.

I am living in Japan so this is a Japanese model so a lot of users probably won't have this problem but it seams to be a general problem to Epson scanners and printers that don't work out of the box.

You can download all of the deb files to get this to work from here:
[http://avasys.jp/eng/linux_driver/](http://avasys.jp/eng/linux_driver/)

to get the Printer to work I had to install "epson-inkjet-printer-ep-702a_1.0.0-1lsb3.2_amd64.deb"

To get the scanner working I had to install 
1. first "iscan-data_1.0.1-1_all.deb" that contains some proprietary bits.

2. Then install the "Image Scan!" program from "iscan_2.25.0-1.ltdl7_amd64.deb"

even if your scanner isn't listed just pick a model they all point to the same software.

After that you can use "Sane" or the Epson "Image Scan" software to scan.

There you go! If you can't find the deb files let me know and I can email them to you.

---

### Post by m1y4b1 on 2011-03-17
Howdy!

I'm glad to see that someone was able to get their printer working! I have the same model, brand new, and am having a bit of trouble. I am running Ubuntu 10.10 and installed the file "epson-inkjet-printer-ep-702a_1.0.0-1lsb3.2_amd64.deb", however it is only spitting out white pages until the paper holder is empty. The self test runs fine and copies fine, so I know that ink is not the issue. It only does this action when I try to print from my computer, so I know that the computer and printer are communicating. 

Also, where would I find the other files that you listed to enable scanning? I've looked all over the site and must be missing them. Thank you in advance for your reply.

William

---

### Post by zaphod777 on 2011-03-17
> **m1y4b1 said:**
> Howdy!

I'm glad to see that someone was able to get their printer working! I have the same model, brand new, and am having a bit of trouble. I am running Ubuntu 10.10 and installed the file "epson-inkjet-printer-ep-702a_1.0.0-1lsb3.2_amd64.deb", however it is only spitting out white pages until the paper holder is empty. The self test runs fine and copies fine, so I know that ink is not the issue. It only does this action when I try to print from my computer, so I know that the computer and printer are communicating. 

Also, where would I find the other files that you listed to enable scanning? I've looked all over the site and must be missing them. Thank you in advance for your reply.

William
I'm not sure which packages you installed but I would install the ones I have here that work perfectly on my system:
[https://docs.google.com/leaf?id=0B4z-U6zSyuryZDdjMmQxMjMtZmQxNy00MzE3LTgyMWEtYzg4YTlhNGU3N2Fm&hl=en](https://docs.google.com/leaf?id=0B4z-U6zSyuryZDdjMmQxMjMtZmQxNy00MzE3LTgyMWEtYzg4YTlhNGU3N2Fm&hl=en)

I have both the x64 and x32 versions so use which ever one you need.

---

### Post by zaphod777 on 2011-03-17
I just realized I didn't put the files in the shared folder :( 
I just put them there so the link should work now.

---

### Post by zaphod777 on 2011-03-17
Also I would delete the printer from your machine and then connect it and see if it will auto detect it. I am also on x64 10.10

If it doesn't auto detect it you can manually select the epson driver from the list once you have installed the deb file.

---

### Post by m1y4b1 on 2011-03-17
Thank you for your suggestion concerning deletion of the initial files. For some reason my computer doesn't autodetect the Epson, but I just deleted everything and started at step one. Now it works perfectly! Thank you also for the links to the other files. My next step is making the scanner work :-)

---

### Post by zaphod777 on 2011-03-17
> **m1y4b1 said:**
> Thank you for your suggestion concerning deletion of the initial files. For some reason my computer doesn't autodetect the Epson, but I just deleted everything and started at step one. Now it works perfectly! Thank you also for the links to the other files. My next step is making the scanner work :-)

no problem :D as long as you install the scanner files in the right order then it should work fine. After that you can use either the Epson scanning utility or the built in Ubuntu one. I thought it would be such a headache getting the printer and scanner working but after having the correct files it was surprisingly easy.

---

### Post by m1y4b1 on 2011-03-17
I used the files in the link you provided and now my scanner works great! Thanks again for all your help. This was my first time using Ubuntu Forums and you made it a nice experience.

---

### Post by zaphod777 on 2011-03-17
> **m1y4b1 said:**
> I used the files in the link you provided and now my scanner works great! Thanks again for all your help. This was my first time using Ubuntu Forums and you made it a nice experience.


No problem everyone here is usually pretty helpful. If you have other issues you can create a post and if no one responds send me a PM and I will take a look at it. I can't promise I can fix it but I will take a look.

---

