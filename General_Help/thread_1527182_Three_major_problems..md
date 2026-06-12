---
title: "Three major problems."
date: 2010-07-09
forum: General Help
---

### Post by dillandriskell on 2010-07-09
I have three major issues right now that are making using Ubuntu 10.4 a nightmare. If anybody can help me with these or provide links to where I can get these issues fixed I would be eternally grateful.

First, every now and then it just refuses to connect to the internet. My ethernet connection is still displayed as working, and I know very well that it works. But my browser will just sit there and try to display even the simplest of pages to no avail. I can usually fix this by rebooting once...sometimes three times.

Second, my flash just broke and I haven't the slightest clue why. I shut my computer down, went and did something for like an hour, came back and started it back up, and now some adobe flash programs work but most don't. Firefox tells me I have missing plugins, so when I tell it to install flash it tells me it's already there.

Usually if I have this much trouble with Ubuntu, I just reinstall the system. But it looks like Ubuntu's not even going to let me do that...I have a half-terabyte encrypted external hard drive that Ubuntu's just decided doesn't exist. I plug it in, it lights up like everything's working...then nothing. It doesn't even appear in the "sudo fdisk -l" menu. Now I can't even transfer my files to do the system reinstall, nor can I back up my files that are very important to my job. And I know it's not the hard drive, as it works perfectly fine with my laptop which also has 10.4.

I'm just completely lost at this point. I've been using Ubuntu since 8.10 and I've never had this much trouble with a release. How can I fix all this?

---

### Post by claracc on 2010-07-09
For the second problem , the flash one, you can use an addon made by lovinglinux in order to install the appropriate flash version, the addon's name is flash-aid, here there is  the link:

[https://addons.mozilla.org/es-ES/firefox/collection/lovinglinux](https://addons.mozilla.org/es-ES/firefox/collection/lovinglinux)

---

### Post by Fastjack77 on 2010-07-09
Hi Dilan,

Can you give us more details about your system and your network? Is Ubuntu connected directly to your modem-cable, using DHCP from your ISP? If so, I'm having this problem and have to disconnect the power from the cable-modem, reconnect the power, and try to connect again from the desktop for it to work.

---

### Post by Akiviri on 2010-07-09
Hi

I'm not sure this will help much - but thought I'd throw it out there as a suggestion you might look into. 

First - "sudo apt-get remove --purge firefox" -or- "sudo apt-get autoremove firefox"

Second - "sudo apt-get install firefox"

Try that to get back online along with/in place of the former suggestion with your modem. Sounds like something happened with firefox along the way - make SURE you use the master password option even if you don't save your passwords to websites. You may also want to look into the 'no-script' add-on for firefox.

Then get a Ubuntu One acct. (free) - "www.one.ubuntu.com"

You can upload your files there for free up to 2GB - anything over that you'll have to pay a small fee...but if you can't get into your external and you need the files....

Then you should be able to reinstall.

Once you are up and running again - I would advise enabling your firewall via firestarter, or the simpler 'firewall configuration tool' found in the software center. Or open a terminal and type " sudo ufw enable " Once it's on, unless you are getting direct attacks and need to configure special rules (which are accomplished through the two aforementioned programs) - you should be fine.

Not sure that will help, as I don't know more than what you've told us - but I hope that helps you some somewhere :)

Good Luck

---

### Post by Braik on 2010-07-09
Hi, I will give you another suggestion because it seems that you often do a format and cleanly install a new system.
 
Just a little lecture about the utility of partitions:
[http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html](http://www.cyberciti.biz/tips/the-importance-of-linux-partitions.html)
 
There is a way to have a second HD (or in the case of a single HD, a separate partition) where you can mount your home folder, in that case you just format your system partition install the system and after that you just remount your home folder and all is just back, without any pain. Just some little tutorials of how to do this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
 
 
I have this in my system and I was very happy in the period of the lucid release.... ;)

---

### Post by lovinglinux on 2010-07-09
For the network problem, try to disable ipv6.

Make sure your connection settings are correct (e.g., Tools -> Options -> Advanced -> Network / Connection -> Settings). Additionally, disable ipv6 on Firefox Preferences, by setting the **network.dns.disableIPv6** preference to **true**.
[LIST=1]
[*]Type **about:config** in the address bar, press Enter.
[*]Find network.dns.disableIPv6 in the list.
[*]Right-click -> Toggle.
[*]Restart Firefox and try again.
[/LIST]
You can also disable ipv6 on the system. See [How to disableIPv6 in Karmic Koala and Lucid Lynx](http://wojox.homelinux.org/?p=46)

For the flash problem, install my extension [FLASH-AID](https://addons.mozilla.org/en-US/firefox/addon/161939) as already suggested.

---

