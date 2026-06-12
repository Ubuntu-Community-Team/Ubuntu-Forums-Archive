---
title: "Installing TV Tuner Drivers from Zip file with Xubuntu"
date: 2011-08-13
forum: General Help
---

### Post by glowboy70 on 2011-08-13
Hello,

I'm quite the rookie using 'Xubuntu' on my older Acer Laptop and recently got a USB AVerTV H826 Hybrid Volar Max tuner so I could hopefully watch some broadcast television using the Kaffeine program.

Well, for the first time ever I had to actually go to the company website and download a driver so my device would work. Normally my devices were automatically installed.



I got the 32bit driver from the AVerMedia website and extracted the .zip file to my Desktop for easy access.

I renamed the extracted folder to TV to lessen what I'm assuming I will have to type in the Terminal command prompt.

*** Inside the extracted folder "TV" is a file named -   AVERMEDIA-Linux-x86-H826D-0.10-beta.sh


After several attempts and hours of trying to install this television tuner I've decided to accept defeat and pick the minds of the wise.

So keeping in mind that I'm not all too savvy with Xubuntu or Linux in general please be as specific as possible with what I need to type in Terminal to install the mentioned .sh driver onto my pc.

Once again the .zip is extracted on the 'Desktop' and I renamed the folder TV

And the file inside is called AVERMEDIA-Linux-x86-H826D-0.10-beta.sh


Thanks!

Dan -

---

### Post by oldos2er on 2011-08-13
Open terminal, run ```
cd Desktop

chmod +x AVERMEDIA-Linux-x86-H826D-0.10-beta.sh

./AVERMEDIA-Linux-x86-H826D-0.10-beta.sh
```

Depending on the script, you may need to use 'sudo' with the last command ```
sudo ./AVERMEDIA-Linux-x86-H826D-0.10-beta.sh
```

---

### Post by glowboy70 on 2011-08-14
Thank you for the prompt reply oldos2er!

There's some good and bad news.

The good news is I now have a pretty good understanding of how to install .zip drivers for devices on my PC.

The bad news is due to an Error message during an installation attempt of the driver it would appear that the software that the manufacturer provides for my TV Tuner doesn't seem to support the current kernal version of Xubuntu and I'm afraid it never will.  



Taken from the manufacturer website here is the list of supported versions:

[Quote] 

The following distributions, with their stock kernel, are officially  tested and supported: 
     1. Open SuSE Linux 10.3 
    2. Mandriva Linux 2008 
3. Fedora Core Release 6     
4. Fedora Core Release 7     
5. Ubuntu 7.10
6. Ubuntu 8.10     
7. Ubuntu 9.04     
8. Ubuntu 9.10     
9. Mandriva Linux 2009
[End Quote]

I thought for sure it wouldn't make a difference what Kernal version I was using, but it seems I was mistaken.



So once again thanks for your help and now next time when I'm confronted with a .zip file I'm pretty confident I can make a much better attempt to install it. :P


Regards,

Dan -

---

### Post by oldos2er on 2011-08-14
Before you installed the drivers, did you check to see if the tv tuner worked at all? You can run **lsusb** to see if the system recognizes it.

I checked [http://linuxtv.org/wiki/index.php/AVerMedia](http://linuxtv.org/wiki/index.php/AVerMedia) and it looks like this particular tuner isn't supported.

---

### Post by glowboy70 on 2011-08-14
I did run the **lsusb** command in Terminal and do in fact see my TV Tuner listed as AVerMedia Technologies, Inc. 
 
I checked out the link you supplied and it looks like you are correct in the determination that my particular Tuner is not supported in Linux. Crapola! (x10)
 
 
I do know that the Tuner works in MS XP so I may be looking at a Dual Boot situation even though I was hoping to not rely on such an inferior OS to use my gadgets.
 
 
Like I said before though atleast I can say I did learn something with your truly appreciated assistance. I now know how to open/install .zip files which will prove to be of great value I am most certain.
 
 
Thanks Again! :)
 
dan -

---

