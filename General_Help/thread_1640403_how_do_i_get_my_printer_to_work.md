---
title: "how do i get my printer to work?"
date: 2010-12-07
forum: General Help
---

### Post by joelkat on 2010-12-07
It wont print at all what do I do?

---

### Post by sgosnell on 2010-12-07
Did you install it?  Is it connected and turned on?  How is it connected?  USB?  ethernet?  Wifi?  What brand and model is it?

"It won't print" doesn't give us much to work with.

---

### Post by joelkat on 2010-12-07
connected by USB Canon mx700

---

### Post by sgosnell on 2010-12-07
Canon seems to be problematic.  Did you install it?  If so, how?  Exactly what are you doing to print, and what happens?  You're being a little too cryptic for me to give you much advice.

---

### Post by joelkat on 2010-12-07
no my computer detects the name thought and how do I install it?

---

### Post by joelkat on 2010-12-07
I really need my printer right nowww

---

### Post by joelkat on 2010-12-07
By the way I have no disc for my printer so yehh

---

### Post by sgosnell on 2010-12-07
System/Administration/Printing.  Click on the triangle just to the right of the New button, and select New Printer.  Follow the prompts, and it should find the printer and install the drivers.  If it still doesn't work, try Google.  Put your printer make and model, plus Ubuntu Linux, into the search box and you should find lots of pages dealing with Canon and Linux.

---

### Post by joelkat on 2010-12-07
I did what you said and there is a confusing thing it searches for Canon MX700 series and finds no drivers? is my printer too old?

---

### Post by sgosnell on 2010-12-07
Maybe, but the real problem is that Canon provides no, or at least few, Linux drivers.  Try searching the Canon site for a driver.

---

### Post by joelkat on 2010-12-07
I know you have a life but I have to eat dinner can you search a driver and I will when I get back?

---

### Post by joelkat on 2010-12-07
Oh I found it asap theres only Windows me windows 7 64 bit win7 vista even mac os x but not one linux / ubuntu if you wanna try here  [http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mx_series/pixma_mx700#DriversAndSoftware](http://www.usa.canon.com/cusa/support/consumer/printers_multifunction/pixma_mx_series/pixma_mx700#DriversAndSoftware)

---

### Post by sgosnell on 2010-12-07
Like I said, Canon is mostly a Windows-only company.  There is apparently no Linux driver for your printer.  I found a few on the Japanese site, you might try one of the mx-series drivers and see if it works.  I have a life too, and I've done all the searching I intend to for this.  I think you need to either go back to Windows or get a printer that works in Linux.  HP and Brother offer extensive Linux support, and I wouldn't buy anything else.

---

### Post by joelkat on 2010-12-07
thanks for the info would this be a good printer? [http://www.walmart.com/catalog/product.do?product_id=14644449&findingMethod=rr](http://www.walmart.com/catalog/product.do?product_id=14644449&findingMethod=rr)

---

### Post by sgosnell on 2010-12-07
I would think it would work.  I haven't found an HP that didn't work under Linux, although Windows can be problematic.  Sometimes a brand new printer will have no Linux driver available for a short time, but the closest driver will almost always work.  Install hplip, and everything should work fine.

---

### Post by anglican on 2010-12-08
> **joelkat said:**
> connected by USB Canon mx700There is a HOWTO in the forums for this printer:

[http://ubuntuforums.org/showthread.php?t=1273363](http://ubuntuforums.org/showthread.php?t=1273363)

H

---

### Post by sgosnell on 2010-12-08
I missed that when I searched earlier.  It may be necessary to change the dependencies to newer versions, since that how-to is rather old, but otherwise it should work.  Things shouldn't be that difficult, but if the manufacturer doesn't provide a driver, it can be.  Personally, I just buy printers that work under Linux, but I understand that people buy based on other priorities, especially if they don't know in advance that they're going to install another OS.  It's good that there is support and information available for getting all sorts of hardware to work.

---

### Post by ProNux on 2010-12-08
As I know Canon has available Linux drivers for their printers, as with my old canon printer. Visit their website, you might find something useful.

---

### Post by Spyderkid on 2010-12-08
here you go....


[Download]("http://sourceforge.net/projects/mp610linux/")

its from source-forge so it's completely safe.


[SIZE="4"]Instructions:
>download from above (in firefox preferably)
>should come up with software centre and ask you to install it, click yes
>wait...[/SIZE]

If it doesn't auto-maticly install (OR IF YOU USED CHROMIUM) then go to the folder (probably downloads and double click on the item)

Go to system> administration >printing >click the add+ button >network printers (that is if its not connected by a cable, if its by cable it should appear strait away and also in network if its wireless) > click on yours and it should find a driver click next next finish. then try printing something or a test page.

---

