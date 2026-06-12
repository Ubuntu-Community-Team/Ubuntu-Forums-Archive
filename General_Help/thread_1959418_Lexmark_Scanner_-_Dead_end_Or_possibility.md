---
title: "Lexmark Scanner - Dead end? Or possibility?"
date: 2012-04-15
forum: General Help
---

### Post by Roasted on 2012-04-15
I wanted a scanner to scan certain documents into my computer and keep digital copies of. I found a cheap used Lexmark and decided to give it a try. This experience has only completely reconfirmed why I avoid Lexmark like the plague. Nonetheless, I'm curious if there is someway, somehow, a slight glimmer of hope. 

My goal is to get my scanner working.
My device is a Lexmark X1185.
My operating system is Ubuntu 12.04 64 bit.

Help?

---

### Post by TheBigH on 2012-04-15
Well, there is a glimmer of hope. I have a Lexmark printer as well (I think an X1185 too, but I'm not home ATM so can't tell you for sure) and I agree with you that these are terrible, terrible machines. But I am able to scan with it using SimpleScan. It takes an eternity to do one page, but it works. Other Lexmark machines I've tried on ubuntu can print, but not scan.

You will need the relevant drivers, which you can get from the Lexmark website IIRC. There's also a bunch of threads on this forum with similar questions. You should search through those for some concrete advice (as opposed to this post of vague encouragement). Good luck.

---

### Post by Roasted on 2012-04-15
Only drivers on the web site are for Mac and Windows. Nothing for Linux. I've been through several lengthy threads on the forum and Google, but nothing concrete for scanning, mostly just printing.

Also, I tried XSane and Simple Scan, no dice.

I can't believe I wasted fifteen whole dollars on a glimmer of hope that MAYBE a Lexmark device would be somewhat worth it. I would have rather given the money to my dog to shred. 

Perhaps Canon's are a better bet. There's some flatbed Canon's on Ebay that can be had for 25 shipped.

---

### Post by kurt18947 on 2012-04-16
I don't know about $25 but the Canoscan 8800f has been plug & play.  I haven't tried it in in 12.04 yet. Fast and does slides & negatives if that's important.  I did a bunch of scan to .pdf pages using a Brother MFC-6490CW MFD and the gscan2pdf app.  That worked really well, SimpleScan worked but was slow.

---

### Post by HermanAB on 2012-04-16
Don't bet the farm on Canon.  Support for Canon scanners can be 2 years behind the curve.

---

### Post by Roasted on 2012-04-16
If Canon can be hit or miss, which brand is a safer bet? HP?

---

### Post by jadtech on 2012-04-16
curious maybe its time for a group experienced in ubuntu distro to put togeather at least known supported hardware list(s) it sure would help people who come to ubuntu to decide which might be for them..

as far as printers scanners and such put some where so it is found in a google search easily ..

---

### Post by kurt18947 on 2012-04-16
> **jadtech said:**
> curious maybe its time for a group experienced in ubuntu distro to put togeather at least known supported hardware list(s) it sure would help people who come to ubuntu to decide which might be for them..

as far as printers scanners and such put some where so it is found in a google search easily ..

There already exist such lists.  They're just neglected and out of date.

---

### Post by kurt18947 on 2012-04-16
> **Roasted said:**
> If Canon can be hit or miss, which brand is a safer bet? HP?

HP is about the safest bet with Linux.  HP puts resources into supporting Linux and should be rewarded.  I've had decent luck with Brother multi-function machines as well.  Brother offers Linux drivers for most models and there are drivers in the repositories as well.  Epson seems to be pretty well supported.  IMO Lexmark, Dell (often rebadged Lexmark) and Canon are more hit & miss.

---

### Post by Sn3akyP3t3 on 2012-04-16
I noticed in Ubuntu 12.04 64 my Canon MP460 now has drivers included for printing.  Previously there were no drivers available although the scanner appeared to work with Sane.

It is memorable that HP has given mind to support Linux drivers with many of their printers as opposed to their competitors.  I know very little about what exactly makes up a driver so perhaps this comparison is invalid, but I'm surprised that HP and Canon have such stark driver support differences given that HP uses a Canon print engine at heart.

