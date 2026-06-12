---
title: "Broadcom + Ubuntu 9.10"
date: 2009-11-02
forum: General Help
---

### Post by howcanireachthesekids on 2009-11-02
Is there anyone that has already got their  Broadcom Wireless BCM4312 card to work with Ubuntu 9.10 ? 
 
I am not talking about Live CD, it  [IMG]http://img5.warez-bb.org/images/smiles/icon_eek.gif[/IMG] works from Live CD version but not when trying to use it from installed Ubuntu  [IMG]http://img5.warez-bb.org/images/smiles/icon_eek.gif[/IMG]  [IMG]http://img5.warez-bb.org/images/smiles/icon_sad.gif[/IMG] Weird. 
 
Anyway, if there is anyone who could fix this problem, PLEASE PLEASE let me know. 
I am having a big headache with this problem [IMG]http://img5.warez-bb.org/images/smiles/icon_sad.gif[/IMG] It is so frustrating

---

### Post by Dimoutlook on 2009-11-02
It works just fine, you may have to enable it from the system>administration>hardware drivers.on my old Acer Aspire I'm getting the full bandwidth of 54 mbs

Dimoutlook

---

### Post by howcanireachthesekids on 2009-11-02
> **Dimoutlook said:**
> It works just fine, you may have to enable it from the system>administration>hardware drivers.on my old Acer Aspire I'm getting the full bandwidth of 54 mbs

Dimoutlook
No it doesnt work just fine, and if you think that i am doing something wrong, other people cant just be all wrong ...
anyway when i try to activate it from the Hardware Drivers it will not get activated ! FRUSTRATING :(

What amazes me is that it works in LIVE CD !

---

### Post by Dimoutlook on 2009-11-02
As I said it works just fine on multiple computers and laptops. If you are having a problem, then please be a little more civil in your replies, thousands of users are using broadcom cards with no problems.

Dimoutlook

---

### Post by gan1708 on 2009-11-02
You could try completely removing the broadcom driver via synaptic (or package kit) and then reinstalling it again.

That did the trick on my Lenovo s10-2 netbook when I tried Kubuntu Netbook Edition a few days ago.

---

### Post by Stripes on 2009-11-02
Following a clean install I went to system>administration>hardware drivers and found nothing there. Just a blank text box. I don't think well meaning people recommending this realize it will be blank.

I got my 4328 chip to work by going into synaptic and hitting the "reload" button. I closed out synaptic then went to system>administration>hardware drivers. Now I had an entry there for Broadcom STA. Using that the wireless turned on just fine.

Steve

---

### Post by MHmedia on 2009-11-02
I have a Dell Inspiron 6400 which has a 1390 wireless card, which apparently is a Broadcom 4312. 

I found that I had to use the "fwcutter" utility to install drivers and then it connected reliably and consistently to my Draytek Vigor wireless router. *However*, although it will see my Huawei E5830 MiFi dongle/wireless access point/router device I just can't get it to connect. 

I've come to the conclusion, as have others, that the Broadcom is problematic with certain routers, and in general you have to live with it. Perhaps lobbying Broadcom for a native driver would help..

---

### Post by h@l0 on 2009-11-08
I have the wl driver working for that chipset on a Lenovo Ideapad S10e.  Is that it listed in your /etc/modprobe.d/blacklist* files?  Is there any related dmesg output.

---

### Post by Digikid on 2009-11-08
Try this.

After a clean install go IMMEDIATELY to the Update Manager....NOT Synaptic.  Do all of the updates using a Networking Cable....reboot....then afterwards go to the Hardware Drivers Section and then activate your Broadcom device.  Reboot and THEN remove Networking Cable and logong to your Wifi.

Worked for me perfectly twice now.

---

### Post by NFblaze on 2009-11-08
I've had that problem a couple times on various versions of ubuntu...I really dont understand why the hell the Hardware Drivers interface does that it really sucks, whenever you see the driver and it wont get activated no matter how many times you do it, but it works just perfectly on the LiveCD

What I've done now is keep a copy of the .deb file offline for myself.
Here is a link to a discussion, that has the link to the deb file among other solutions.
[URL="http://ubuntuforums.org/showthread.php?t=1229614"]
http://ubuntuforums.org/showthread.php?t=1229614[/URL]

but I havent tried the other solutions listed in their the .deb file works for my situation.

---

### Post by And-car on 2009-11-08
I'm having a similar problem with wi-fi networks not being detected on my Dell machine/Broadcom wi-fi. But when I cable it in, I still can't get to the internet. Browser page begins to load but just hangs. I wondered if my network manager is snafu'd. 

Looking at other threads on this topic, I see some people suggest typing command lshw but I get "command not found" message. Any suggestions please?

---

### Post by NFblaze on 2009-11-08
I dont know about your first problem. Though are you sure you have lshw installed. Type in "where lshw" if it prints out a path like /usr/bin/lshw that means it's there you usually have to run lshw with sudo.

If not you can see if you can install it from synaptic.

---

### Post by And-car on 2009-11-10
Thanks, I installed from synaptic.

---

### Post by colleenyork on 2009-11-14
OH MY GOSH THANKS. This worked after like a day of frustration. 
FYI: I have a Dell Inspiron 1545, my chipset is Broadcom4312.  I used the Broadcom STA driver.  
In my previous installation it would hang when I tried to activate it.
 
Thanks!
- Total Newbie

---

### Post by colleenyork on 2009-11-14
OH MY GOSH THANKS. This worked after like a day of frustration. 
FYI: I have a Dell Inspiron 1545, my chipset is Broadcom4312. I used the Broadcom STA driver. 
In my previous installation it would hang when I tried to activate it.

Thanks!
- Total Newbie

---

### Post by jon_heard on 2009-11-21
> **Digikid said:**
> Try this.
 
After a clean install go IMMEDIATELY to the Update Manager....NOT Synaptic. Do all of the updates using a Networking Cable....reboot....then afterwards go to the Hardware Drivers Section and then activate your Broadcom device. Reboot and THEN remove Networking Cable and logong to your Wifi.
 
Worked for me perfectly twice now.
 
 
Just wanted to say "thanks" for this little gem of a tip!!! I'm a recent convert to Linux and Ubuntu (living on the Isle of Man, i thought I should try and stick to a "local" version!!). I had tried the Netbook Remix version of Ubuntu but it was running incredibly slow on my lilttle HP2133 netbook! Not only that, it couldnt see the Broadcom device....just installed the full version of Ubuntu and had the same problem, but thanks to this forum and Digikid I've got it all up & running!!! So cheers - good work fella!

---

### Post by howcanireachthesekids on 2009-11-26
shameless bump

---

