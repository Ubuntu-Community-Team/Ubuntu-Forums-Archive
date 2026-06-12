---
title: "Integrated Graphics (not working)"
date: 2006-06-15
forum: General Help
---

### Post by link141 on 2006-06-15
Hey guys :)
As the subject explains, my integrated graphics aren't working.  I **may** purchase a graphics card in the future, but for now, let's focus on getting this to work.  Allow me to explain what's wrong, simply, the driver is not present.  I've checked, and the driver isn't included in the Ubuntu system :(.  Anyway, my motherboard manufacturer provided a set of Linux drivers on the CD, but apparently, I need to compile it from source if I want to do use this driver.  I am not technical.  The integrated graphics are Unichrome Pro IGP, I got them from their integrated graphics manufacturer Via, on there site at < [http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2260&SubCatID=150](http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2260&SubCatID=150) >  All I ask is that some experienced user take a look at this and give me their interpretation on how to get the driver compiled, in place, and ultimately working.  
Thanks to anyone willing to help.

---

### Post by link141 on 2006-06-19
One typo, the drivers I got from their 'sight.  Now will anyone be able to help me?  I'd like to get this sorted out, and this thread has been sitting here for 4 days.  
thanks.

---

### Post by link141 on 2006-06-19
Ohh...  Sorry.  SUPER BUMP.

---

### Post by Tomy on 2006-06-19
[quote=link141]Hey guys :)
As the subject explains, my integrated graphics aren't working.  I **may** purchase a graphics card in the future, but for now, let's focus on getting this to work. Allow me to explain what's wrong, simply, the driver is not present. I've checked, and the driver isn't included in the Ubuntu system :(. Anyway, my motherboard manufacturer provided a set of Linux drivers on the CD, but apparently, I need to compile it from source if I want to do use this driver. I am not technical. The integrated graphics are Unichrome Pro IGP, I got them from their integrated graphics manufacturer Via, on there site at < [http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2260&SubCatID=150]("http://www.viaarena.com/default.aspx?PageID=420&OSID=20&CatID=2260&SubCatID=150") > All I ask is that some experienced user take a look at this and give me their interpretation on how to get the driver compiled, in place, and ultimately working. 
Thanks to anyone willing to help.[/quote]

The graphics driver is available in Ubuntu 6.06 (Dapper Drake). It goes by the name of "via" and is found in '/usr/lib/xorg/modules/drivers/' Edit your '/etc/X11/xorg.conf' file so the "Device" section looks like this:

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

good luck
Tomy

---

### Post by dcstar on 2006-06-21
[QUOTE=Tomy]The graphics driver is available in Ubuntu 6.06 (Dapper Drake). It goes by the name of "via" and is found in '/usr/lib/xorg/modules/drivers/' Edit your '/etc/X11/xorg.conf' file so the "Device" section looks like this:

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

good luck
Tomy[/QUOTE]
I have the (old) Unichrome driver working with my integrated video (very nicely, thank you very much....), but I now directly compile it into my custom kernel rather than have it loaded as a module.

The current Dapper kernel seemed to recognise my Via hardware straight away, so I don't think anyone really needs to do much apart from:
```
sudo dpkg-reconfigure xserver-xorg
```
And select the Via driver (if the auto-detect already doesn't).

---

### Post by Tomy on 2006-06-21
On my hardware the two options seem to make a  difference.

         Option          "DisableIRQ"
         Option          "EnableAGPDMA"

---

### Post by link141 on 2006-06-26
THANK
Sorry for not responding for a while, I was busy, and did not check the forum.

---

### Post by link141 on 2006-06-26
Sorry... did not finish typing.

---

### Post by link141 on 2006-06-26
THANK YOU!!!!!  AWESOME, SPECTACULAR, MARVELOUS, WONDERFUL!!!!
I've been trying to get my integrated graphics working for *quite* a while now, and this thread put an end to this tedious task.  I tried entering dcstars' code, entered via (graphics selection), and that did the trick!  The unused graphics chip is getting it's first workout on Linux, and is **definitely** working.  I was apprehensive of doing this at first, being that this (selecting via as my driver) crashed my display, and I had to reinstall (I'm not that technical).  Once again, THANK YOU VERY MUCH, to everyone who left a response.  

I have just one question:  How can I configure the two options that tomy recomended changing?  

Once again THANKS!

---

