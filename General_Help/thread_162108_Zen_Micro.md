---
title: "Zen Micro"
date: 2006-04-18
forum: General Help
---

### Post by thunderduck3141 on 2006-04-18
does anybody know how to get the Zen Micro (Creative) working w/ Dapper?
My PC senses it and even names it correctly, but i can transferfiles or open the device
thanks

---

### Post by Omnios on 2006-04-18
You need Gnomad2 which I actualy use for mine and need to start Gnomad with sudo as it can not access the usb without sudo. Personaly I got the Drapper deb off this forum and it works perfetly.

---

### Post by IYY on 2006-04-18
Yeah, it works as long as you run gnomad2 as root.

---

### Post by thunderduck3141 on 2006-04-18
nah that aint working, i get a "No Jukebox Found" message

---

### Post by christooss on 2006-04-20
> nah that aint working, i get a "No Jukebox Found" message

Me too.

---

### Post by nathansnook on 2006-06-10
I also have a creative Zen Micro (Creative) and seem to be having some of the same issues that everyone else here is having.  I am starting to think that it has to do with my own firmware.  I am going to attempt to look for an older version that does not have the MTP included into it.  I will update my results when I find the firmware.

Can not detect the device on USB

Here is a brief an overview of my USB bus

nathan@tux:~/Desktop$ lsusb
Bus 006 Device 011: ID 041e:4130 Creative Technology, Ltd
Bus 006 Device 001: ID 0000:0000
Bus 001 Device 004: ID 03f0:0201 Hewlett-Packard ScanJet 6200c
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c03d Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 002: ID 04f9:0028 Brother Industries, Ltd
Bus 002 Device 001: ID 0000:0000

Thankz,
Nathan

---

### Post by nathansnook on 2006-06-10
Zen Micro Update:

As I have said in my last post I would do some firmware hunting and report my results.

I have found another version of the firmware that I was not using.  I have found 1.11.01.  I will include some links at the end of my post.  Once I updated my firmware in a Windows Environment I was able to connect to Gnomad 2 with out sudo requirements.

Seems to work perfectly at this point in time. 

There are somethings that I want to inform any user that is downgrading there firmware like I have done.  I started out with Firmware 2.21.02 which supports MTP and subscription services threw various DRM providers.   Once I attempted to downgrade it informed me that I was going to loose all data within my Zen and not have the ability to use MTP services.  So if you have files and music that you want to keep you must BACKUP you DATA.  This is the small price that I payed for coming to Linux and have no problems with it.

The links below are where I was able to get the firmware.

The first link is my site and the second link is from Nomads Downloads

Nathan's Nook Zen Micro
[http://www.nathansnook.us/index.php?option=com_content&task=view&id=19&Itemid=32]("http://www.nathansnook.us/index.php?option=com_content&task=view&id=19&Itemid=32")

Nomads Downloads
[http://www.nomadworld.com/downloads/firmware/wma-zenmicro.asp?nProdID=10795&sProd=Creative%20Zen%20Micro]("http://www.nomadworld.com/downloads/firmware/wma-zenmicro.asp?nProdID=10795&sProd=Creative%20Zen%20Micro")

---

### Post by vladdythephotogeek on 2006-06-15
[QUOTE=nathansnook]Zen Micro Update:

As I have said in my last post I would do some firmware hunting and report my results.

I have found another version of the firmware that I was not using.  I have found 1.11.01.  I will include some links at the end of my post.  Once I updated my firmware in a Windows Environment I was able to connect to Gnomad 2 with out sudo requirements.

Seems to work perfectly at this point in time. 

There are somethings that I want to inform any user that is downgrading there firmware like I have done.  I started out with Firmware 2.21.02 which supports MTP and subscription services threw various DRM providers.   Once I attempted to downgrade it informed me that I was going to loose all data within my Zen and not have the ability to use MTP services.  So if you have files and music that you want to keep you must BACKUP you DATA.  This is the small price that I payed for coming to Linux and have no problems with it.

The links below are where I was able to get the firmware.

The first link is my site and the second link is from Nomads Downloads

Nathan's Nook Zen Micro
[http://www.nathansnook.us/index.php?option=com_content&task=view&id=19&Itemid=32]("http://www.nathansnook.us/index.php?option=com_content&task=view&id=19&Itemid=32")

Nomads Downloads
[http://www.nomadworld.com/downloads/firmware/wma-zenmicro.asp?nProdID=10795&sProd=Creative%20Zen%20Micro]("http://www.nomadworld.com/downloads/firmware/wma-zenmicro.asp?nProdID=10795&sProd=Creative%20Zen%20Micro")[/QUOTE]

Sweetness. I'll downgrade (my, how many times do you hear SWEET followed by downgrade anymore?) and let you know how it goes.
Thank you for your pointers.
Paul

---

### Post by thunderduck3141 on 2006-06-16
yes thank you very much
sometimes u need to take a few steps back to go forward

---

### Post by penquin on 2006-06-16
Hey I know you probably tried this but did you also download libnjb-hotplug?  It worked for breezy I see no reason it should not work for dapper.  search the old forums with my loggin name and mp3 players for more details if you did try this already.

---

### Post by vladdythephotogeek on 2006-07-05
[QUOTE=nathansnook]Zen Micro Update:

As I have said in my last post I would do some firmware hunting and report my results.

I have found another version of the firmware that I was not using.  I have found 1.11.01.  I will include some links at the end of my post.  Once I updated my firmware in a Windows Environment I was able to connect to Gnomad 2 with out sudo requirements.

Seems to work perfectly at this point in time. 

There are somethings that I want to inform any user that is downgrading there firmware like I have done.  I started out with Firmware 2.21.02 which supports MTP and subscription services threw various DRM providers.   Once I attempted to downgrade it informed me that I was going to loose all data within my Zen and not have the ability to use MTP services.  So if you have files and music that you want to keep you must BACKUP you DATA.  This is the small price that I payed for coming to Linux and have no problems with it.

The links below are where I was able to get the firmware.

The first link is my site and the second link is from Nomads Downloads

Nathan's Nook Zen Micro
[http://www.nathansnook.us/index.php?option=com_content&task=view&id=19&Itemid=32]("http://www.nathansnook.us/index.php?option=com_content&task=view&id=19&Itemid=32")

Nomads Downloads
[http://www.nomadworld.com/downloads/firmware/wma-zenmicro.asp?nProdID=10795&sProd=Creative%20Zen%20Micro]("http://www.nomadworld.com/downloads/firmware/wma-zenmicro.asp?nProdID=10795&sProd=Creative%20Zen%20Micro")[/QUOTE]

Greetings!

So tell me, how exactly did you downgrade the firmware on the Zen? I have tried on an XP machine but the firmware package *.exe was unable to connect to the player? Do I need (and I suspect I do) need to tell the Zen that it's recieving a new firmware package? And if so, how do I do that? Do you need an XP machine to downgrade?

Hope to hear from you soon. I've been dying to get my Zen to connect to 6.06 but it's been a terribly frusterating exersize in futility.
Paul

---

### Post by Omnios on 2006-07-17
Zen micro uses usb which I think has to be accessed using sudo as root to mount the usb.

---

### Post by Lord Illidan on 2006-07-17
I guess I was lucky I didn't update my firmware... When can we get support for MTP?

---

### Post by mishranurag on 2006-07-17
Hi!
I used Kzenexplorer for this. It appears to have a nice interface. However, most of the time the application hangs or do not load properly. Did anybody try Kzenexplorer? GNomad2 works finr for me, but I liked Kzenexplorer's interface.
Anurag

---

