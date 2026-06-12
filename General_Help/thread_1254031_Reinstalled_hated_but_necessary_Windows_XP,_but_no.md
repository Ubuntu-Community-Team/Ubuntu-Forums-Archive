---
title: "Reinstalled hated but necessary Windows XP, but now it won't connect to the internet."
date: 2009-08-30
forum: General Help
---

### Post by OsakaWilson on 2009-08-30
I've been using Ubuntu for so long, that maybe I just forgot what I need to do, but I can't get Windows connected.

I thought maybe I needed to download a driver for the motherboard, but that doesn't seem to have worked. I don't even know if I got the right one. The name on my board is MSI 865G Neo2-P, but the closest thing I have found is MSI 865G Neo2-PLS/ PFS. This is on the MSI site. 

[http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=151](http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=151)

I don't even know if this is the problem. Can anyone help? I cringe at the thought of actually buying Vista, but I will have to if I can't make this work.

---

### Post by uylug on 2009-08-30
Going back to XP? Why? Why would someone do that?

Anyways, don't you have a cd or something?

---

### Post by OsakaWilson on 2009-08-30
I'm not going back, I need it for a few things that Ubuntu can't do yet. I rarely use it, but when I do, it is necessary. I re-installed it with the Windows XP CD, but now it won't connect to the internet.

---

### Post by uylug on 2009-08-30
Yeah but don't you have a cd your motherboard came with?

---

### Post by OsakaWilson on 2009-08-30
No, I don't have it. Do you know how to get Windows XP connected to the Internet?

---

### Post by uylug on 2009-08-30
You need to get your network drivers first.

---

### Post by OsakaWilson on 2009-08-30
I downloaded and installed the Realtek Gigabit Ethernet Drivers from the link in my original post. The install seemed work, but no change in the Internet connection.

I switched cables with my Ubuntu computer to make sure the it was not my network.

---

### Post by uylug on 2009-08-30
Sorry but i don't know. lol.

Have you tried running ipconfig? Does it say you're connected? Have you configured your ip address and gateway?

---

### Post by OsakaWilson on 2009-08-30
Running ipconfig doesn't open the command prompt or do anything at all. 

I have a wired LAN throughout my home and up until now, I have only needed to put in ISP information for email.

---

### Post by mdurham on 2009-08-30
Maybe it would be better to run Windows in VirtualBox

---

### Post by uylug on 2009-08-30
No, i was talking about ipconfig being run on the Windows side,

---

### Post by OsakaWilson on 2009-08-30
I'm beginning to think so. Even if I just put Ubuntu on that old Windows machine and use it only for VirtualBox.

---

### Post by OsakaWilson on 2009-08-30
Yeah, Uylug, I ran it in Windows, nothing happened. Anyway, I think I will just bag it. Thanks for the help.

---

### Post by Kristofer Van Orton on 2009-08-30
whats your computer make and model?

---

### Post by OsakaWilson on 2009-08-30
It's a five-year-old thing someone put together for me from all new parts.

---

### Post by oboedad55 on 2009-08-30
> **OsakaWilson said:**
> It's a five-year-old thing someone put together for me from all new parts.

Is this a computer that was running Ubuntu successfully or not? In either case, why not boot the Ubuntu CD and make sure your network is working under Linux. That will at least tell you it's not the hardware.

--Jon

---

### Post by OsakaWilson on 2009-08-30
It was running Windows XP successfully before the re-install. I have a wired LAN in my home with cables in each room. I switched cables with the computer that is successfully connecting Ubuntu and still it didn't work. 

Anyway, I am trying the Ubuntu CD now.

---

### Post by oboedad55 on 2009-08-30
> **OsakaWilson said:**
> It was running Windows XP successfully before the re-install. I have a wired LAN in my home with cables in each room. I switched cables with the computer that is successfully connecting Ubuntu and still it didn't work. 

Anyway, I am trying the Ubuntu CD now.

Ah, I see. I didn't understand your original post. Well, do let us know how you come out with the Ubuntu CD. Refresh my memory; why do you need Windows?

--Jon

---

### Post by OsakaWilson on 2009-08-31
Why I need  Windows:

For work, I need to edit MS Word files that have elaborate formatting and somehow when people open my files that I have edited in OpenOffice and saved as .doc files, the formatting is quite different. 

Audible.com still won't let me download in Linux. 

I live outside the U.S. and iTunes is the only legal option for downloading the final season of Lost. :)

My Plantronics CS50 mic is not acknowledged in Ubuntu.  

Other than that, I would have gotten rid of it long ago. A primary goal in my life is to solve these problems, but I am not there yet.

*****

I connected to the Internet perfectly with the live CD.

---

### Post by darco on 2009-08-31
If you installed Windows for the first time, sounds like you need to install your chipset drivers. They typically contain the ethernet controller...
I use vmware to run Windows because I need Outlook.....this is a great setup.

darco

---

### Post by OsakaWilson on 2009-08-31
Do you know how to find out what these "chipset drivers" are and how to get them?

Edit: The computer I wish to install them onto is running an Ubuntu Live CD, if there is any way to find and retrieve them in Ubuntu.

---

### Post by darco on 2009-08-31
Since its a home built pc, I would find out the make/model of the motherboard and go from there...
good luck

darco

---

### Post by OsakaWilson on 2009-08-31
Sorry for being so completely ignorant Ubuntu has worked so well for me over the years, I don't know what to do with a Windows machine. 

I included a link to the motherboard in my original post. 

[http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=151](http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=151)

I assume that the drivers listed at the bottom of the page are the "chipset drivers". Is this correct? Do I need to install all of them? I installed the first one, Realtek Gigabit Ethernet Drivers, but there was no change in ability to connect to the Internet.

---

### Post by darco on 2009-08-31
Oh ya sorry for missing the link...no the last link is for USB drivers that add support to the chipset.....I would try the Intel INF Drivers instead.
In Windows, go to System and then Device Manager and you will see what drivers need to be installed. You will see a yellow exclamation point next to them.

darco

---

### Post by OsakaWilson on 2009-08-31
I'll give it a try. Thank you very much. Details about this kind of thing are very hard to find.

---

### Post by toogooda on 2009-08-31
> **OsakaWilson said:**
> Running ipconfig doesn't open the command prompt or do anything at all. 

I have a wired LAN throughout my home and up until now, I have only needed to put in ISP information for email.
Hey Buddy,
ipconfig does work but if you run from run prompt it will close before you can see it.

First type CMD from startmenu->Run
Then ipconfig
once we have that info we can help.
ot wireless?
I assume you are using a Ethernet not wireless

---

