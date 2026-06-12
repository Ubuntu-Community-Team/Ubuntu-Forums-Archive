---
title: "Back in Ubuntu"
date: 2006-04-14
forum: General Help
---

### Post by hippomofatumas on 2006-04-14
Hi all,

I delved into Ubuntu a while back but couldn't figure some things out. After some unsuccessful attempts at Gentoo's new livecd gui installer, I decided to come back to Ubuntu's simplicity.

So I have a fresh new install alongside XP, with all the updates successful and a reboot. I am at around 800kb/s bandwidth again, I should be at 1.5mb/s, this happened before with Ubuntu and wasn't too tough to solve. I can get most everything else working, firefox 1.5, all the other apps. But one thing is still impossible: MY GRAPHICS DRIVER THINGY!

I have an ati radeon xpress 200 (I hate ati I'm replacing with xfx geforce 6800 gs when I get some money), and had to change xorg.conf to vesa driver in order to install. But now I am at 1280x1024 and things on the screen are fuzzy or jittery, and they just don't look as nice as they should.

When I tried Ubuntu before, nothing really worked like it should have. Can someone please give me a very specific set of instructions that will help me get a normal looking screen? 

Thank you ever so much,
Hippomofatumas

---

### Post by rabidphage on 2006-04-14
driver try this
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)
internet try disabling ipv6
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide#config](https://wiki.ubuntu.com/WirelessTroubleshootingGuide#config)

Give more details on what sort of connection u r on and stuff

---

### Post by zubrug on 2006-04-14
Try the easy ubuntu script, it does the ATI drivers as well as the Nvidia

[http://www.ubuntuforums.org/showthread.php?t=64629](http://www.ubuntuforums.org/showthread.php?t=64629)

---

### Post by hippomofatumas on 2006-04-15
Hi all,

I downloaded the file for easy ubuntu, but honestly I'm so new at this that I don't know what to do with a tar.bz2 or whatever.

Slightly discouraged, I follwed the steps for method 2 on that ubuntu ati site...

AND OH MY GOOD LORD IT IS WORKING!!!

IT LOOKS NORMAL!!!!

AND BEAUTIFUL!!!

---

### Post by hippomofatumas on 2006-04-15
Just tried that IPv6 change and there wasn't a change...

anything else?

again, internet is normal in windows but about half as fast here...

thanks so much, you all just saved my major ubuntu nightmare with the ati thingy.

hippomofatumas

---

### Post by tay on 2006-04-15
what kind of special boot paramaters did you have to give?

did you get the black screen on default boot too?

---

### Post by hippomofatumas on 2006-04-15
special boot parameters?....

well, I selected te ati driver like the page told me to and restarted. xserver didn't. so i did the usual sudo dpkg-reconfigure xserver-xorg and changed it to vesa again. but when i went back to the site and finished up all that it told me to do, it worked.

i don't know if that was an answer to your question.

um, so now there's a couple other things.

1: i want my "windows media center" partition to be the default in grub.
2: do i need the older ubuntu linux kernels to boot in to? can i remove them?
3: although i know i don't need them i got aegis and clamav. how they hell do i use them?
4: xp and all the clocks in my house say its 3:05 am. ubuntu says 1:50 am. i thought i had the time set up correctly. any change i make in ubuntu changes xp. how do i sync them up?
5: i still need a full bandwidth internet connection.

thanks a million,
hippomofatumas

---

### Post by hippomofatumas on 2006-04-15
I have accomplished goal number 1.

The clock synchronization is most important.

---

### Post by hippomofatumas on 2006-04-16
Well,

I managed to get the two clocks within a minute or two of each other at the right time. 

Bit annoying.

Okay, I just looked at my Ubuntu clock and the seconds are going by almost twice as fast as they should be. Weird.

Any ideas?

---

### Post by hippomofatumas on 2006-04-16
I found another thread that addressed the quick clock issue. Had to tack on noapic nolapic at the end of the kernel line in grub's menu.lst or something. Now the clock is at normal speed. But the clock's are 4 hours apart I think. They're both correctly set at -5:00 GMT Eastern US Time. I'm in Florida. I selected the Havanna time zone in Ubuntu I believe. But the system clock keeps going back and forth. I need them to both read the same time!

Help please!

---

### Post by hippomofatumas on 2006-04-18
Hi all,

Everything is fixed, pretty much. I installed a bunch of stuff with Automatix and some with Add Applications, and now I get this error message whenever using synaptic or trying to update?

E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1

What does it mean and what do I do?

---

### Post by z_diver on 2006-04-18
[QUOTE=hippomofatumas]Hi all,

Everything is fixed, pretty much. I installed a bunch of stuff with Automatix and some with Add Applications, and now I get this error message whenever using synaptic or trying to update?

E: /var/cache/apt/archives/lilypond_2.6.3-9~breezy1_i386.deb: subprocess pre-installation script returned error exit status 1

What does it mean and what do I do?[/QUOTE]
Good to hear you are making progress.  Once you get your Ubuntu setup the way you like, it's pure joy to use.  Usually output of status=0 means everything went fine and anything else is acknowledgement of an error.  So 1 means an error occured.  Seems like the deb package downloaded with lilypond is not installing correctly.  Have you tried romoving it?  or reinstalling it with synaptic?  Maybe something happened to the download --possibly while tinkering with the network connection or something?  Not sure, but worth a try.

---

