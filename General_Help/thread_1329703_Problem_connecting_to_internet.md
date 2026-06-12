---
title: "Problem connecting to internet"
date: 2009-11-17
forum: General Help
---

### Post by Pesky_Programmer on 2009-11-17
I can not get ubuntu to recgonize my usb modem without first loading windows with the modem inserted. I can connect to the Internet no problem but i would like to be able to connect to the Internet using ubuntu only.

Any help would be greatly appreciated.

---

### Post by hal8000 on 2009-11-17
You need to provide some basic info:

Make / model of your USB modem
Ubuntu version

With the usb modem plugged in type:

sudo lsusb

---

### Post by Pesky_Programmer on 2009-11-17
sorry  for making it so brief but my last post went ignored so I made this one shorter hopeful  that alone would attract more attention here is my original post.

I am running a dual boot with Karmic Koala and windows xp. My modem is Novatel Wireless modem through the Verizon network. My modem will only work after I have booted windows first with the modem inserted. I have experienced this same problem on my previous install of ubuntu Jaunty Jackalope. 
I have tried asking this question on IRC and no one seamed to have the answer. The closest anyone came to helping me was to tell me to use dialler programs which will not help as I can already connect to verizon and have in ubuntu i just want to be able to connect to the Internet with out using windows. 

btw sudo isusb does not work

---

### Post by Pesky_Programmer on 2009-11-27
[FONT=Times New Roman][SIZE=3]I have recently done a fresh install of Karmic on my Gateway MX7527 laptop, along side my currant Windows XP install. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]However I have been unable to get Ubuntu, even in my last install of Jaunty, to recognize my usb modem on its own. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]In order to go online using my modem I must first boot Windows with the modem inserted, just sitting at the login screen does the trick. I then reboot to Ubuntu with the modem still inserted and I can go online no problem. But if I were to remove the modem while running Ubuntu I would have to reboot into windows to make the modem work again and then go back to Ubuntu. This makes keeping Ubuntu up to date very annoying as I have to boot my computer twice just to surf the web in Ubuntu. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I have come to two conclusions either I need a driver similar to the one used by windows for Linux, or Ubuntu simply can’t detect hardware properly. I have been unable to find an answer to this and if anyone could point me in the right direction it would be greatly appreciated.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]For all those who want to know, [COLOR=black][FONT=Times New Roman]not that I think it makes a difference [/FONT][/COLOR], I am using a Novatel Wireless modem that connects to the verizon network.[/SIZE][/FONT]

---