Perhaps Canon's issue with giving support to Linux for drivers is because of how stratified the company is.  I noticed this when I tried to apply for an SDK for their PTZ cameras back during my college days.  [http://www.usa.canon.com/cusa/professional/products/professional_cameras/ptz_cameras/vb_c50i_vb_c50ir/?pageKeyCode=downloadSDK&productOverviewCid=0901e02480041840&id=0901e02480057a45_1&fileURL=NVS_SDK_Form](http://www.usa.canon.com/cusa/professional/products/professional_cameras/ptz_cameras/vb_c50i_vb_c50ir/?pageKeyCode=downloadSDK&productOverviewCid=0901e02480041840&id=0901e02480057a45_1&fileURL=NVS_SDK_Form)

I'm in awe at how little TWAIN 2.0 appears to have done for the Linux community.  Perhaps it will or already has had improve(d) Sane and scanner compatibility.  I'm still not able to scan my checks and send them to my bank because the Java applet is looking for TWAIN drivers.  Maybe scanTwain will be of some use that I can test while 12.04 is still in Beta 2.

---

### Post by Roasted on 2012-04-17
> **Sn3akyP3t3 said:**
> I noticed in Ubuntu 12.04 64 my Canon MP460 now has drivers included for printing.  Previously there were no drivers available although the scanner appeared to work with Sane.

It is memorable that HP has given mind to support Linux drivers with many of their printers as opposed to their competitors.  I know very little about what exactly makes up a driver so perhaps this comparison is invalid, but I'm surprised that HP and Canon have such stark driver support differences given that HP uses a Canon print engine at heart.

Perhaps Canon's issue with giving support to Linux for drivers is because of how stratified the company is.  I noticed this when I tried to apply for an SDK for their PTZ cameras back during my college days.  [http://www.usa.canon.com/cusa/professional/products/professional_cameras/ptz_cameras/vb_c50i_vb_c50ir/?pageKeyCode=downloadSDK&productOverviewCid=0901e02480041840&id=0901e02480057a45_1&fileURL=NVS_SDK_Form](http://www.usa.canon.com/cusa/professional/products/professional_cameras/ptz_cameras/vb_c50i_vb_c50ir/?pageKeyCode=downloadSDK&productOverviewCid=0901e02480041840&id=0901e02480057a45_1&fileURL=NVS_SDK_Form)

I'm in awe at how little TWAIN 2.0 appears to have done for the Linux community.  Perhaps it will or already has had improve(d) Sane and scanner compatibility.  I'm still not able to scan my checks and send them to my bank because the Java applet is looking for TWAIN drivers.  Maybe scanTwain will be of some use that I can test while 12.04 is still in Beta 2.

Pardon my ignorance but what is TWAIN that you refer of? I've never heard of them so I'm drawing a total blank on what you're referring to.

> **kurt18947 said:**
> HP is about the safest bet with Linux.  HP puts resources into supporting Linux and should be rewarded.  I've had decent luck with Brother multi-function machines as well.  Brother offers Linux drivers for most models and there are drivers in the repositories as well.  Epson seems to be pretty well supported.  IMO Lexmark, Dell (often rebadged Lexmark) and Canon are more hit & miss.

Good deal. I should be picking up a 25 dollar HP flatbed from Craigslist tonight. :guitar:

---

### Post by Sn3akyP3t3 on 2012-04-18
The easiest to understand definition of TWAIN I've seen is from wikipedia.  "TWAIN is a standard software protocol and applications programming interface (API) that regulates communication between software applications and imaging devices such as scanners and digital cameras."  Source: [http://en.wikipedia.org/wiki/TWAIN](http://en.wikipedia.org/wiki/TWAIN)

SANE is the Linux community's answer to TWAIN.  TWAIN suffered, or perhaps still does, from no disassociation with driver front end GUI and back end daemon.  A notable consequence of this can be read from Wikipedia, "One consequence of this separation is that network scanning is easily implemented with no special handling in either the frontends or backends. On a host with a scanner, the saned daemon runs and handles network requests. On client machines a "net" backend (driver) connects to the remote host to fetch the scanner options, and perform previews and scans. The saned daemon acts as a frontend locally, but simply passes requests and data between the network connections and the local scanner. Similarly, the "net" backend passes requests and data between the local frontend and the remote host."  Source: [http://en.wikipedia.org/wiki/Scanner_Access_Now_Easy](http://en.wikipedia.org/wiki/Scanner_Access_Now_Easy)

---

### Post by Roasted on 2012-04-18
Thanks for the update.

