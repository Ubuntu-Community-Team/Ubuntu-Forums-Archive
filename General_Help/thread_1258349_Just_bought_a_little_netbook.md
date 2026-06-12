---
title: "Just bought a little netbook"
date: 2009-09-04
forum: General Help
---

### Post by thefuturism on 2009-09-04
Hello all,

I've always wanted to try out ubuntu, and I just got a new Acer AspireOne netbook so I thought I would try out the netbook remix I've been reading about.

Now, I am brand new to ubuntu so I just had a couple questions...

I want to put the UNR on my netbook but I still want to be able to use XP when I want to. Is it possible to have both systems installed at the same time if I partition my hard drive? Or is there a different way of doing this?

Since this install will just be for my netbook, I am mainly concerned with the the internet browser and open office capabilities for school. 
-Are there any other (better) alternatives to using open office programs with UNR?
-Also, has there been any major problems with the network configuration for the wireless? I will be using the netbook at school almost exclusively and I have to go through a somewhat tiresome procedure to connect to the school network. I just want to make sure there aren't any blatant issues with this - although I don't think there are.

Thanks for any information.
-Ryan

---

### Post by Kristofer Van Orton on 2009-09-04
you dont really even have to partition your harddrive
just burn the ubuntu iso to a disk-->put it in your computer--->navigate to my computer--->click the drive you inserted the disk into--->it will come up with a dialog and the middle option with say "install inside windows"--->click that and pick your preferences--->install
now when you boot your computer it will load the boot loader
Windows XP
Ubuntu
hope this helps
KVO

ps. im sure there are alternatives but open office works fine
also you shouldny have any problems with the wireless, it should set up automatically

also if it makes you feel any better i have an Acer Aspire x1200 desktop computer running ubuntu and vista fine
as if you couldnt tell from my signature :P

---

### Post by sailthesea on 2009-09-04
You could also put the ISO on a USB thumb drive and use it for live sessions when you want to use ubuntu Especially as not a great many netbooks seem to have cd/dvd drives You can also do a Wubi install that sets it up within windows Wireless issues aren't so much of a problem now and remix is very much geared at getting top performance from a netbook
Having the thumb drive also means you can use another compatible machine to use your personal copy of ubuntu
Enjoy!

---

### Post by thefuturism on 2009-09-04
Well, the netbook doesn't actually have an optical drive. So I'll have to install it from a usb flash drive. Will that work the same way?

Is your method what they call 'dual boot'?

I just want to be able to operate both XP and UNR without them interfering with each other. Also, on startup how am I able to choose which system loads?

---

### Post by thefuturism on 2009-09-04
> **sailthesea said:**
> You could also put the ISO on a USB thumb drive and use it for live sessions when you want to use ubuntu Especially as not a great many netbooks seem to have cd/dvd drives You can also do a Wubi install that sets it up within windows Wireless issues aren't so much of a problem now and remix is very much geared at getting top performance from a netbook
Having the thumb drive also means you can use another compatible machine to use your personal copy of ubuntu
Enjoy!

So, you mean I can run the ISO straight from the flash drive without having to install? How would that affect any save files I create while using UNR? Also, wouldn't that slow the performance of UNR? If I have them both installed in 'dual boot' or whatever, then only one would be active at a time, right? 

Sorry for so many questions haha.

---

### Post by lildigiman on 2009-09-04
You will be able to choose at startup when Ubuntu will auto-install GRUB in the MBR(master boot record).

I would not suggest an Install INSIDE windows, because that can decrease the performance of Ubuntu (only alittle, but still).

---

### Post by lildigiman on 2009-09-04
> **thefuturism said:**
> So, you mean I can run the ISO straight from the flash drive without having to install? How would that affect any save files I create while using UNR? Also, wouldn't that slow the performance of UNR? If I have them both installed in 'dual boot' or whatever, then only one would be active at a time, right? 

Sorry for so many questions haha.

Running a Live Boot of UNR would be possible from your flash drive, again, you would have decreased performance.

---

### Post by blueridgedog on 2009-09-04
> **thefuturism said:**
> 

I want to put the UNR on my netbook but I still want to be able to use XP when I want to. Is it possible to have both systems installed at the same time...?
-Are there any other (better) alternatives to using open office programs with UNR?
-Also, has there been any major problems with the network configuration for the wireless? I will be using the netbook at school almost exclusively and I have to go through a somewhat tiresome procedure to connect to the school network. I just want to make sure there aren't any blatant issues with this - although I don't think there are.



UNR comes as an IMG file.  See this site for instructions on installation:

