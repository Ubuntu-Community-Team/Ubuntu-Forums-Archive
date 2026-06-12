---
title: "Problem with opeing data.cab files"
date: 2010-06-24
forum: General Help
---

### Post by JungleBugie on 2010-06-24
Hi I am new to Ubuntu, I just installed version 10.04 on my Dell studio 1749 and I have problems with installation of wireless drivers. I have tried to solve it by a few methods I found on forums, however it didn't help me so far. Now I am trying to deal with it using ndiswrapper and here comes the problem, to do it I need unpacked .inf and .sys files and so far i could not get them. I tried to find a driver in the internet in ZIP form - failure. I also tried to get the files that are installed in windows folders, and they are not there. Finally I managed to unpack the driver.exe however I cant find a way to open the data.cab files inside it, I Tried to open them in Windows with 7-zip, WInzip and Winrar, plus I Tired to do it on Linux with Unzip Unishield and Cabextractor. All these programs seem to be able to open the other cab files in Drive.exe but not the ones named data1.cab data2.cab etc.

If anyone knows how to open these files please helm me ;)

I have Dell Wireless 1397 Half Mini-card
Terminal recognizes it  as Broadcom B4312

And there is link to the driver I am dealing with:
> [http://ftp.us.dell.com/network/R238145.exe](http://ftp.us.dell.com/network/R238145.exe)PS- Sorry if started this tread in wrong category but I could not find a proper one for it ;/

---

### Post by dandnsmith on 2010-06-24
If you've ever had the wireless stuff working on that PC under Windows, then the .inf file should be present in the \WINDOWS\inf folder. I don't know what the relevant name would be for it, but suggest you look in device manager for clues in the device properties (posibly drivers). I certainly found it easily enough for my netbook.

---

### Post by Javich on 2010-06-24
Dude, try this:

Open a terminal, then type ```
sudo apt-get install cabextract
```.
Once you have done this the "usual" gnome tool will know how to use cab files, just right click on it and then "extract here".

Cheers,
Javier

---

### Post by pbrane on 2010-06-24
The Broadcom 4312 should be supported in linux b43 driver. Or you can get the Broadcom driver from here:
[http://www.broadcom.com/support/802.11/linux_sta.php]("http://www.broadcom.com/support/802.11/linux_sta.php")

I bought an Intel wireless card for $20 and replaced my BCM card. I have a Dell Inspiron 1720 and the Intel card works great. It's up when the kernel boots.

---

