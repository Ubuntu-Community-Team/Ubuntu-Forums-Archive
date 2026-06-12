---
title: "Before I Install"
date: 2012-06-03
forum: General Help
---

### Post by Googleness on 2012-06-03
Dear Ubuntu Community,
I've recently learned that using Wine or wine through PlayOnLinux I'll be able to play some Video games on linux itself and after veryfing on the WineDB site I've learned that all of the Games Currently installed on my system are ranked gold or platinum and working flawlesly.

So I've decided to install Ubuntu 12.04 (64bit) on my new pc which currently running Windows 7 64bit.

Before I'll install the system I would like to ask you a few questions and prepare myself so the expiriance will be smooth as possible...

0. this is my PC components list:
```

Intel Core i5 2500K
Gigabyte GA-Z68X-UDP-B3
G.Skill Sniper 2X4GB DDR3 1333Mhz PC3-10666 Kit
Gigabyte GTX550 Ti OC 
LG GH24NS
ASUS Mini Bluetooth Adapter
Logitech Webcam C270
Razer Lachesis 5600DPI Gaming Mouse 
Razer Sphex Mouse Pad
Thermaltake Challenger Gaming Keyboard
Advice PRD 750
Plantronics GameCom 367 Headset
Western Digital Blue Caviar 1TB
Coolermaster 690 II Plus Black ATX Case
Corsair TX 750W PSU
Noctua NH-D14 CPU Cooler
Samsung M2 Portable 500GB Externel HDD
Samsung SyncMaster B2330HD 23" TV/Monitor 

```1. there are any known issues with drivers or functionality of any components currently in use in my PC?
2. There is a tool for configuring the keyboard and the mouse like the ones coming with the drivers by TT and RAZR on windows?
3. there is any tool for configuring my UPS? currently I have program running at the background which manages what to do in case of power failure.
4. for gaming purpose and HD movies does the proprietary or free drivers are recommended?
5. what is a recommended partition scheming for 1TB HDD this days? and which file system is recommended for each partition?
6. My smartphone is the Motorola Razr XT910 which uses a software called motocast to stream my files directly to my phone as long both pc and the phone are connected to the internet. is there an equivalent to this software for Ubuntu? also there is a software which allows to back the Motorola razr on Ubuntu? 
7. how's OnLive this days on Ubuntu? anyone uses it (through wine of course) ? 
8. any further tips will be appreciated as the last time I've worked with Ubuntu was on 2008.. :P

Thanks for the help!

---

### Post by idoitprone on 2012-06-03
> **Googleness said:**
> Dear Ubuntu Community,
I've recently learned that using Wine or wine through PlayOnLinux I'll be able to play some Video games on linux itself and after veryfing on the WineDB site I've learned that all of the Games Currently installed on my system are ranked gold or platinum and working flawlesly.

So I've decided to install Ubuntu 12.04 (64bit) on my new pc which currently running Windows 7 64bit.

Before I'll install the system I would like to ask you a few questions and prepare myself so the expiriance will be smooth as possible...

0. this is my PC components list:
```

Intel Core i5 2500K
Gigabyte GA-Z68X-UDP-B3
G.Skill Sniper 2X4GB DDR3 1333Mhz PC3-10666 Kit
Gigabyte GTX550 Ti OC 
LG GH24NS
ASUS Mini Bluetooth Adapter
Logitech Webcam C270
Razer Lachesis 5600DPI Gaming Mouse 
Razer Sphex Mouse Pad
Thermaltake Challenger Gaming Keyboard
Advice PRD 750
Plantronics GameCom 367 Headset
Western Digital Blue Caviar 1TB
Coolermaster 690 II Plus Black ATX Case
Corsair TX 750W PSU
Noctua NH-D14 CPU Cooler
Samsung M2 Portable 500GB Externel HDD
Samsung SyncMaster B2330HD 23" TV/Monitor 

```1. there are any known issues with drivers or functionality of any components currently in use in my PC?
2. There is a tool for configuring the keyboard and the mouse like the ones coming with the drivers by TT and RAZR on windows?
3. there is any tool for configuring my UPS? currently I have program running at the background which manages what to do in case of power failure.
4. for gaming purpose and HD movies does the proprietary or free drivers are recommended?
5. what is a recommended partition scheming for 1TB HDD this days? and which file system is recommended for each partition?
6. My smartphone is the Motorola Razr XT910 which uses a software called motocast to stream my files directly to my phone as long both pc and the phone are connected to the internet. is there an equivalent to this software for Ubuntu? also there is a software which allows to back the Motorola razr on Ubuntu? 
7. how's OnLive this days on Ubuntu? anyone uses it (through wine of course) ? 
8. any further tips will be appreciated as the last time I've worked with Ubuntu was on 2008.. :P

Thanks for the help!

i can only answer a few

4. yes propriety drivers are recommended because nouveau are still having problems with nvidia clock support. Mesa stack only support opengl 2.1 sighhhhh

5 the recommended partition scheme is to have a /home, /root and /swap

/ root is for system file
/home is for you user configurations files
/swap is for hibernating
swap should be near the front then root then home

