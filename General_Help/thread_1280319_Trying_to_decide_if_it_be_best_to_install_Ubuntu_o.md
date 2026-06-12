---
title: "Trying to decide if it be best to install Ubuntu on laptop."
date: 2009-10-01
forum: General Help
---

### Post by demonic_crow on 2009-10-01
I tried getting the linksys wusb54gsc to work on my desktop but it doesn't show a device.  I'm not sure if its cause it doesn't have usb 2 or not.  So I'm thinking about putting ubuntu on my laptop since I had ton of problems with it for the past year.  I had to reinstall the OS alot. So my question is I wondering if I will be able to get my Intel pro/wireless 2200bg network connection card to work with unbuntu.  It doesn't work right now with the computer cause it says it have problem with resources.  If I could get that card to work in ubuntu when it doesn't on window XP that would be great.  Thanks for taking time to read this all.

---

### Post by ninjapirate89 on 2009-10-01
Boot from a live cd. If your hardware works, then it will (should) work when installed.

---

### Post by Bucky Ball on 2009-10-01
+1. Lot of Intel cards 'just work'. Try the Live CD as suggested. This will give you a good picture of what is what.

Incidentally, *please* do a search for info **before** posting in the forums:

[http://au.altavista.com/web/results?itag=ody&q=Intel+pro%2Fwireless+2200+ubuntu&kgs=0&kls=0](http://au.altavista.com/web/results?itag=ody&q=Intel+pro%2Fwireless+2200+ubuntu&kgs=0&kls=0)

Good luck with it.

---

### Post by demonic_crow on 2009-10-01
ok, I just install ubuntu on my desktop yesterday.  So when I boot my laptop up with the cd in it, does it have an option to choose live.

---

### Post by cariboo on 2009-10-01
If you have the desktop Live CD, it is the first choice in the menu. Try before you install.

---

### Post by demonic_crow on 2009-10-01
Is there something I can type into the terminal to see if it recognize it or something.

---

### Post by ninjapirate89 on 2009-10-01
> **demonic_crow said:**
> Is there something I can type into the terminal to see if it recognize it or something.

If Ubuntu recognizes it then you should be able to connect to a wireless network and test it.

---

### Post by demonic_crow on 2009-10-01
I ran sudo iwconfig and it show no wireless.  Would I be able to get it to work some how.

---

### Post by ninjapirate89 on 2009-10-01
> **demonic_crow said:**
> I ran sudo iwconfig and it show no wireless.  Would I be able to get it to work some how.

Sorry, I'm not the best at fixing ubuntu when it comes to stuff like this. If it's not working by default then someone else will have to figure it out.

---

### Post by Bucky Ball on 2009-10-02
Try plugging an ethernet cable in and then switching the machine on. You should be offered updates. Accept them. It may offer drivers for you card in the process.

---

### Post by demonic_crow on 2009-10-02
It wont bring up the internet using the live disc. It does show im connected. Any thoughts on that. I might just install ubuntu on it and hope I can get the wireless internet to work. Not sure if it be easlier doing it that way. I tried to install compiz on it and it had issuse and didnt install it.

---

### Post by Bucky Ball on 2009-10-02
You are running from the CD. Waste of time installing Compiz or anything else as it won't stick.

Install to hard drive and fix wireless. If it shows connected it will just be a setting and should be easily fixable.

---

### Post by jubop on 2009-10-03
Ok so I'm a bit of a beginner but if I understand your problem you want ubuntu to recognize your wireless card, if that's the case then try this:

to get my wireless card working on ubuntu once ubuntu is installed go to System>Administration>Hardware Drivers

it'll take a second to scan for drivers your wireless card should appear once the program opens. Highlight the driver then click the Activate button in the lower right-hand corner.

Hope this helps, though I know someone else who had a problem getting the wireless card recognized and they needed to install ndiswrapper so if this doesn't work try searching for info about ndiswrapper and see if this applies to you.

Best of luck

---

