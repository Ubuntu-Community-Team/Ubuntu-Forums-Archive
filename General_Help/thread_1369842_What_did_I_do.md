---
title: "What did I do?"
date: 2010-01-01
forum: General Help
---

### Post by Capgains on 2010-01-01
I decided that my New Year's resolution would be to try Linux on my laptop that I was retiring from business work.  It would become my new "hobby" machine.  

Last night I installed Ubuntu onto the laptop.  It is 4 or 5 year old, Dell Inpiron 6000 with an internal wireless card, I believe the card is an Intel Pro/wireless 2200BG.  At least that is what it shows in the network cards under device manager.  

I installed Ubuntu as a dual boot on the machine with the existing Xp Home.  After the installation, everything looked fine except there was not network connection, so I clicked on the wireless symbol at the top of the page, and proceeded to select my home network, and enter the security key as I have done with all my wireless devices.  I was told the connection was made, and the meter shows a strong signal. 

When I start Firefox, the home page is the Ubuntu 9.10 homepage, and I assume that is cached.  If I enter google.com into the address bar.  It will say that it is looking, but will time out.  This happens with almost any address I enter.   The Ubuntu launchpad did work, and was able to request to send an activation link to my email address.  Although I had to get the email on another windows box since I can't get Firefox to find Google Gmail right now.   

Any ideas on what to do?  

I have come across several pages of help manuals that suggest I enter this command or that.... Where do you have the ability to enter commands on Ubuntu?  Is there a prompt somewhere?

I am not a programmer, but I'm not a helpless slouch on computers.  I can follow directions.  :)

p.s.  Am I right that Ubuntu is the system, but the desktop I am using is actually Gnome?



Danno

---

### Post by 73ckn797 on 2010-01-01
Command prompt type procedures are performed using Terminal. It is found under Applications/Accessories. Found on top right menu bar.

You may want to look under System/Administration/Hardware Drivers and make sure there are no drivers recommended for the wireless card. Typically you will only find drivers for your video card there.

If you wireless router is set for WEP I have seen many issues related to that encryption. Try changing to a WPA setting and see what happens.

Other info:
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
and
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) (read the sticky notes)

---

### Post by Bradj47 on 2010-01-01
Sounds to me like you aren't resolving domain names properly, which means your nameservers are wrong. Look up the name of your nameservers by whatever means you know. If you don't know any, try calling your ISP. They should be in the form of IP addresses. Once you get them, go to **Applications -> Accessories -> Terminal**. Type sudo **gedit /etc/resolv.conf**. You will be asked for your password. Type your password and the text editor will come up. Add the nameservers to the bottom of the document or using this format: 

```

nameserver xxx.xxx.xx.xxx

```

Add as many lines as you need. Once you're done, save the document and close. Try loading a webpage in Firefox again. 

Good luck, 
Brad

---

### Post by Capgains on 2010-01-01
Thanks for pointing me to the Terminal for inputing commands.

Okay, I checked the drivers, and there is nothing there... as you predicted.

I really don't want to change the wireless security protocol from WEP since this would be the only one of 7 devises in the house that can't seem to work.

Brad, I looked at the resolv.conf file, and the two nameservers I have are already in place in there.

Just a bazaar situation. The connection shows a good 54 mps, but it is as if the browser has a bandwidth problem.  Many pages will actually put the header of the site at the top of the page like it made contact, and then.... it will spin and spin and spin.

---

### Post by Leppie on 2010-01-01
do you have the same issue if you connect the laptop with a cable to the router?

---

### Post by Capgains on 2010-01-01
Well, the Firefox is up and running, but to get it to work, I hope I didn't sacrifice, security or something else.  If I go into Firefox via the address bar, type in about:config, agree to the warning, and then proceed to disable the network dns IPv6.... it works fine.   However, I hope I didn't just open my fly to some other kind of problem here.

---

### Post by davec64 on 2010-01-01
Capgains, that's what I have to do with my system.
By default IPv6 is enabled in Firefox, so whenever it tries resolve an address it does it by IPv6 first then IPv4. It sounds very much like yours was timing out before it got to resolving via IPv4.
Disabling IPv6 is a good option unless you're on an IPv6 network. It will speed up Firefox!

---

### Post by Groundswell on 2010-01-01
capgains, i know you don't wanna change your wireless security like you said, but everytime i see this i try to let people know, WEP is extremely weak, i can crack it in under 5 minutes, but wpa(2) actually stands a fighting chance, especially if you don't use word passwords and use some numbers and letters. if your network's in a remote location with few neighbors then never mind :P

---

### Post by Capgains on 2010-01-01
Thanks, I'll take that into consideration... We are pretty remote.  It's not quite the edge of the world, but you can see it from here :)

---

