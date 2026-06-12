---
title: "Updated dial-up modem list"
date: 2011-06-28
forum: General Help
---

### Post by Je Et on 2011-06-28
Although Ubuntu says it is for everyone, it seems to be for everyone except for people with dial-up. When searching I run across people saying 'you should just get DSL', and all the how-tos  are from 2008 or earlier. Telling me about DSL when I'm trying to find out about dial-up is like giving me beer when I asked for water. If I had the knowledge or the expertise to write a how-to, I would, but I am not blessed with that gift. I thank the programmers and the creators of Ubuntu for all the work and effort they have put into this wonderful distro, to make it available for the rich and poor alike (except for those of us with dial-up). I am posting this using **Windoze XP** because the only modem I have is **conexant** modems (pci and external usb) and **Windoze 7** does not support them, neither does Ubuntu 11.04 it seems, and I paid $19.99 USD to [COLOR=#333333][FONT=arial]l**inuxant** for the full speed driver. I guess I'll just have to save up and get another **Agere** modem,as this winmodem has worked with every version of Ubuntu I have used, including 11.10, which leads me to the reason I wrote this post:

**_Agere modem - martian_**
[/FONT][/COLOR][COLOR=#333333][FONT=arial]With Ubuntu it w[/FONT][/COLOR][COLOR=#333333][FONT=arial]orks with wvdial at full speed, but I haven't been able to able to make gnome-ppp recognize it.

[/FONT][/COLOR][COLOR=#333333][FONT=arial]**_Agere modem - _**[/FONT][/COLOR]_**agrsm**_
[COLOR=#333333][FONT=arial]With Ubuntu it w[/FONT][/COLOR][COLOR=#333333][FONT=arial]orks with wvdial at full speed and gnome-ppp **will **recognize this one.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial] 
**_conexant chipset - hsfmodem_**

Worked with Ubuntu up to 10.10, but at half speed unless you buy their driver.  I could not get it to compile with 11.04.

If anyone has any to add, please do.

  
[/FONT][/COLOR]

---

### Post by gordintoronto on 2011-06-28
Could you tell us what error message you got when trying to compile?

---

### Post by Je Et on 2011-06-28
Here is the buildlog:

```
driver version 7.80.02.06full
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.38-8-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/2.6.38-8-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.38-8-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1320:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1369:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_7800206full_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1396:1: warning: the frame size of 1028 bytes is larger than 1024 bytes
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408:8: error: 'MUTEX' undeclared here (not in a function)
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2
```

---

### Post by frank cox on 2011-09-08
Check this thread out. I have found those cheap USB winmodems sold on ebay for 12.00 or less delivered are recognized  well on every Linux distro I have tried them on. They seem to like 460800 best. Great solution for a laptop.
There are some commands you have to know to get the right permissions and all that info is available on this thread :

[SOLVED] 			 			[Permission Problem Gnome-PP]("http://ubuntuforums.org/showthread.php?t=1839620&highlight=gnome-ppp") 			 		  		  		 			 			 				frank cox

It took me 2 hours to get the first one to work, the next 10 minutes.

---

### Post by Denver Dave on 2011-09-11
i think I have a similar issue.  I'm trying out 11.04 from the disk from "The Official ubuntu Book".   Seems to detect my Cable modem connection just fine, but don't find anything for my dial-up modem.   I use the dial-up as a backup and also I'm researching if Ubuntu can be used on a 2nd PC with just a dial-up.

I've found System / Administration / Network tools, but this does not list connections.

I found this page: "Setting up a dial-up connection in Ubuntu"
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
which references a page for System / Administration / Networking (not Network tools) which is supposed to show the dial-up modem option.

Suggestions??

Thanks.

---

### Post by gordintoronto on 2011-09-11
You might also look at this:
[http://www.pcurtis.com/ubuntu-mobile.htm](http://www.pcurtis.com/ubuntu-mobile.htm) contains information ranging from dial-up on land lines to mobile broadband USB sticks.

---

### Post by doogie544 on 2011-09-11
[LEFT][SIZE=2]**Zoom USB Mini External modem  Model #3095**[/SIZE]
[/LEFT]
 
It works with Natty and is recognized by Gnome-ppp and Kppp
I have been able to get better connections with this that with the PCI that is in my computer(junk winmodem)  when I was using Windozzz.  I don't think I've connected at less than 40,000 and more often 44+  the PCI was lucky to get me 40 most of the time.

I found mine at my local Walmart for $45.  Might have been able to get it cheaper online but wanted a place I could return it if it didn't work.  Here is the link if it is any help...

 [http://www.walmart.com/ip/Mini-External-V.92-Analog-Voice-Fax-Modem/15042273](http://www.walmart.com/ip/Mini-External-V.92-Analog-Voice-Fax-Modem/15042273)

Hope this helps.

---

