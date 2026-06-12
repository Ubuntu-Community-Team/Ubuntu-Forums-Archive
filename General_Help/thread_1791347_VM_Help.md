---
title: "VM Help"
date: 2011-06-26
forum: General Help
---

### Post by Anniemoose98 on 2011-06-26
Hi all,


I have a Windows 7 32 Bit VM running in Virtual Box on 11.04. I have a USB Wireless card from Belkin. On my VM I have the filter for all devices set, but Win. 7 wont see my WiFi card so I can watch Netflix. 


Any help is appreciated.

Anniemoose98

---

### Post by gdonwallace on 2011-06-26
If you are running the VirtualBox from the repos, that may be the problem.  I would suggest uninstalling it, going out to virtualbox website and download the newest version from them.  There is a file called guestadditions.  You will need to mount this as a CD and then run the program from within win 7.  This will allow your USB and video card to work.

---

### Post by Anniemoose98 on 2011-06-26
I used the version from the VB website...

---

### Post by Anniemoose98 on 2011-06-26
ok, installed Guest Editions, still nothing.

---

### Post by Anniemoose98 on 2011-06-26
bumpin it to the top

---

### Post by Anniemoose98 on 2011-06-26
I need to do this before the end of the day...any help?

---

### Post by haqking on 2011-06-26
Do you want to mount the USB device as wireless in the VM or you mean just access the internet connection from your wifi in the VM.

What network settings do you have ?

Are you using NAT, Bridged, internal etc ?

[http://www.virtualbox.org/manual/ch06.html](http://www.virtualbox.org/manual/ch06.html)

---

### Post by coldraven on 2011-06-26
Did you add yourself to the vboxusers group? In System>Admin>Users and groups.
You will have to reboot or logout and back in for it to take effect.

---

### Post by Anniemoose98 on 2011-06-26
@Haqking: NAT
@coldraven: done

---

### Post by Anniemoose98 on 2011-06-26
Also, I just want to use my USB wifi card in the windows VM so I can watch netflix and browse the internet

---

### Post by haqking on 2011-06-26
> **Anniemoose98 said:**
> Also, I just want to use my USB wifi card in the windows VM so I can watch netflix and browse the internet

So your USB wifi is working in your host, you start up your virtual machine and it iset to use nat but you have no connectivity ?

what do you get when you ping from within your VM ?

---

### Post by Anniemoose98 on 2011-06-26
It doesn't even detect the card, just the Intel Ethernet controller. I just don't understand it... It works in Ubuntu, but doesn't in Windows...

---

### Post by Anniemoose98 on 2011-06-26
ok, when pinged, it gets responses from the Intel 10/1000 Ethernet, but not the card...

---

### Post by haqking on 2011-06-26
> **Anniemoose98 said:**
> It doesn't even detect the card, just the Intel Ethernet controller. I just don't understand it... It works in Ubuntu, but doesn't in Windows...


ok so yes its working in Ubuntu and so using NAT in your VM it should use your wifi on host as a connection in the VM normally as eth0 even though it is not hardwired

what is result of ipconfig /all and a ping in your windows 7 VM ?

can you upload a screen capture of both ipconfig /all, ping to any internet address or your router and a network settings page from your Virtual machine

---

### Post by Anniemoose98 on 2011-06-26
It pings to the Ethernet, but wont to the wifi card

---

### Post by Anniemoose98 on 2011-06-26
also, ipconfig sees the ethernet only, too

---

### Post by Anniemoose98 on 2011-06-26
WTF... I don't know what I did... but all of a sudden the thing started working...

---

### Post by Anniemoose98 on 2011-06-26
and it is broken again... please help!!!!!

---

### Post by haqking on 2011-06-26
it pings to the ethernet ?

your ethernet on your VM is your wifi on your host, it is not usually seen as wifi but as eth0 in a vm

---

### Post by haqking on 2011-06-26
> **Anniemoose98 said:**
> and it is broken again... please help!!!!!


i am trying to so i refer you back to my original request to show me the images.

you will not see wireless connection in ipconfig, your ethernet from your VM will be using the wireless connection that is all.

if you have your network settings set up that way that is

---

### Post by Anniemoose98 on 2011-06-26
Ok, now windows sees that there is a "wire" attached, but it asks for a username and password from my isp... what should I put?

---

### Post by haqking on 2011-06-26
i am trying to help here but i think you are getting confused.

Please supply me screen captures of information so i can see better what is going on.

at this point i dont have enough information

---

### Post by Anniemoose98 on 2011-06-26
[https://picasaweb.google.com/106224396136883723533/UbuntuShots?feat=directlink](https://picasaweb.google.com/106224396136883723533/UbuntuShots?feat=directlink)

---

### Post by haqking on 2011-06-26
> **Anniemoose98 said:**
> [https://picasaweb.google.com/106224396136883723533/UbuntuShots?feat=directlink](https://picasaweb.google.com/106224396136883723533/UbuntuShots?feat=directlink)

you might want to take a look at the images you uploaded.

on every one all i can see is the take screenshot menu ;-)

just press the print screen on your keyboard and save it or paste into image viewer and then save it and add it as a attaqchment to your post.

---

### Post by haqking on 2011-06-26
i need to see the VM network settings from within your host

then in the VM your ping and ipconfig results from command prompt

not the network settings screen GUI

---

### Post by Anniemoose98 on 2011-06-26
[https://picasaweb.google.com/106224396136883723533/UbuntuShots2?feat=directlink](https://picasaweb.google.com/106224396136883723533/UbuntuShots2?feat=directlink)

---

### Post by haqking on 2011-06-26
can you ping an external address such as google ?

---

### Post by Anniemoose98 on 2011-06-26
I hope that was what was needed...

---

### Post by Anniemoose98 on 2011-06-26
Ok, pings to google, but when I open up IE, it attempts to connect through the WAN miniport (PPPOE)

---

### Post by Anniemoose98 on 2011-06-26
ok, it finally decided to work...

---

### Post by haqking on 2011-06-26
> **Anniemoose98 said:**
> Ok, pings to google, but when I open up IE, it attempts to connect through the WAN miniport (PPPOE)


mmm can you post an image of that output.

it sounds like it is trying to connect directly thorugh a modem device connected directly to broadbadn.

mmm i cant remember windows 7 interface and my VM's are in the middle of a copy.

in the Control Panel choose Internet Options.  

choose the Connection tab and make sure that "Never use Dial-Up" is selected.  

click on the LAN Setting button and make sure Proxy Server is unselected.

---

### Post by haqking on 2011-06-26
> **Anniemoose98 said:**
> ok, it finally decided to work...


decided to or something changed ?

if so what was it,. post it here if you know and mark the thread as solved so others no in the future if it is solved.

---

### Post by Anniemoose98 on 2011-06-26
I'm not sure. I shut down the VM, checked this thread, logged back on my vm and windows update opened and installed 86 updates...

---

