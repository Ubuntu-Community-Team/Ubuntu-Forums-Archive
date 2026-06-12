---
title: "Scanner compatibility 12.04"
date: 2012-06-10
forum: General Help
---

### Post by dalpets on 2012-06-10
12.04 does not recognise my old Umax 1220P scanner with any of the provided frontends.

Is there a file repository in 12.04 that shows the actual scanners that are compatible with this version?

I've looked at the Ubuntu Wiki and there is nothing in there at this stage for 12.04 and it is a little bit dangerous to assume that scanners working with previous versions will work with 12.04.

Hope you can help. Thanks.

---

### Post by dalpets on 2012-06-11
Is anyone using a fully working scanner with 12.04?.

---

### Post by robert shearer on 2012-06-11
In response to your deleted post.... 
Why not take a 12.04 live cd with you when you go shopping for a scanner to confirm that it will work with Ubuntu ?.

Epson Perfection 1650 works for me.

links...
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)  (lists some Umax models and the umax-sane package needed)

[http://askubuntu.com/questions/tagged/scanner](http://askubuntu.com/questions/tagged/scanner)

[http://www.sane-project.org/man/sane-umax_pp.5.html](http://www.sane-project.org/man/sane-umax_pp.5.html)  (sane man-page for your Umax astra 1220p)

[http://manpages.ubuntu.com/manpages/hardy/en/man4/uscanner.4.html](http://manpages.ubuntu.com/manpages/hardy/en/man4/uscanner.4.html) (**usb** scanners that are said to work in 12.04. Note the Umax 1220u (u for usb) is listed. Your **Parport** Umax (1220p)may be a little more difficult to get functional but it probably wouldn't work ootb, if at all, in the latest version of Windows either..?)

---

### Post by dalpets on 2012-06-11
Thank you for your input.

The Umax 1220p is listed as definitely not working in 12.04. Actually it does work in XP with an HP (rebadged) driver.

 How does the live cd approach work?. I assume you mean loaded on a laptop. Unfortunately I don't think too many shops would welcome asking them to unpack their packaged scanners for such a test if that is what you are suggesting.

Your 1650 is no longer available in the market place. 


> **robert shearer said:**
> In response to your deleted post.... 
Why not take a 12.04 live cd with you when you go shopping for a scanner to confirm that it will work with Ubuntu ?.

Epson Perfection 1650 works for me.

links...
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)  (lists some Umax models and the umax-sane package needed)

[http://askubuntu.com/questions/tagged/scanner](http://askubuntu.com/questions/tagged/scanner)

[http://www.sane-project.org/man/sane-umax_pp.5.html](http://www.sane-project.org/man/sane-umax_pp.5.html)  (sane man-page for your Umax astra 1220p)

[http://manpages.ubuntu.com/manpages/hardy/en/man4/uscanner.4.html](http://manpages.ubuntu.com/manpages/hardy/en/man4/uscanner.4.html) (**usb** scanners that are said to work in 12.04. Note the Umax 1220u (u for usb) is listed. Your **Parport** Umax (1220p)may be a little more difficult to get functional but it probably wouldn't work ootb, if at all, in the latest version of Windows either..?)

---

### Post by kurt18947 on 2012-06-11
> **dalpets said:**
> Is anyone using a fully working scanner with 12.04?.

Yes.  I've gotten a few Brother MFC models to scan though it takes some time.  The Canoscan 8800F was plug & play after doing an update while the scanner was plugged in.  It looks like the Canon 8800F has been replaced by the 9000F.  I have no experience with the 9000F.

---

### Post by robert shearer on 2012-06-11
> **dalpets said:**
> Thank you for your input.

The Umax 1220p is listed as definitely not working in 12.04. Actually it does work in XP with an HP (rebadged) driver.

and would probably work in older Ubuntu versions too but my point was that it would not be likely to work with a **current** version of Windows.

>  How does the live cd approach work?. I assume you mean loaded on a laptop. Unfortunately I don't think too many shops would welcome asking them to unpack their packaged scanners for such a test if that is what you are suggesting.

Unfortunately we do not know where you are so suggestions like mine have to be rather generic.

Here in New Zealand we have a Consumers guarantee act that ensures goods are fit for purpose and retailers would be more than happy to allow a shop trial or swapping units until one was found that worked with Ubuntu.

Given the global economy any retailer who won't go the extra distance and allow you a shop trial is not likely to be in business much longer.
 Avoid them like the plague, they won't be around to honour any warranty if needed.

> Your 1650 is no longer available in the market place.

Correct and as everyone bought all-in-one printers a large number of stand-alone scanners were discarded.

Again, in New Zealand, most thrift shops have a couple of usb scanners costing anywhere from US$0.50 to US$5.00

As you seem happy with an ancient parport scanner I assumed an upgrade to usb would suffice and the list on this man-page should serve as a guide.....
[http://manpages.ubuntu.com/manpages/hardy/en/man4/uscanner.4.html](http://manpages.ubuntu.com/manpages/hardy/en/man4/uscanner.4.html)

My Epson 1650 was a freebie from a recycling initiative, there may be several online where you are... ?

I see others have posted their experiences with newer units. 

Regards Bob.

---

### Post by tlhIngan on 2013-01-04
Has anybody had any success getting the Umax Astra 1220P parralel port scanner working with 12.04 using Sane?

---