good size for root 10GB-20GB 
/swap must be equal to amount of ram you are using + swap
Since you have like 8 GB of ram. I recommend 6GB swap because 8 GB of swap is excessive. Chance of you using all 8GB ram and then hibernating is very slim
Unless you want to be safe, then make a 8GB swap partition

for home partition as big as you want it since this is where you will save you personal files


after you install remember to change swappiness to 0, because swapping will make your system slower

You can put this all on an extended partition so it only consumes 1 primary partition

wine support depends on games. It is a hit and miss sort of thing

---

### Post by mikewhatever on 2012-06-03
1.While waiting for replies, make a Live CD/USB and test. There is no reliable way of knowing if a hardware combination will work, other then tesing.
2.There are basic tools for configuring keyboard and mouse,  but nothing special. You might have problems with gaming hardware, as most of it is designed as Windows only. Test, same as above.
4.Propraetary.
5. There is none! I'd go with the simplest, and keep the default file system.
6.I don't expect Motorolla to make any special streaming software for Ubuntu. Perhaps you can do it with Bluetooth.

---

### Post by irv on 2012-06-03
After testing the live CD/DVD of Ubuntu, and if you decide to install it, I would setup a dual boot system. Install along side Windows 7. this way if you have problems running any of your games, you can boot into windows and still be able to play them. As Long as you paid for your copy of Windows you might as well use it. There is nothing wrong with using two OS's. I have been doing this for years. But 98% of the time I am in Ubuntu with Unity desktop.

---

### Post by Bucky Ball on 2012-06-03
As mentioned, download Ubuntu desktop ISO, burn to a CD, boot from CD, Try Ubuntu. See how it runs.

Frankly, if you are into playing Windows games, I'm really not sure why you have decided you want to use Ubuntu. They are Windows games.

Another option is to use Windows as a virtual machine inside Ubuntu (this would avoid the troublesome Wine).

---

### Post by Googleness on 2012-06-03
I'm trying to run a Live usb test but with Unetbootin and Universal usb installer I get same bug..
I choose "run Ubuntu..." then it's stuck nothing happens.

This is a screenshot:
_[http://img254.imageshack.us/img254/966/201206032247381.jpg]("http://imageshack.us/photo/my-images/254/201206032247381.jpg/")_
_[]("http://imageshack.us")_

---

### Post by Bucky Ball on 2012-06-03
When you boot from the stick and get to the choices to install or try, hit F6 and choose 'nomodset', then 'Try Ubuntu'. See if that makes a difference.

---

### Post by Googleness on 2012-06-04
nomodeset = Working. seems that ubuntu recognize all of my hardware even on live run so installing now...

wish me luck :P

---

### Post by Bucky Ball on 2012-06-04
Oh, just a word.

Make sure you hit the F6/nomodset option before installing as well. You can make this change permanent once you have installed but if you don't hit nomodset/install Ubuntu option first you may run into problems while installing. 

And good luck ... ;)

---

### Post by Dapilot1 on 2012-06-04
I have the same video card, no problems.
With 1TB may as well make the swap 8GB. That is what mine is, but I went the 4x2GB memory route. Also I find 12GB comfy for / on my laptop, but my desktop uses a full 16GB SSD. (ext4 btw)
Them make your /home whatever windows doesn't need.

I make both a USB and CD and have tried them on many systems, dunno why but sometimes one will work and not the other. I suspect it has to do with the motherboard. I remember having to change something about floppy emulation for USB ... it was legacy hardware. Get to know your BIOS settings, I had USB running at Full-speed instead of High-speed after clearing the CMOS battery.

---

### Post by Bucky Ball on 2012-06-04
> **Dapilot1 said:**
> I have the same video card, no problems.
With 1TB may as well make the swap 8GB.

Why??? And what has the size of your hard drive go to do with anything??? It is generally calculated on your RAM, and if you have more than 2Gb of RAM you will rarely, if ever, use /swap anyway (unless you plan running the next space station supply launch). 2Gb is plenty. With 8Gb of RAM you could switch /swap off and you wouldn't notice any difference. More RAM, less /swap.

---

### Post by Googleness on 2012-06-04
Hmmm extremely frustrating :X
So I'm trying to install then I see my continue button is grayed. Investigating further into the matter I learn that Ubuntu actually don't recognize my HDD.
Further investigation tells me I have what's called Marvell SATA3 Controller on my board and it's kinda problematic. I've tried every solution I've found online except physically connect my HDD sata cable to the Sata2 port which I'm not fond of this idea.

ideas?

---

### Post by Bucky Ball on 2012-06-04
You might be interested in this:

[http://ubuntuforums.org/showthread.php?t=1456238](http://ubuntuforums.org/showthread.php?t=1456238)

... which I discovered here:

[http://au.search.yahoo.com/search?p=install%20ubuntu%20sata3&fr=altavista&fr2=sfp&pqstr=install%20ubuntu%20sata3](http://au.search.yahoo.com/search?p=install%20ubuntu%20sata3&fr=altavista&fr2=sfp&pqstr=install%20ubuntu%20sata3)

---

### Post by Googleness on 2012-06-04
I've stumbled on those two topics and tried those solutions and even some more but the only thing left to try is to connect my hdd to Sata2 connection on my MoBo which I'm not fond of as I have huge heavy computer case connected to loads of cables :X

---

