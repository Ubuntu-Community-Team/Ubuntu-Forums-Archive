---
title: "Menus not available on Ubuntu 10.10"
date: 2010-11-05
forum: General Help
---

### Post by adityachs on 2010-11-05
Hi ,

I am new to Ubuntu. Recently I installed Ubuntu 10.10 Maverick on my HP notebook
(Intel core2 CPU T5600@1.83GHZ)

I facing lot of initial hiccups in using Ubuntu as i came from Win XP.

I am not able to see any menus in the home screen. No right click is available on desktop. While searching in forum, I came to know that there will be menu in the desktop. and also run option(Alt+F2 or so). But I don't have any menu except top bar with Ubuntu Logo and status bar and Launcher Bar. Alt+F2 is not working.

I am trying windows kind of desktop/menus/look and feel. I installed Cairo-Dock. which has menu item "application menu".  But it seems my system struck due to this.

I have another system with XP OS. Both are in same lan. Inorder to communicate between both I tried xipmsg. I cant find the application under applications launcher. From terminal if i give this command, small gui is opened. where there are no users found :(.  also printing this error at closing. "XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1844 requests (1844 known processed) with 0 events remaining."

Then I installed ipmsg for windows using WINE.  Its giving 3 errors in the startup and my system name only available in the users list :(. When I press Refresh, that name also vanishes. Then I installed Genome IPmsngr, where I could not find single entry similar to xipmsngr. 

  sometimesstatus icons of LAN/wireless &  ipmsngr coming out of status bar and showing below the status bar.

Also getting following errors while hibernate.
btusb bulk complete: hci0 urb efdc5280 failed to resubmit(1).

I request you to help me resolving the above said issues.

/Aditya

---

### Post by ajgreeny on 2010-11-05
I suspect from the apparent disaster you have seen that the iso file, or the burned CD or USB is corrupt.  You should check the md5sum of the iso file if you downloaded it with a browser, though if you got it from a torrent, it should be fine, as the bit-torrent applications all check the downloads as they come down.

You can find the md5sums of all the iso files at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
and how to find them with linux, Mac and windows at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the iso file is good, burn it again at the slowest speed possible, and while doing so do not use the computer for anything else.

---

### Post by adityachs on 2010-11-06
Hi,

If you are talking about Ubuntu ISO, I have downloaded from [http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook) ( I donno I have to download Desktop version or Notebook version, so I chose Notebook). 

I followed the same instruction given for installation. Unfortunately I lot all my exiting files and Winxp OS due to installation , which is a different story.

I used Universal USB Installer for installer from ISO. Now I don't have the ISO to check also.
 
But I dont think its due to corrupt installer. Today when I revisited the download page, I could see the image, which is similar to my desktop.
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/U3_unity_small.jpg[/IMG] 

But I want to customize my desktop, where I think I am failing.

/Aditya

---

### Post by foxmulder881 on 2010-11-24
> **adityachs said:**
> Also getting following errors while hibernate.
btusb bulk complete: hci0 urb efdc5280 failed to resubmit(1).

I just started using the hibernate function and I also get this error message upon going into and coming out of hibernation.

Hibernation function works, but what is this message?

---