### Post by sanderj on 2009-11-27
Dupe of your post one week earlier: [http://ubuntuforums.org/showthread.php?t=1329703](http://ubuntuforums.org/showthread.php?t=1329703)

---

### Post by Elfy on 2009-11-27
Closed - that is 5 threads on the same issue. Please do not post duplicates.

Open thread is [http://ubuntuforums.org/showthread.php?t=1329703](http://ubuntuforums.org/showthread.php?t=1329703)

---

### Post by sanderj on 2009-11-27
> **Pesky_Programmer said:**
> 
 
btw sudo isusb does not work

That's not what hal8000 adviced you to do. Read his advice again. Better: copy paste his advice.

---

### Post by cariboo on 2009-11-27
Please don't double post on the same subject, I have merged your two threads.

---

### Post by Pesky_Programmer on 2009-11-27
I am sorry for spamming your forums but I hope you can understand my frustration as I am unable to get ubuntu to preform a task as simple as connecting to the Internet without being dependent on Microsoft Windows XP. It would also appear, after scanning your forums, it is a common problem that people can't get ubuntu to recognise their hardware as it should and that if there is a simple solution such as a device manager, like in windows, there should be more documentation on it to avoid disgruntled users.

I was able to get sudo lsusb to work. It must of been an error on my part sorry about that. Here is the relevant output.

>  Bus 003 Device 002: ID 1410:6000 Novatel Wireless I hope now that I have gotten more attention that this problem will have a quick resolution.
If you need any more information on my hardware let me know; however I believe I have posted sufficient information about my current problem.

---

### Post by sanderj on 2009-11-27
In the upper right corner, after you click on the NetworkManager applet, does it show something like "Mobile Broadband"? Can you check "New Mobile Broadband"?

---

### Post by Pesky_Programmer on 2009-11-27
Yes that is how my Internet connection appears and when I click it I get connected no problem. The first time I was able to connect to the Internet in Ubuntu it loaded up a wizard that walked me through the configuration of my mobile broad band. Ever since then my connection when it is available comes up as Verizon Connection. As a matter of fact im using Ubuntu to reply.

My problem is that I must boot Windows XP with the modem inserted first before Ubuntu will register that there is a connection available to connect to.
Also when I type in sudo lsusb, whether the modem is working or not, I can see my modem. I just cant see the associated connection unless I  have booted Windows XP first.

I hope this explanation has cleared up my present situation and thanks for reading my post.

---

### Post by pyrofreak99 on 2009-11-27
actually i am having the same problem everytime i boot into ubuntu i cant get to the internet but when i go through vista i have no problems in that area whatsoever  



so can anybody help us out?

---

### Post by Pesky_Programmer on 2009-11-27
Pyrofreak99. I will assume you are also using a mobile broadband card like I am. Does your card have any memory storage portion to it. 

Mine has a slot for a removable memory card and a read only portion that contains the windows drivers and the VZAccess manager, also a windows program. 

The memory card slot is empty and always displays under computer whether the modem works or not. The read only portion with VZAccess manager only becomes visible in Ubuntu when the modem is inserted after Ubuntu has already been loaded. This coincides with my modem not working in Ubuntu.
 
I don't know if this has anything to do with the problem but at this point I don't have much to go on.

---

### Post by pyrofreak99 on 2009-11-27
no actually im not using a verizon internet card im hooked directily into a internet modem

and when i log in it wont connect to the internet


im using a windstream modem

---

### Post by Pesky_Programmer on 2009-11-27
So when you said you have the same problem you mean you can only connect to the Internet, in Ubuntu, directly after having Windows loaded and the modem connected/enabled.  
I'm just trying to clarify both of our situations so that others reading may better grasp the problem and hopefully help us figure it out.

---

### Post by sanderj on 2009-11-28
> **Pesky_Programmer said:**
> 

My problem is that I must boot Windows XP with the modem inserted first before Ubuntu will register that there is a connection available to connect to.
Also when I type in sudo lsusb, whether the modem is working or not, I can see my modem. I just cant see the associated connection unless I  have booted Windows XP first.



If you boot Ubuntu *without* first booting Windows:
- what does "lsusb" say? Post complete output here
- Is there a extra disk drive available via Places -> Computer, Places -> System, or just on the desktop?
- Post the complete output of mount here.
- what does NetworkManager say? Does it have Mobile Broadband?

---

### Post by Pesky_Programmer on 2009-11-28
When my modem is working, meaning I have loaded Windows XP first, this is what lsusb outputs.
 

> Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 1410:6000 Novatel Wireless  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  


 I have four usb ports and at the time of me using this command my mouse receiver, cooling pad, and my mobile broadband, Novatel wireless, modem are plugged in. Thats three of my four usb ports in use.
 

 If I were to then unplug the modem, it would read...
 

> Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 


and if I were to plug it back in  
 

> Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 003: ID 1410:5030 Novatel Wireless  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 


While getting this output I noticed that every time I unplug and plug it back in the device # is increased by one. I don't know if that means anything but figured it couldn't hurt to point it out.  
 


 Lastly, and answering Sanderj, I shutdown my computer inserted the modem and booted Ubuntu first, not loading Windows, and here is the output I got.
 

> Bus 002 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 1410:5030 Novatel Wireless  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 

---

### Post by sanderj on 2009-11-28
Can you please answer my four questions in post [http://ubuntuforums.org/showpost.php?p=8400372&postcount=16](http://ubuntuforums.org/showpost.php?p=8400372&postcount=16)

---

### Post by Pesky_Programmer on 2009-11-28
As a reference here is how my computer looks with out the modem
 

 

 

 See first attachment 

 

 

 

 

 If I boot Ubuntu only here is how my mounted drives look. This is when I **can not** connect to the Internet through Ubuntu.






See second attachment 

 







 Reading from left to right; My 120 Gb HD containing Windows XP and Ubuntu.  
 

 The CD Drive is the read only portion of my usb modem, this contains Verizons VZAccess manager a networking tool for windows and generic drivers for the modem (again windows only).  
 

 The CD/DVD drive is my empty CD/DVD drive that came with my laptop.
 

 The Novatel MMC storage is the empty microSD Memory Card slot.
 

 Finally the file system is Ubuntu of course, and is contained on the same Hard Drive as Windows.
 

 If I remove the Drive and reinsert it after Ubuntu has booted my mounted drives look like this
 



See third attachment



 

 Note that the read only portion of my modem is missing other then that its the same as before.

---

### Post by Pesky_Programmer on 2009-11-28
I am attempting to post the screen shots as they did not work in my last post. I am sorry for the delay in answering all of your questions I am just trying to answer them as best as I can.

---

### Post by Pesky_Programmer on 2009-11-28
This is how my connection shows in the network connections window. Ubuntu still has the configuration saved in Mobile Broadband it just cant see the connection to connect to it.

---

### Post by sanderj on 2009-11-28
Can you unmount the VZaccess (and the other Novatel memory) drive; in Nautilus, right click to select Unmount? 

After that, can you use the Network Manager's Mobile Broadband connection? Can you post 'lsusb' after the unmount?

---

### Post by Pesky_Programmer on 2009-11-28
[COLOR=black][FONT=Verdana]While attempting to load Ubuntu to try your advice I began to have problems with Gnome. ](*,)[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Four times in a row Ubuntu has taken several minutes to display my desktop image and when it does it looks like the below picture. I have no panels and thus am unable to perform some of the tasks necessary to continue trouble shooting the problem. The only thing I have changed recently was that I added the weather icon to the top panel. I even tried failsafe Gnome and got the same result. The second picture shows the end now window that appeared when I tried to reboot. This is how I know Gnome was the culprit.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Is there some work around or should I try downloading KDE as a substitute GUI?[/FONT][/COLOR]

---

### Post by Pesky_Programmer on 2009-11-28
I tired Ubuntu again and it seams to of loaded up fine this time. I will ignore the problem Gnome was having before for now so long as it does not come back.

I was able to boot my computer from being turned off, directly to Ubuntu with the modem inserted before hand. After everything finished loading I  went to Computer and tried going to eject for the VZAccess drive. When I did this both the VZAccess icon and the Novatel one disappeared. A second later the Novatel one came back and I was able to connect to the Internet. This is the first time I was able to connect to the Internet in Ubuntu without first loading Windows XP. :D

Thanks for the help I am really grateful hopefully as I learn more about Ubuntu I might be able to return the favour later.

---

### Post by sanderj on 2009-11-28
Good. Exactly like this experience on [http://elf.org/node/32](http://elf.org/node/32)
> 

The puzzle comes when you connect as a USB device to Ubuntu. It identifies as a cdrom drive with ID:

Bus 006 Device 005: ID 1410:5041 Novatel Wireless

At this point, I thought to google the problem and found a Verizon forum post with the magic answer to my puzzle. If you eject the VZAccess Manager volume which mounts as device 1410:5041, then it comes back and connects as a wireless modem / cdrom with ID:

Bus 006 Device 007: ID 1410:6000 Novatel Wireless

The network manager picks it up as "Auto Mobile Broadband (CDMA) connection" and you can make a 3G connection by simply selecting it from the network manager menu. 



So: problem solved? If so, mark this thread SOLVED.

---

