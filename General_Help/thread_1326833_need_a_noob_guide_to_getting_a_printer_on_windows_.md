---
title: "need a noob guide to getting a printer on windows machine to work with ubuntu"
date: 2009-11-14
forum: General Help
---

### Post by AmishFury on 2009-11-14
everything i can find through google and searching these forums is not helping much

the printer (HP deskjet 3650) is connected to desktop running windows xp 

the laptop running ubuntu (8.04) has samba installed and the smb.conf is set according to what is recommended in the threads and such that i can find 

the printer works with the laptop just fine in windows (though right now windows itself is not working so well on the laptop) but when i click browse when adding a printer in ubuntu it says "scanning" for a bit then nothing




...getting the printer to work the other way (desktop running ubuntu and laptop running windows) was alot simpler

---

### Post by 73ckn797 on 2009-11-14
See if this will help:
[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

or
[https://help.ubuntu.com/community/HPPrinterInstallation](https://help.ubuntu.com/community/HPPrinterInstallation)
or
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

Have you installed 'hplip" from the repos? Check that first. I believe that it is included. you may want to install "hplip-gui".

---

### Post by AmishFury on 2009-11-14
yes that is installed and unless i'm mistaken that only helps if i was trying to connect the printer directly to the laptop

this is a problem with printing over a network with the printer on a windows machine... i'm sure i mentioned that somewhere in my post

---

### Post by jamesisin on 2009-11-14
I wrote this blog post:

[http://www.soundunreason.com/InkWell/?p=767](http://www.soundunreason.com/InkWell/?p=767)

Maybe it will help you some.

---

### Post by dcstar on 2009-11-14
> **AmishFury said:**
> everything i can find through google and searching these forums is not helping much

the printer (HP deskjet 3650) is connected to desktop running windows xp 

the laptop running ubuntu (8.04) has samba installed and the smb.conf is set according to what is recommended in the threads and such that i can find 

the printer works with the laptop just fine in windows (though right now windows itself is not working so well on the laptop) but when i click browse when adding a printer in ubuntu it says "scanning" for a bit then nothing




...getting the printer to work the other way (desktop running ubuntu and laptop running windows) was alot simpler

And we all assume that you have enabled File and Print sharing and shared the printer.....

---

### Post by 73ckn797 on 2009-11-14
> **AmishFury said:**
> yes that is installed and unless i'm mistaken that only helps if i was trying to connect the printer directly to the laptop

this is a problem with printing over a network with the printer on a windows machine... i'm sure i mentioned that somewhere in my post

You did but I was throwing out multiple options.

---

### Post by AmishFury on 2009-11-14
> **jamesisin said:**
> I wrote this blog post:

[http://www.soundunreason.com/InkWell/?p=767](http://www.soundunreason.com/InkWell/?p=767)

Maybe it will help you some.

well this got the printer installed and it sends print jobs

but... the printer makes a few noises, quits, the print jobs won't go away unless i reboot windows machine

ubuntu is great when you don't try to get it to play nice with windows ](*,)

---

### Post by jamesisin on 2009-11-15
Yeah, or "Windows is great as long as you don't try to get it to do anything"...

My printer rarely plays nicely, even on the Windows server to which it is attached.  So it goes.

---

### Post by AmishFury on 2009-11-15
well good for you then :p

i've resorted to just using the pdf option then printing the pdf on the windows machine

unless someone has a suggestion

---

