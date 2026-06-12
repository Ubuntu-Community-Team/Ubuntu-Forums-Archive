---
title: "Samsung Captivate (samsung galaxy s) mounting issues"
date: 2010-08-21
forum: General Help
---

### Post by radtek on 2010-08-21
I bought this nifty **android** phone last week. On .xda developers forum the official solution to connecting to this phone is to use virtualbox and install windows and a program called "kies" I don't think there's many linux users over there.

I've done this and found a random xp torrent which installs nicely. Unsure about the security aspect but will disable Internet access. Still working on getting it to sync under Windows. Makes me sick to even try to use it...](*,)

Regardless, under the 4 different syncing functions available on the phone I can only get my pics off of the Media player syncing option with F-spot (just like my iPhone). So that's good.

So- other than this^^^ while ubuntu sees my phone I can't mount it to look at the file system or transfer files.

Help? Ideas? Some sort of SSH issue?

Thanks.

---

### Post by ythe1300 on 2010-08-27
any ideas on this one guys?

---

### Post by mlalkaka on 2010-08-30
I just picked up this phone recently as well. I think if you want to view the raw files on the device, you have to enable USB Debugging Mode (Settings > Applications > Development > USB Debugging). When I did this, I see new devices in Nautilus when I click on "Computer", but I can't seem to actually open those new drives up. Let me know how it goes for you.

---

### Post by Fife3951 on 2010-09-01
Having the same frustrating issues here.

A solution would be AWESOME.

---

### Post by jamesey on 2010-09-03
the same thing happens on my galaxy s (vibrant edition)

---

### Post by Flyboy712 on 2010-09-03
Go to settings> applications> USB Settings> select "mass storage" or as I do it select "ask on connection" then I can choose what I want to do with it when I plug it in.  When you plug in your USB  go to your notification bar at the top where you see the USB symbol and press and hold then pull down the notification bar or main menu> notifications, you should see a notification saying "USB Connected" select it and it will give you the option to mount your phone.

Thats it it'll show up in nautilus and you can drag and drop files just like a thumb drive.

Samsung offers Windows drivers that might make it automatically mount in Windows thus no complaints from that community about it.

---

### Post by apropos on 2010-09-28
> **Flyboy712 said:**
> Go to settings> applications> ... When you plug in your USB  go to your notification bar at the top where you see the USB symbol and press and hold then pull down the notification bar or main menu> notifications, you should see a notification saying "USB Connected" select it and it will give you the option to mount your phone. ...
Thanks, your solution works.

---

### Post by confused_user on 2010-10-11
That does not work for me :(

I'm working around it by installing swiftp server on the phone and just connecting to it over wifi / ftp

---

### Post by mkubena on 2010-12-03
Ha ha this is really weird.  For all of those who have followed the steps in this thread, it has worked for one of my captivate phones but not the other.  So as a last ditch option, make sure that you have a micro sd card in the phone.  Then put the phone in usb debugging, and mount. voila, it will now work.

---

### Post by zjagannatha on 2010-12-16
I was having similar issues mounting the internal SD card for my Sony Captivate i897.

(FYI, I'm running Ubuntu Lucid Lynx)

Plug in the Phone using the USB cable.
When promped, select "Mass Storage" on the phone.
In the status bar there should be a notification that USB Storage was activated. Tap it and it'll pop up a message asking if you want to mount the SD card. Click "Mount" and the SD card appears on the left panel in the file manager in Ubuntu.

You can them mount it and transfer files as needed.

Hope that helps!

---

### Post by fozzytbear on 2011-01-13
> **Flyboy712 said:**
> Go to settings> applications> USB Settings> select "mass storage" or as I do it select "ask on connection" then I can choose what I want to do with it when I plug it in.  When you plug in your USB  go to your notification bar at the top where you see the USB symbol and press and hold then pull down the notification bar or main menu> notifications, you should see a notification saying "USB Connected" select it and it will give you the option to mount your phone.

Thats it it'll show up in nautilus and you can drag and drop files just like a thumb drive.

Samsung offers Windows drivers that might make it automatically mount in Windows thus no complaints from that community about it.

Works for me, too.

---

### Post by impresionist on 2011-03-24
> **Flyboy712 said:**
> Go to settings> applications> USB Settings> select "mass storage" or as I do it select "ask on connection" then I can choose what I want to do with it when I plug it in.  When you plug in your USB  go to your notification bar at the top where you see the USB symbol and press and hold then pull down the notification bar or main menu> notifications, you should see a notification saying "USB Connected" select it and it will give you the option to mount your phone.

Thats it it'll show up in nautilus and you can drag and drop files just like a thumb drive.


Hi Guys,
It's work for me in Samsung Galaxy S v. Lucid

BUT, what that's all, no SSH access to that Samsung, how? I just changed my Iphone with this Samsung to run away from Mr. Apple, there Cydia like minimum offer an ssh access, here I can't find any way for that??

Regards,

---

### Post by xe1ufo on 2011-04-05
> **Flyboy712 said:**
> Go to settings> applications> USB Settings> select "mass storage" or as I do it select "ask on connection" then I can choose what I want to do with it when I plug it in.  When you plug in your USB  go to your notification bar at the top where you see the USB symbol and press and hold then pull down the notification bar or main menu> notifications, you should see a notification saying "USB Connected" select it and it will give you the option to mount your phone.

Thats it it'll show up in nautilus and you can drag and drop files just like a thumb drive.

Samsung offers Windows drivers that might make it automatically mount in Windows thus no complaints from that community about it.

This worked like a champ for accessing my Samsung Galaxy S i9000 memory card! Thanks, Mr Flyboy712! Now if I could just figure out a way get at my contacts and their phone numbers.

---

### Post by morrna on 2011-04-14
When I connect my Captivate via USB to my laptop (Toshiba Portege m200 running Ubuntu 10.04) it just recognizes it as a generic power source, and I never get the chance to mount it.  Any ideas of what could cause this?

---