In an even more unfortunate turn of events, I scored a nice HP 5400c (after all, HP should be more widely supported, no?), but it too does not work with Simple Scan or XSane.

What, wait... really? Come on... ](*,)](*,)](*,)](*,)

The only thing I can't help but to question is, maybe it's because I'm on 12.04? I have yet to come across somebody who said their scanner is working on 12.04 (but then again I have yet to come across anybody who said they're using a scanner at all on 12.04)...

---

### Post by kurt18947 on 2012-04-18
> **Roasted said:**
> Thanks for the update.

In an even more unfortunate turn of events, I scored a nice HP 5400c (after all, HP should be more widely supported, no?), but it too does not work with Simple Scan or XSane.

What, wait... really? Come on... ](*,)](*,)](*,)](*,)

The only thing I can't help but to question is, maybe it's because I'm on 12.04? I have yet to come across somebody who said their scanner is working on 12.04 (but then again I have yet to come across anybody who said they're using a scanner at all on 12.04)...

There is a common issue installing scanners in 12.04 - and 11.10.  There is mention in another thread about using alien to convert .rpm to .deb.  I suspect that's what printer manufacturers do.  There's one glitch -- the .deb installer created with alien puts scanner files in the wrong place.  Brother's problem is documented here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html#f00101)

3rd item down.  The same problem is present in 12.04.  I also added any user accounts that I wanted scanner access to the 'lp' group.  Scanning in 12.04 is now working very well for me.  This glitch is not just Brother, I've seen it referenced by another brand as well.  I don't have a HP scanner so can't help out there.

---

### Post by Roasted on 2012-04-18
Hmm, good call. Thanks for the update. I was just coming back to post "Just tried with 11.10 LiveCD and it still doesn't work." I'm going to give this a shot later tonight.

There's only one additional question I have. I wasn't able to locate a .deb of ANY scanner driver for either the Lexmark or the HP that I have. So how is it I could even come across this if I never installed a deb in the first place? :(

---

### Post by Roasted on 2012-04-19
I ended up catching a sale for a Canon all in one, so I grabbed it. It prints great, but there's one catch - it doesn't detect the scanner.

It's times like this I feel like we're back in 1997. ](*,)

Oh hey, sweet:

[https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/800434?comments=all](https://bugs.launchpad.net/ubuntu/+source/simple-scan/+bug/800434?comments=all)

EDIT: I'm sold, I'm going back for this guy:

[http://hplipopensource.com/hplip-web/models/officejet/officejet_4500_g510a-f.html](http://hplipopensource.com/hplip-web/models/officejet/officejet_4500_g510a-f.html)

4th time is a charm, no? :(

EDIT II: I find it oddly frustrating that the Canon Pixma MP490 is on the list, the MP500 is on the list, but ask me where the MP495 is? Now, ask me who owns the MP495?

dfjals;djflaksjdfa;lksdjfalksjd;fl

---

### Post by kurt18947 on 2012-04-20
Sometimes you don't need the exact model #,  the 'family' will work.  it's possible that the MP490 software would work.  The only way I know to tell is to install the software and try it.

---

### Post by Roasted on 2012-04-20
> **kurt18947 said:**
> Sometimes you don't need the exact model #,  the 'family' will work.  it's possible that the MP490 software would work.  The only way I know to tell is to install the software and try it.

That's the part I don't get, because the printer works fine for the MP495. What doesn't work is the scanner. How can you install scanner software in Linux? After all, Sane libs are installed, and Sane is what has all of the drivers. A scanner is one thing I feel, if it doesn't work out of the box, you're pretty much out of luck.

---

### Post by Roasted on 2012-04-20
Well, I got me a new all in one. I picked up an Officejet 4500. I looked it up, along with almost all of HP's other all in one offerings, and sure enough the whole way down the list "yes, yes, yes, yes" for Linux support made me smile.

I was tempted to get the Epson, since I've had tremendously good luck with Epson too, but I decided to stick with the HP since it happened to be on sale anyway. I was also quite happy that I was able to print wirelessly as well without any issue.

This just goes to show, we need to stick with hardware that works for our operating system of choice. My Mac friends do the same thing. In fact, one of them specifically dual boots 10.6 and 10.7 because his printer doesn't work in 10.7. That would drive me crazy to dual boot specifically for that reason alone.

But anyway, we're in good shape now. :guitar:

---

