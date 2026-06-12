---
title: "SystemError: installArchives() failed"
date: 2010-10-11
forum: General Help
---

### Post by binarylife on 2010-10-11
I can't install wireless drivers !! 
Broadcom B43 wireless driver
Broadcom STA wireless driver

error msg:
SystemError: installArchives() failed!! 
help please ?

I have HP550 notebook with Intel® Core&#8482; 2 Duo Processor T5470 (1.6 GHz, 800 MHz FSB, 2 MB L2 cache).

---

### Post by binarylife on 2010-10-11
no need for help! thanks to caffeinpill!! all my respect.

[QUOTE=caffeinepill;9240122]Even this didn't work for me (Ubuntu 10.04  64 bit), although I see many people have had success with this method!. I  was getting various errors when I attempted to install (and several  attempts to re-install) the bcmwl-kernel-source package manually via  synaptic.

Assuming you have attempted to install bcmwl-kernel-source and its  dependencies manually, received errors during its install and synaptic  is showing bcmwl-kernel-source as 'installed'... this may solve the  problem.

[SIZE=1]Go into synaptic and[/SIZE][SIZE=2][SIZE=1]...

[/SIZE]**completely remove bcmwl-kernel-source** **AND dkms**[/SIZE]

*then**, whilst still in synaptic ***[B][SIZE=2]

install bcmwl-kernel-source[/SIZE][/B]


For me this did the trick, I'm not sure why. (removing dkms was the  golden ticket). I then went back into Hardware Drivers and driver was  showing as activated but not in use. All it took then was a quick reboot  and :guitar:

Hope this helps someone![/QUOTE

---

### Post by akarun on 2010-10-13
Thanks a lot! I will give it a shot today!

---

### Post by mjuvt on 2010-11-01
Thanks to binarylife!!

Worked for me with an Acer Aspire One (10.1 inch display) and Ubuntu 10.10 netbook edition.

Before, I had tried that standard procedure of Ubuntu to install the binary driver for the Broadcom WLAN device. It failed. The b43-fwcutter method also failed ("unsupported low-power device"). But your post showed me the way :)

:P

---

### Post by binarylife on 2010-11-03
> **mjuvt said:**
> Thanks to binarylife!!

Worked for me with an Acer Aspire One (10.1 inch display) and Ubuntu 10.10 netbook edition.

Before, I had tried that standard procedure of Ubuntu to install the binary driver for the Broadcom WLAN device. It failed. The b43-fwcutter method also failed ("unsupported low-power device"). But your post showed me the way :)

:P
Great man ! I am happy to hear that ..! 
: )

---

### Post by RandomGuy8291 on 2010-11-06
I just want to thank Binary for posting this solution; it helped me solve all of my wireless connection problems on my Dell Inspiron 1525 (after I had searched for a solution for hours to no avail).

Thanks! You saved me a lot of time! :)

---

### Post by xtechcode on 2010-11-14
Hellow fellows! Firstly I would like to thank to _binarylife_ for partial solution of my problem.

How I resolved the problem:

sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

As you can see I had to remove firmware-b43-installer firstly. Without that I couldn't remove dkms and bcmwl-kernel-source (it returned error). Anyway, my wireless now works thanks to binarylife. :)

---

### Post by binarylife on 2010-11-14
> **xtechcode said:**
> Hellow fellows! Firstly I would like to thank to _binarylife_ for partial solution of my problem.

How I resolved the problem:

sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

As you can see I had to remove firmware-b43-installer firstly. Without that I couldn't remove dkms and bcmwl-kernel-source (it returned error). Anyway, my wireless now works thanks to binarylife. :)

My pleasure ! You are welcome anytime. And thanks for putting full solution so maybe another person would have the same problem.
Enjoy Ubuntu :D

---

### Post by nnamdi on 2010-11-27
thank you so much it worked for me!!!

---

### Post by killa.fr0gg on 2010-12-01
*sigh* It seems I'm the odd man out... I upgraded to 10.10 just earlier today, and it's funny - wireless worked fine in the liveCD, and now absolutely refuses to work. Doesn't make any sense... I'm gonna reinstall and see if that magically fixes anything...

---

### Post by binarylife on 2010-12-02
> **killa.fr0gg said:**
> *sigh* It seems I'm the odd man out... I upgraded to 10.10 just earlier today, and it's funny - wireless worked fine in the liveCD, and now absolutely refuses to work. Doesn't make any sense... I'm gonna reinstall and see if that magically fixes anything...

Try this before you reinstall anything.


> **xtechcode said:**
> Hellow fellows! Firstly I would like to thank to _binarylife_ for partial solution of my problem.

How I resolved the problem:

sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

As you can see I had to remove firmware-b43-installer firstly. Without that I couldn't remove dkms and bcmwl-kernel-source (it returned error). Anyway, my wireless now works thanks to binarylife. :)

