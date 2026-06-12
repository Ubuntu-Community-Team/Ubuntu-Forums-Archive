---
title: "Which Derivative for Compaq Presario SR1010Z"
date: 2011-02-21
forum: General Help
---

### Post by PUPPY?123 on 2011-02-21
Hi all,

I have a Compaq Presario SR1010Z desktop with an AMD 64 processor and 512 MB RAM (some is used by the graphics card which isn't exactly state of the art). 

I have used (X)(K)(U)buntu and puppy linux with it throughout the years and have often had the following problems with all of the above:

Sometimes, these multicolored lines will appear sporadically around the screen (not my monitor I know this).  If I open new windows over them, they will someitmes go away.  It is most prominent when I try to use OpenOffice's powerpoint program but happens if OOo isn't even installed.

Sometimes, it just freezes. 

KDE is the worst.  But it even happens in Lubuntu and Xubuntu and  (unfortunately Lubuntu didn't recognize my wireless).  

Also, the old versions of ubuntu seem to recognize my wireless fine, while the new ones act like it doesn't exist, so I was thinking about installing an old version then using synaptic to reach the desired windows manager/version combination.  

I can get the wireless working with puppy after a bit of finagling.  I don't need OOo.  I want to mainly use this computer for web browsing and playing around with linux, but unexpected freezing could still mess me up.  I had to reisntall puppy more than once because it froze when updates my repositories.  

Anybody have suggestions as to what this combination might be?  Especially those of you who have the same desktop?

---

### Post by gordintoronto on 2011-02-21
I have a 1055CL, which is somewhat similar. What wireless card did you add? lspci will identify it. Did you install a video card? I bought a video card for $10 on eBay, and it was a major improvement over the (via Chrome?) original video. I'm about to discard the computer, which has given me full value over the years.

---

### Post by PUPPY?123 on 2011-02-22
Thanks for replying.  I can't tell you the wireless card right this second because I won't be back near it until tomorrow.  

Old ubuntu could detect it.  Sometimes, it would detect it on the liveCD but not when installed.

It's pci card of some sort.  

Regarding the video card:  How do I check what hardware I have now?  Can I show you a specific output when the liveCD is in?  

I would be up for buying a new video card if it costs between $10-20, but I would want to make sure it's an improvement.  

What derivative did you have running on your computer?

---

### Post by gordintoronto on 2011-02-22
Open Accessories/Terminal. Enter the command:
lspci

The line which includes the string "VGA" is your video adapter. The line which includes "802" is your wireless adapter.

My wife uses the Compaq. When she was on an extended visit to China I swapped in a different hard drive and ran Ubuntu, probably 9.10. She uses a program called QQ for videoconferencing, and I'm pretty sure that means she needs Windows.

I run 10.04 and 10.10 (mostly 10.10) on my desktop, and 10.04 on my laptop.

---

### Post by PUPPY?123 on 2011-02-23
Thanks for your response.  Sorry for the delay with mine.  I should have access to the computer in a couple of hours.  

I'm going to install the latest version of xubuntu and hope wireless works (was considering DreamLinux but am not digging the OS X look as I already have a Mac and Ubuntu has way better support).  Either way, I'll post the output you suggest.

I really appreciate your help.

---

### Post by PUPPY?123 on 2011-02-23
Okay, so new xubuntu messed up wireless again.  I found a xubuntu 7.10 disk from before and ran it live.  Here is the output:


VGA compatible controller:  Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761x PCIE VGA Display Adapter

Network controller: Intersil Corporation ISL 3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

I'm installing old xubuntu (hoping wireless stays) then updating (hoping wireless stays).

I've put a huge swap space of nearly 6 G in addition to the 512 MB RAM/~375MB with graphics card (I know it's an overkill, but hopefully I won't need to partition again for as long as I use the machine).

---

### Post by PUPPY?123 on 2011-02-23
Wireless did not work upon install with 7.x and now it seems WEP did not work with the LiveCD but upon install I had nothing (like no wireless card was there).

I had this problem before where it didn't load the driver properly, but I've had wireless working before perhaps with newer but still old versions.  I also got it to work on the latest Puppy.

Hopefully you can help and I can install the current Xubuntu version.

---

### Post by gordintoronto on 2011-02-24
I would try lubuntu rather than xubuntu, but I don't have a lot of experience with either. I installed lubuntu on an external drive, and it worked very nicely for me for a few dozen hours of playing around.

If you can find a Windows driver for your wireless, and good instructions on using ndiswrapper, you can get the wireless working. I've never needed to use that approach, so I don't have a pointer to a good writeup on ndiswrapper.

The SIS graphics adapter is about as bad as it gets. I would scour ebay for a cheap video card. First, open the box and check whether you need an AGP card or PCI. I *think* you need AGP, but I'm not at all sure. On my similar computer, as soon as I installed a video card, the motherboard video was disabled -- which is what you want.

---

### Post by PUPPY?123 on 2011-02-25
Thanks for the hardware advice.  I think I will try to find a windows driver though it really sucks since the old kernel worked out of the box for 8.04.

---

