---
title: "Hp deskjet f2480 doesn't work"
date: 2009-10-16
forum: General Help
---

### Post by feffo on 2009-10-16
Hello, I've just bought an HP f2480 all-in-one printer and I can't find anywhere a way to install it! I had a good working old hp before and it worked flawlessly with hplip, but this model isn't supported... 
It also doesn't figure here [http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi) so I really don't know what to do!! 
Any help is really appreciated! :D

Thanks ad bye!!

---

### Post by zieglerj on 2009-10-16
Did you install HPLIP? I couldn't get my deskjet 4440 to work. It wasn't even supposed to be suported but after I followed the instructions [here]("http://hplipopensource.com/hplip-web/install/install/index.html"), it just magically started working. 

Hope it works for you!

---

### Post by c-lou on 2009-11-07
Hi,

I am also unsuccessfully trying to get my HP Deskjet F2480 to work with Ubuntu 9.10.

I tried following the instructions at the hplip link you suggested, but it didn't work. The hplib installed fine, but it could not find any printers in step 13 of the instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html).

Are there any other solutions to this problem?

Thanks heaps!

---

### Post by c-lou on 2009-11-08
> **c-lou said:**
> Hi,

I am also unsuccessfully trying to get my HP Deskjet F2480 to work with Ubuntu 9.10.

I tried following the instructions at the hplip link you suggested, but it didn't work. The hplib installed fine, but it could not find any printers in step 13 of the instructions at [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html).

Are there any other solutions to this problem?

Thanks heaps!

OK, it's fixed now :D

I clicked on System -> Administration -> Printing

Then I clicked on the 'New' box at the top of the Printer Configuration window, and selected 'Printer' in the drop-down menu.

Then, after the system 'searched for printers' for a few seconds, it came up with a list including my printer:

HP Deskjet F2400 (serial number)

Then (this is the bit I was missing before) I clicked on the >Connection button in the centre bottom of the window, and selected 'USB'.

After that, I just followed through the instructions and it worked. 

I don't know whether it would have worked if I hadn't already installed hplip.

---

### Post by aviedw on 2010-03-30
Hi i just recently purchased a HP Deskjet F2480 and i cant seem to get it to work. Even with the help of this thread i have not managed to get the printer to work correctly. I tried the traditional method of adding the printer and search the data base but the closest drivers that i managed to find were for the f2200 series and those dont seem to work at all. Im currently downloading the file that zieglerj suggested and im going to try that now. I will report back. I hope this works.thanks in advance.


***update***

The second posted instructing is what worked for me as far as getting the prining to work, Now im trying to get the copying function to work as well.

---

### Post by amoun on 2012-03-19
Installing on EEEPC 900 (Hardy 8.04) 

1. I removed the hplip that I installed via synaptic as it didn't work

2. Went to [http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) downloaded latest version and ran from terminal as directed.

3 During install I got a message saying that another version was still recognised but it automatically dealt with it

4. During the auto download of files needed I got an error 100 for the three following as they couldn't be found
[ lipcups2-dev, cups-bsd, cups-client ]
I opted to not install them.

5. The install carried on with warnings about loss of functionality but printing worked for my HP 2400 series.Well black anyway - must check there's colour ink :)

6. Once working I checked, via synaptics, for above missing files and found cupsys-bsd and cupsys-client but nothing like lipcups2-dev

Thanks

---