---

### Post by killa.fr0gg on 2010-12-02
> **binarylife said:**
> Try this before you reinstall anything.

Haha I did that already of course! What ended up happening, though, is after about three reinstalls and a lot of carefully calculated update/uninstall/reinstall tasks I got it working! And ultimately, this thread was the big helper - thank goodness for rooted Androids and USB tethering!

Maverick is slick!

---

### Post by Penguin=) on 2010-12-04
> **killa.fr0gg said:**
> *sigh* It seems I'm the odd man out... I upgraded to 10.10 just earlier today, and it's funny - wireless worked fine in the liveCD, and now absolutely refuses to work. Doesn't make any sense... I'm gonna reinstall and see if that magically fixes anything...

If it still isen't fixed do what i said in this post:

[http://ubuntuforums.org/showthread.php?p=10198674#post10198674](http://ubuntuforums.org/showthread.php?p=10198674#post10198674)

hope it helps you!

---

### Post by Safoora on 2010-12-06
> **xtechcode said:**
> Hellow fellows! Firstly I would like to thank to _binarylife_ for partial solution of my problem.

How I resolved the problem:

sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

As you can see I had to remove firmware-b43-installer firstly. Without that I couldn't remove dkms and bcmwl-kernel-source (it returned error). Anyway, my wireless now works thanks to binarylife. :)

Hello!
I just registeres to thank you and binarylife!!!
I've had this wireless problem for about a year!! I have Dell Vostro 1520. First I used Ubuntu 9.10 and I never found out how to make it recognize my wireless card!! Then recently I upgraded to 10.10 and using your solution I got it solved... Thank you!

---

### Post by binarylife on 2010-12-07
> **Safoora said:**
> Hello!
I just registeres to thank you and binarylife!!!
I've had this wireless problem for about a year!! I have Dell Vostro 1520. First I used Ubuntu 9.10 and I never found out how to make it recognize my wireless card!! Then recently I upgraded to 10.10 and using your solution I got it solved... Thank you!

You are welcome , Enjoy Ubuntu (:

---

### Post by bimbot on 2011-01-30
> **xtechcode said:**
> Hellow fellows! Firstly I would like to thank to _binarylife_ for partial solution of my problem.

How I resolved the problem:

sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

As you can see I had to remove firmware-b43-installer firstly. Without that I couldn't remove dkms and bcmwl-kernel-source (it returned error). Anyway, my wireless now works thanks to binarylife. :)


Thanks for this.  I didn't even think to uninstall b43 first.  I, too, was getting the error when trying to remove dkms.

These exact steps fixed wireless in my cousin's HP 1000

---

### Post by mcasim on 2011-02-06
Hello, I have the same problem, but I cant solve it like this.

I am trying to install ubuntu 10.10 on a USB drive. When I boot from CD I can activate the Broadcom driver without any problem.

But when I boot from the USB drive, which was created by the ubuntu-internal program, I can not install the Broadcom driver. I get the error: installArchives() failed

After that it is not possible to remove the packages dkms and bcmwl-kernel-source.

The bc43-installer is not installed.

Details:
Dell 1564 with BCM43224 Chip (ID 4353)

Is there anyone who has an idea why it is not working from USB drive?

Best regards,

mcasim

---

### Post by aluex on 2011-02-09
Thx, i got it solved following your posts. :)

---

### Post by milesk12 on 2011-02-23
Hi,
 
I'm new to Ubuntu and this forum however I am not new when it comes to unix systems. I would just like to say you guys are stars, this has fixed my issue as I had this problem after installing several backport modules. 
 
I do however have a question which is slightly off topic but still related to wireless.
I have a linksys WMP54GS and a ubuntu machine in my shed the total distance from AP to machine is no more than about 10 feet with 2 walls between them. I have an issue and I'm not sure if its network or samba related.
 
When I copy files to my ubuntu box from my XP machine it will start copying and then drop out usually with an error like "path is too deep" or "connection was reset". I think this is network related as my wireless does sometime skip when pinging. Is there anyway I can make wireless more responsive and get a stronger network link in Ubuntu 10.10 or setup some kind of flow control in samba to stop this? The network starts at 70% but seems to degrade over time to the point where its unusable using a network cable is not an option.
 
Any further help is appreciated.
 
[COLOR=black][FONT=Verdana]P.S. It appears that this soloution may have resolved my samba copying problem in the process, maybe this is the result of re-installing the mention packages correctly as there was obviously something not right. I have just managed to copy serveral large files so far without issue, however I'm not sure if this is just the calm before the storm. In the past it has worked but it just seems pretty hit and miss. I will keep an eye on it please ignore the above for the meantime.[/FONT][/COLOR]

---

### Post by rehpot73 on 2011-02-25
I'm running a dell 1526 laptop with the same card.  [xtechcode]("http://ubuntuforums.org/member.php?u=1187749") instructions worked great.  

:DThanks

---

### Post by aochoa on 2011-03-04
It also solved the same problem on a DELL Inspiron 1545 where I just replaced Windows with Ubuntu. 

And it is working amazingly fast and better than ever.

Thank you very much for your tips.

Arturo

---

### Post by bytefish on 2011-03-10
Thanks a lot for the tip. Solved the problem on my Lenovo G550, works like charm now.

---

### Post by kerry79 on 2011-03-10
Hi there, just installed Xubuntu 10.04 on an old laptop. Like the original problem others were seeing, I too was unable to connect via wireless. I followed the steps outlined i.e.
[I]sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot[/I]

Turns out that firmware-b43-installer, dkms or bcmwl-kernel-source weren't already installed. So I went ahead and installed bcmwl-kernel-source and then rebooted. Now both my ethernet and wireless networks are showing as UNCLAIMED. And eth0 is no longer showing up on 'ifconfig'. It does appear though that the ethernet and wireless controllers are being identified. 

Any ideas how I might recover from this situation? Is there a way to roll back to the drivers prior to installing bcmwl-kernel-source?

Thanks

---

### Post by K_Boomer on 2011-03-15
the sudo purge method worked well for me, but only after I installed wicd via terminal, rebooted, activated b43 driver, then rebooted again. I'm just glad this is up and running. 

Thanks!

---

### Post by Technologiic on 2011-04-25
worked for a hp pavillion ! bravo good sir ! :P

---

### Post by rixseeco on 2011-10-10
guys, please do me a favor... I followed all your guides whether by complete uninstallations on synaptics and also using the sudo apt-get install bcmwl-kernel.source.. What i've found that on the installation package on both guides includes dkms to be installed as well.. then i've tried to just removing the dms package, still, no solution.. running BT5 on HP mini... thanks for advance..

---

### Post by Tomba1110 on 2011-10-27
Hi
My wireless stopped working when I turned on my laptop today and I tried this method but it's not working for me. 
First I tried to remove and again activate my STA Broadcom Wireless driver but when I tried to activate it I got the "SystemError: installArchives() failed" error

So I went to Synaptic and completely removed dkms and bcmwl-kernel-source and installed bcmwl-kernel-source again. During the installation I got an error:
"E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 10"

When I viewed installation details (terminal) I got these errors too:
------------
Error! Bad return status for module build on kernel: 2.6.32-34-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.

DO YOU HAVE gcc INSTALLED???
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
-------------

PS The day before,I tried to connect to WiFi at my college and I changed the wpa_supplicant.conf in order to connect (but I forgot to do a back-up of it). And I managed to connect and when I got home,wireless still worked. But the supplicant isn't the main problem anymore. Please help anyone.

---

### Post by Tomba1110 on 2011-10-27
I checked the make.log file in the  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build.

-------------
 DKMS make.log for bcmwl-5.60.48.36+bdcom for kernel 2.6.32-34-generic (x86_64)
Thu Oct 27 17:32:28 CEST 2011
make: Entering directory `/usr/src/linux-headers-2.6.32-34-generic'
/usr/src/linux-headers-2.6.32-34-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make: gcc: Command not found
  LD      /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/built-in.o
  CC [M]  /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o
/bin/sh: gcc: not found
make[1]: *** [/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/src/shared/linux_osl.o] Error 127
make: *** [_module_/var/lib/dkms/bcmwl/5.60.48.36+bdcom/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-34-generic'
---------------

Looks like I don't have a C compiler. I tried to install gcc from Synaptic but I get the same error like with bcmwl-kernel-source:  "DO YOU HAVE gcc INSTALLED???" etc.

---

### Post by Tomba1110 on 2011-10-29
OK I solved my issue here, I completely removed dkms,bcmwl-kernel-source and gcc package,then rebooted, installed gcc and this time I wasn't getting any errors so I installed the rest and rebooted again. Tnx anyway

---

### Post by gaisboy on 2012-01-19
> **xtechcode said:**
> Hellow fellows! Firstly I would like to thank to _binarylife_ for partial solution of my problem.

How I resolved the problem:

sudo apt-get --purge remove firmware-b43-installer
sudo apt-get --purge remove dkms
sudo apt-get --purge remove bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
sudo reboot

As you can see I had to remove firmware-b43-installer firstly. Without that I couldn't remove dkms and bcmwl-kernel-source (it returned error). Anyway, my wireless now works thanks to binarylife. :)


THANK YOU FROM DEEPEST OF MY HEART!!!!!!!!!!!!!!!!!  :popcorn:

---

### Post by lefteris121 on 2012-08-11
[LEFT][FONT=Arial Black]Hi . I have the same problem. InstallArchives() failed : Selecting previously deselected package patch. This message appeared when I tried to Install any program .[/FONT]
Please help me !!
:confused:

[/LEFT]

---

