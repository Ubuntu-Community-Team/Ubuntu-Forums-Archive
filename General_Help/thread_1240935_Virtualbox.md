---
title: "Virtualbox"
date: 2009-08-15
forum: General Help
---

### Post by Shugs81 on 2009-08-15
Hi Chaps...

Just got virtual box up and running and there's a few questions i'm hoping people can help me with...

firstly... how do i get an internet connection? is it possible? and how do i get access to other drives and usb devices? it doesn't read my usb external hdd and i can't get access to my windows drive...

any help with this will make me leave windows off all my computers for good...

---

### Post by yeeeev on 2009-08-15
I'm guessing you're talking about an Ubuntu host with a Windows guest.
Regarding networking, it worked for me after installation with no efforts. Try Settings->Network->enable network adapter (as NAT works for me)
Regarding USB Try settings->usb->enable

---

### Post by Shugs81 on 2009-08-16
booo... it better not be that easy!!! though knowing me that will be the case!! lol...

---

### Post by AlanR8 on 2009-08-16
It is that easy!

---

### Post by Shugs81 on 2009-08-16
well... got t'interweb working... it was that easy...

as to usb hard drives.... not finding anything.... not even the ipod... could this have something to do with the devices being used in linux? altho they're not actually being used if you know what i mean!

I'm using virtualbox ose... i also have the gtk version (if it is a version!) should i try that? or is there anything else i could try?

and can anyone reccomend a free firewall to install? used to use pctools but for some reason won't load....

---

### Post by Shugs81 on 2009-08-16
oh i forgot to add... how do i get it to recognise my graphics card? and is there a way i can get it to read my windows HD or should i just create another fake partition? and is there a way to access the virtual box HD without loading it?

and does Itunes work in it?

Ta!

---

### Post by earthpigg on 2009-08-16
unless i am mistaken, virtualbox for ubuntu 9.04 downloaded directly from sun's website includes features and functionality not included in the OSE (open source edition) found in ubuntu's repositories.

what i do know for a fact is i had problems a while back with vbox from the repos, i uninstalled it, installed it from sun's website and everything worked perfectly, and i havent tried the OSE since.

---

### Post by theozzlives on 2009-08-16
ose don't support USB, you want the one from: [http://www.virtualbox.org/]("http://www.virtualbox.org/")

---

### Post by howefield on 2009-08-16
> **Shugs81 said:**
> well... got t'interweb working... it was that easy...

as to usb hard drives.... not finding anything.... not even the ipod... could this have something to do with the devices being used in linux? altho they're not actually being used if you know what i mean!

I'm using virtualbox ose... i also have the gtk version (if it is a version!) should i try that? or is there anything else i could try?

and can anyone reccomend a free firewall to install? used to use pctools but for some reason won't load....

The OSE version doesn't have USB support, you would need to download the PUEL (Personal Use & Evaluation Licence) to get USB support. Download the appropriate .deb file from virtualbox.org.

It won't recognise your graphics card, it uses a virtual driver supplied by virtualbox. Have you installed guest additions ? 

Firewall ? Last time I used a software firewall it was Zone Alarm, but that was several years ago, not sure who the best free software is these days.

---

### Post by Shugs81 on 2009-08-16
aaahhh..... didn't know there was a difference between ose and one of site.... will do that....

as to graphics card issues.... can i specify higher than 127meg in t'other version??

and firewalls.... it's running through linux so guessing it should be pretty ok... plus there's a firewall in the router.... or should i be setting something else up???

---

### Post by howefield on 2009-08-17
> **Shugs81 said:**
> and firewalls.... it's running through linux so guessing it should be pretty ok... plus there's a firewall in the router.... or should i be setting something else up???

Be aware that you should treat your windows vm as you would a normal windows installation as far as securing the system is concerned. I'm not saying you should run a software firewall in addition to the router firewall, just that your windows vm isn't invulnerable because it is "hiding" inside linux.

It isn't.

---

### Post by Shugs81 on 2009-08-18
it's ok... it's just being windows and being a bit random... the firewall now works but even though i've enabled various usb devices and hubs they still don't seem to find them....

and is there a way to mount my ntfs drive? can't tell the difference between machine drives and the other one which i can't remember...

I only wanted to play games through it!!

---

