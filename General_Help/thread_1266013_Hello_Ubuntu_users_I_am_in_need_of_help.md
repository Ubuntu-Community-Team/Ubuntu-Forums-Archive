---
title: "Hello Ubuntu users I am in need of help"
date: 2009-09-14
forum: General Help
---

### Post by Daylon on 2009-09-14
Hello Ubuntu users I am new to this OS and before I install Ubuntu and completely forget about windows I'd like to explain my pc problems and some questions.

The reason why I am switching to Ubuntu is because my computer crashed and I sent it to get fixed and they didn't do anything all they did was make a new partition and install the OS on there, the problem is my boot partition is only 5GB and I'm getting stupid fatal disk error messages and I'm just so sick of it I want to throw my pc in the pool, but my friend reccomended Ubuntu he says that it works just fine and personally I like the interfaces and I've seen some videos of it. I do know how to delete the partition and ect but I have NO copies of windows CD's, well I do but it's really old like 2002 or something like that. 

My concerns are as follows:

Will my Nvidia video card work?
Will my Realtek speakers work?
***********I'm connected to the internet through a Wireless USB Adapter is this a problem? I have the install CD.***********
I play a game called runescape it is Java-Based (pretty much all I do on my computer), will it work fine?

Anyway please take the time to read my thread and let me know if I will have any problems with what I stated above, most importantly the internet question.

Thankyou all and have a pleasant day,
Vtec!

---

### Post by Sub101 on 2009-09-14
Do you have anymore info about the wireless adapter?

---

### Post by Ms_Angel_D on 2009-09-14
Before you come running head long into ubuntu(something a lot of people have done...lol) I highly suggest some reading. You should be aware of what kind of change your making. A lot of people come to ubuntu for a free version of windows, only to be plagued with problems later because they didn't research first.

Start Here
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Then if you still wish to give Ubuntu a try Use these
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

As far as runescape, it works fine. I was just playing it. You'll have to be a bit more specific on the make & model of your Video card & Sound as I wouldn't feel comfortable confirming that they should work without more details.

I don't know much about wireless in linux, but I do know you'll need to give more details on the wireless card.


If you have any other questions feel free to post here someone is always around ;).

---

### Post by kixome on 2009-09-14
the wireless could be a problem, but java games and such, should not be any problem whatsoever. Nvidia should work if its not the newest of the new. Realtek is no sweat, usually works with out a hitch. If the wireless is a belkin, linksys, netgear adapter, then all should be fine unless it uses a broadcom chipset. Most belkins use zydas wich uses a proprietary driver but works fine.
Basically if your computer is not brand new, almost everything should work. As mentioned above, specifics will go a long way toward knowing if your HW is compatible.

---

### Post by Daylon on 2009-09-14
> **Sub101 said:**
> Do you have anymore info about the wireless adapter?