[https://help.ubuntu.com/community/Installation/FromImgFiles](https://help.ubuntu.com/community/Installation/FromImgFiles)

You may run it off of a USB thumb drive, shrink your windows partition or install it on an SSD card (a great option).  If you do not have an SSD card in the external slot currently, then you can put in an 8 gig card and then install to that.

As to open office, it is the best you can get on Ubuntu and a very nice product at that.

As for the wireless, my eeePC works perfectly with UNR, I only needed a few tweaks to get everything working (restricted codecs and the camera).  

Good luck.  I only run UNR on my netbook as the overhead of windows is too much.

---

### Post by sailthesea on 2009-09-04
> **thefuturism said:**
> Well, the netbook doesn't actually have an optical drive. So I'll have to install it from a usb flash drive. Will that work the same way?

Is your method what they call 'dual boot'?

I just want to be able to operate both XP and UNR without them interfering with each other. Also, on startup how am I able to choose which system loads?

Well you have a lot of answers already
Having no optical drive leaves you with the option of putting the ISO on a thumb drive to boot into or install from 
You can treat a USB as a seperate  drive with UNR on it and any files stored on your windows install can be accessed from (but not vice versa)
To boot into the USB you will need to press F11 or something on startup and select the boot option It won't be as good as an istall but will give you a feel, plus any changes to a USB can be kept for future use

---

### Post by thefuturism on 2009-09-04
Thanks for all the information everyone!

I think I just have one last set of questions while I am waiting for the img file to finish downloading.

- I think I will install UNR to the hard drive, so I put the img file on the thumb drive, plug it in, and boot up my computer. Do I need to partition my hard drive first in order to do this?

- Does the UNR come with this GRUB thing that allows me to choose with OS I want to load on future startups? Basically I like the idea of being able to choose what OS I want to use when I turn my computer on each time.

- If I did decide to install and run UNR off a SD card kept permanently in the card reader, would all the files I generate (such as open office files of my school lecture notes) be stored on the SD card as well? Would there be a way to retrieve these files (short of just emailing them to myself to access them from another computer)?

---

### Post by sailthesea on 2009-09-04
Once you have the USB set up you can boot into it without making any changes to your computer (that is in the boot option menu) You can then run a live session from it to see how your computer performs Don't try and install just yet it will end in tears Honestly:)
 If everything checks out you can think about installing a dual boot from USB This would be best performance wise but I would seek help beyond my experience in the best way to do it A netbook is limited in performance and requires a tailored installation
 PS Ensure you correctly download and burn the ISO to the USB drive You should find the relevant guides in the Get UNR download site

---

### Post by lildigiman on 2009-09-05
Install on an SD card is a great Idea. I would suggest saving all your Documents (like music, office files, etc) on the windows Partition (Ubuntu Can read Windows), that way Windows can read them too (because windows won't be able to read Ubuntu's ext Filesystem).

Grub *should *auto install. I would be surprised if it didn't.

Best of luck - lildigiman.

---

### Post by blueridgedog on 2009-09-05
> **thefuturism said:**
> 

- If I did decide to install and run UNR off a SD card kept permanently in the card reader, would all the files I generate (such as open office files of my school lecture notes) be stored on the SD card as well? Would there be a way to retrieve these files (short of just emailing them to myself to access them from another computer)?

Yes, you could create a partition on the SSD card that was readable by many OS's, such as fat32.  Documents saved there could be read by most computers you insert the card into.

---

### Post by thefuturism on 2009-09-05
So, I have managed to get UNR onto my usb thumb drive, and I have run several live sessions to play around with it. 

Before I go ahead with the actual install I have a few concerns that I can't seem to find the answer to.

- When I launch the UNR install from the boot screen, will I be able to choose to which drive I install it to? So for example, if I partition my hard drive will I be able to choose the partition without XP for the install? (Doing this I would be able to choose which OS I want to boot from my system BIOS, right?). OR, I was thinking of partitioning my 8GB thumb drive and installing the UNR to the thumb drive itself - is this possible? Would this create 'persistence'? 

- A less important question is... I know that UNR comes with the desktop switcher between the UNR environment and the more basic gnome style environment... But if I wanted it to look like (see Image link below) would I be able to just install some kind of package to add that option, or would it even be possible with the UNR? And if yes, where would I find it?

[http://news.softpedia.com/images/news2/GNOME-2-22-A-Truly-Amazing-Desktop-2.jpg]("http://news.softpedia.com/images/news2/GNOME-2-22-A-Truly-Amazing-Desktop-2.jpg")

---

### Post by mike555 on 2009-09-06
be very careful if you decide to partition your harddrive (assuming it's big enough to partition) pick the "manual" option during install and when the partition manager comes up you can shrink your ntfs partition to make room for Ubuntu ,set it to format ext3 and to " / ", then make a small swap partition (maybe 4 GB) and set it as a swap format ..... then install Ubuntu to the ext3 partition .... reboot when it tells you to (removing the USB)

---

### Post by thefuturism on 2009-09-08
Okay, I think I have this figured out.

Here's my plan - please object if I make any mistakes :) .

1) Use WIN32DiskImager to attach the UNR .img file to my 1GB SD card.
2) Restart computer and boot from SD card.
3) Plug in 8GB USB thumb drive.
4) Go ahead with regular UNR install, but choose the 8GB drive as the destination (instead of my actual hard drive).

I think this will work. But, after I install UNR to the thumb drive, will all I have to do to run UNR is have the thumb drive inserted when I turn on my computer (assuming the BIOS boots from the USB)?
Also, will changes I make to the OS be stored on the thumb drive?

---

