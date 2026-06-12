---
title: "Install canon pixma 6150"
date: 2012-05-13
forum: General Help
---

### Post by samwillc on 2012-05-13
Hi everyone,

I went to the canon website and downloaded:

MG6100series-printer_driver.tar AND MG6100series-scanner_driver.tar

These are linux drivers for my printer/scanner. As I've said before this is all new to me, what do I do with the files? This is not a case of double clicking a windows .exe file!

How do I install the drivers? Any help is most appreciated. Thanks.

Sam.

---

### Post by JC Cheloven on 2012-05-13
Hi, please first of all, try to simply plug-in the device (scanner or printer), and try to use it. Chances are that the driver is already included in the kernel!

---

### Post by samwillc on 2012-05-13
Thanks but it's wireless.

I tried a scan network for printers but results returned nothing.

Sam.

---

### Post by JC Cheloven on 2012-05-13
Ok, then :)

A tar file is an archiver, something like a zip file, most likely with several files compressed inside. First thing is to unpack it. You can simply right-click on the file and select "Extract here". You'll get a new folder in the current directory. Hopefully there will be a README text file, which will help. 

Usually, that readme file will guide you by a process which basically cosists in running a couple of commands (something like "make" and "make install"), but let's see first what is actually there.

---

### Post by samwillc on 2012-05-13
Ok great, thanks.

First folder I 'extracted here' same as I would do in windows, contains:

MG6100series-printer_driver (folder)

which contains:

cnijfilter-mg6100series-3.40-1-deb.tar.gz
cnijfilter-mg6100series-3.40-1-rpm.tar.gz
guidemg6100series-pd-3.40-1_en.tar.gz

guidemg6100series-pd-3.40-1_en.tar.gz <---- this contains an html guide of how to use the printer, which has a load of instructions :)) looks promising, starts thus:

**For Ubuntu 10.04** ** 1) Expanding the archived file and switching to the expanded directory**
 [B] [user@zzz /yyy]$ tar zxvf cnijfilter-mg6100series-3.40-x-deb.tar.gz
[user@zzz /yyy]$ cd cnijfilter-mg6100series-3.40-x-deb[/B]
 ** 2) Installing the printer driver**
 ** [user@zzz /yyy]$ sudo ./install.sh**
 
 ** When the installation is completed, a message instructing you to register the printer is displayed.**
 [B] Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
>[/B]
 ** Check that the machine is properly connected and that the power is on. Then press the Enter key.**
  
It goes on step by step so I think I should be able to follow it. I presume this will work with 12.04?!

Sam.

---

### Post by samwillc on 2012-05-13
I found it quite awkward with the commands 'cd <DIRECTORY NAME>' as the folders were named with such complicated names!

Instead, I just extracted the folder with deb in the title, and double clicked on the install.sh. 
Terminal opened, followed the instructions, and printed test page, success!

Sam.

---

### Post by JC Cheloven on 2012-05-13
Glad to hear that. Congrats!

Hope you'll enjoy the linux experience as much as I do, despite some "not straightforward" hardware. We have to cope with that now and then, but things are improving as more people use gnu-linux. 

Best
JC

---

