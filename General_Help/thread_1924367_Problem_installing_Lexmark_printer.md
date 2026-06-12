---
title: "Problem installing Lexmark printer"
date: 2012-02-12
forum: General Help
---

### Post by TinkerTaylor on 2012-02-12
Have a Lexmark C534n, am running 11.10 (Gnome), and they are connected over my local network.

I've downloaded the drivers from Lexmark's site and installed them from the terminal using sudo dpkg. No problems so far. Then one needs to run the "Lexmark Print Drivers" utility that has appeared under System Tools. I find the printer on the network alright, but then I guess you need to create a queue and associate it with the printer/device. Here I get the error message "Printer Name Already Exists !" when I try to create a queue for the device. I don't understand which name the error message refers to since I've called the printer/device "Lexmark_C534" and I haven't used that name anywhere else. 

This happens regardless whether I'm running the Lexmark utility from the Applications meny or from command line (with "sudo lexprint").

Googling gave nothing. 

I'm quite new to this Ubuntu/Linux thing so no advice or suggestions are too simple!

---

### Post by jasonrisenburg on 2012-02-12
It seems that since the 11.10 release, it has not really been working to well for anyone. From what I read they dont really support it from the manufacture. here is a few links I found that I was looking at. 
[http://askubuntu.com/questions/70363/driver-for-lexmark-x7675-printer](http://askubuntu.com/questions/70363/driver-for-lexmark-x7675-printer)
[http://wiki.winehq.org/Printing](http://wiki.winehq.org/Printing)
[http://patchlog.com/patches/ddiwrapper-on-ubuntu-9-04/](http://patchlog.com/patches/ddiwrapper-on-ubuntu-9-04/)

---

### Post by jerrrys on 2012-02-12
I have used Lexmark in the past and found out that they work great; after about two days of screwing with one.  If you call the support line and get Italy; hang up.  Those people told me lexmark will not support Linux.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Lexmark+C534n&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Lexmark+C534n&sa=Search&cof=FORID:9)

---

### Post by hvieren on 2013-03-08
i succeeded to use 

lexmark printer drivers drivers-lexprtdrv
with problems:
 Error:Print Queue already exists
lpadmin:Unable to copy interface script
in ubuntu 12.10 

see

 [http://www.opengov.be/ubuntu-1210-lexmark-printer-drivers-drivers-lexprtdrv-errorprint-queue-already-existslpadminunable-c](http://www.opengov.be/ubuntu-1210-lexmark-printer-drivers-drivers-lexprtdrv-errorprint-queue-already-existslpadminunable-c)

---