[http://amcoso.com/index.php?page=shop.product_details&flypage=flypage_new.tpl&product_id=73&category_id=28&option=com_virtuemart&Itemid=109&vmcchk=1&Itemid=109](http://amcoso.com/index.php?page=shop.product_details&flypage=flypage_new.tpl&product_id=73&category_id=28&option=com_virtuemart&Itemid=109&vmcchk=1&Itemid=109)

That is the EXACT model I have, what do you think?

---

### Post by thecow on 2009-09-14
> **kixome said:**
> If the wireless is a belkin, linksys, netgear adapter, then all should be fine unless it uses a broadcom chipset. 

That is generally false in my experience, that is if you want to use WPA.  I have a linksys wireless adapter that uses a Ralink chipset.  Ralink has drivers that I installed and the adapter did indeed work, that is if you dont want to use WPA.  Because of that the whole adapter is now not functional, (I mean who doesn't use WPA?)

---

### Post by P4man on 2009-09-14
I think the best way is to make an ubuntu cd, boot from it, and try it out. You can run a live cd without installing anything, although it has some limitations and is pretty slow compared to a normal install. You can also use a USB stick instead of a cd.

However, the issues you had with windows might well have been hardware related (im thinking of a harddisk gone bad), and if that was the case, then using another operating system isn't going to cure it Im afraid.

nvidia card is no problem though.

> 
[http://amcoso.com/index.php?page=sho...k=1&Itemid=109](http://amcoso.com/index.php?page=sho...k=1&Itemid=109)

That is the EXACT model I have, what do you think? 

Thats a router (/modem/access point), not a wireless adapter. If you connect to that router with a network cable, there will no problem whatsoever. if you connect wirelessly, we need to know which wireless card or stick you are using in the PC (although almost any wifi card can be made to work, and most just work without any effort, just out of the box).

---

### Post by Daylon on 2009-09-14
okay i think i linked you to the wrong place. but below i am sure that mine is exactly the same, below is my wireless usb adapter

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3522753&CatId=2692](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3522753&CatId=2692)

that looks the same as mine and the specs are the same

---

### Post by 3rdalbum on 2009-09-14
Looks like an Atheros-based device. Here's an Ubuntu Forums topic about it from quite a few months ago:

[http://ubuntuforums.org/showthread.php?t=893879&page=2](http://ubuntuforums.org/showthread.php?t=893879&page=2)

(in other words, it's out-of-date - they're talking about using it on Ubuntu 8.10, and the current Ubuntu version is 9.04; the Atheros driver is much different today).

According to linuxwireless.co.uk, that card is "recommended (works with minimal configuration)" and uses the ath5k driver, which is present in Ubuntu 9.04 out-of-the-box.

Why don't you just download the Ubuntu desktop CD, boot it up on your machines and use the "Try Ubuntu" option at the startup menu, and see if the wireless card works? That's the easiest way to settle it!

---

### Post by rob-ward on 2009-09-14
I would reccommend that you give Ubuntu live cd ago, you should have no problem with the nvidia card and the wireless device you linked to should work. However I beleive from your first comment that you may have a hardware issue, likely a hard drive causing most of your problems so ubuntu may not fix them.

---

### Post by Daylon on 2009-09-14
ugh i made a live cd and put it in while windows was booted and it works fine but my windows is REFUSING to boot from cd i even used the boot helper that comes with the cd does anyone have any last suggestions beforei  just wipe windows and regret it? ive set my boot sequence in the order of 1st 2nd 3rd 4th ALL to cd and still nothing

---

### Post by mike555 on 2009-09-14
You did burn it as an image right? (not as data) and burned it slowly?

---

### Post by P4man on 2009-09-14
I think he already installed it actually...with wubi? Rather than just booting off the disk?

---

### Post by mike555 on 2009-09-14
boot helper??? that is a new one for me........ you are restarting your computer with the cd in (and not trying to boot from within Windows right ?) and do you have at least 512 RAM memory? 
  if you give us more info we can help you better ...

and if you can't start the Ubuntu cd how are you going to wipe Windows??


I don't mean to sound like a smart ars ,just trying to help.

---

### Post by Daylon on 2009-09-14
Okay I installed ubuntu successfuly testing live first also checked for disk errors  and memory test on the ubuntu splash screen everything went well until i chose partitioning and like it told me to make a swap-area thing or w/e and i gave it 5Gb and like my windows got erased :S i dont care though my main problem is that my USB adapter (i named the specs and link a few posts back) is NOT working it will NOT read any networks it just tells me to add a wireless and i put in my ssid and wep key and still no connect it just lets me edit/erase, i have no internet connection on it so yeah i had to boot my other pc up to get on here does anyone know whats wrong and how i can fix it?

---

### Post by P4man on 2009-09-15
Need to know the exact type of wifi card. To get that, open a terminal (apps > accessories > terminal) type

```
lsusb
```

find the line that relates to the wifi stick and post it here.
Can you get a wired internet connection temporarily ?

---

### Post by Daylon on 2009-09-15
> **P4man said:**
> Need to know the exact type of wifi card. To get that, open a terminal (apps > accessories > terminal) type

```
lsusb
```find the line that relates to the wifi stick and post it here.
Can you get a wired internet connection temporarily ?


it showed Netgear, Inc. 

I followed this guide on youtube and it told me to insert my ubuntu disc and install ndiswrapper everything went fine until i got to my driver file and i didn't see a .inf file in the CD :/ i really thought that would have fixed my problems big let down :/

---

### Post by ccline19 on 2009-09-15
I would be concerned with the fatal disk errors. You said the computer crashed, was the HD replaced? If not, you might have a HD going out and you would need to fix this first.
When HD's are about to "crash" they tend to give out a loud high whining noise. Much louder then when you first got it. In most cases it is the result of the head free floating across the plater and makes nick's in the disk resulting in disk I/O's errors. A simply chkdsk can determine if your disk "appears" to be ok.

---

### Post by Daylon on 2009-09-15
also, i do not see my video card under hardware drivers is it possible to get the driver some other way??? i don't have internet

---

### Post by P4man on 2009-09-15
> **Daylon said:**
> it showed Netgear, Inc. 

I followed this guide on youtube and it told me to insert my ubuntu disc and install ndiswrapper everything went fine until i got to my driver file and i didn't see a .inf file in the CD :/ i really thought that would have fixed my problems big let down :/

netgear is just a brand, Id need the exact model to give you better info.
If you want to use ndiswrapper you have to feed it the extracted windows driver (.inf file and some .sys files I think), not some big .exe file that installs the driver along with other software.

---

