---
title: "two problems"
date: 2011-09-15
forum: General Help
---

### Post by d2redneck on 2011-09-15
I have a toshiba satalite p750 series laptop my internal mic dosn't work and I have brother mfc 495 cw printer that I can't get hooked up to my computer and I don't think that I can get my internal web cam to work either.  I think that I found the drivers on the brother site and I dl'd them to my downloads folder.  any help would be great and please be patient I am very new to linux.  I also went to the toshiba website and they don't have any drivers for linux.  I am using ubuntu 11.04 I think.  Thanks.

---

### Post by gordintoronto on 2011-09-15
It's probably a lot easier than you expected. Click on the Sound icon in the top panel, and select Sound Preferences. Your mic is probably muted.

For the printer, I'm not sure what you mean when you say you "can't get it hooked up." Run Printers, select "add" and be just a little patient. If it's a network printer, select that option, and a few seconds later the printer should appear. Click it and select the obvious options from there.

For the webcam, use Synaptic Package Manager to install Cheese and run it. You will probably see yourself on the screen.

---

### Post by d2redneck on 2011-09-20
ok I already tried the other two deals that you posted and the mic isn't mutted.  it isn't there and I can't get the drivers that downloaded for the printer set up to the computer.  I will try that cheese program and see how that works and let you know.  thanks for the advise.

---

### Post by d2redneck on 2011-09-24
Well the cheese program worked but Im still having problems with the mic and printer.

---

### Post by Hakunka-Matata on 2011-09-24
what model brother printer do you have?

---

### Post by IWantFroyo on 2011-09-24
```
alsamixer
```

Just to make sure.

Also, you likely don't need to download drivers. If you know the printer model, just open the "Printing" app and add a new printer. Select your printer from the database, and everything will be just dandy. I have heard of Brother printers not having included drivers. If the model isn't there, you might want to do a Synaptic search.

Good luck!

---

### Post by Hakunka-Matata on 2011-09-24
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by d2redneck on 2011-09-27
I tried the alsamixer deal didn't do much good and I am using a brother mfc 495cw printer.  I already looked in the add printer and it wasn't there and I downloaded all of the drivers they had for my printer and I can't get them installed.  Sorry if I sound like a real noob here but, My classes at ITT got me interested in linux and I am just learning.  I haven't gotten to the second linux class where they teach you how to install printers or anything like that so I guess I am a real noob.  Please be patient with me.  I downloaded these drivers to the downloads folder.

---

### Post by Hakunka-Matata on 2011-09-27
I found a ppd file for your mfc 495cw printer.

Go to [http://ubuntuforums.org/showthread.php?p=9126813](http://ubuntuforums.org/showthread.php?p=9126813)

and check post # 14

you can also google **brmfc495cw.ppd**

---

### Post by kurt18947 on 2011-09-28
One thing that can cause confusion installing Brother printers is the Brother furnished printer drivers are all 32 bit.  Anyone using a 64 bit system needs to follow the directions on the driver page.  This line is the one that's different on 64 bit installs:
```
dpkg  -i  --force-all  (lpr-drivername)or (CUPS-drivername)

```The "--force-all" tells dpkg to ignore the architecture differences and install anyway.  If you don't know if you have a 32 bit or 64 bit O.S., open a terminal and run this command:
```
uname -a
``` You'll see mention of either i686 (32 bit) or X86_64 (64 bit).  That's the only difference I'm aware of installing Brother's printer drivers.  Of course if the printer is found automagically it's even easier, the correct driver will be installed, no command line required. Not all Brother printers are in the foomatic database.

---

### Post by d2redneck on 2011-09-28
well I got the printer to work after going through and doing what the brother site said again and I also did the force all.  there was two problems with the printer.  one was the fact that I wasn't doing the force all in the directory I had saved the files to and the other was that it was showing up has a usb device instead of a network device.  took care of those problems and now all I have to do is get the internal mic working.  When I get that done I can darn near get rid of windums on laptop completely.  please help with this last issue and help me grow my geek hat.  Thanks.

---

### Post by d2redneck on 2011-12-06
well I finally figured out what was wrong with my system.  I went into the sound setup and put it on analog duplex from analog speakers and BOOM it worked.

---

