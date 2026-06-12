---
title: "screen problem"
date: 2010-06-03
forum: General Help
---

### Post by croccio on 2010-06-03
last month i spoke about screen problem! it is very frequentely now =( i read the guide but they doen't resolve my problem =( how can i do??? the desktop crashes with the live cd =( i don't play! i'm navigate on internet! in 1 hour my desktop crashes 5 times! =(

---

### Post by Kevbert on 2010-06-03
Please run memtest86+ from the Ubuntu installation CD. If you get any errors it may be due to bad memory (Windows may work but crash occasionally for no apparent reason).

---

### Post by croccio on 2010-06-03
how it works??? can u explain please??

---

### Post by croccio on 2010-06-03
i've done it! it passes wothout errors!

---

### Post by Kevbert on 2010-06-04
Good. With the PC turned off please check that the display adapter card is properly seated in the motherboard (if it's not on the motherboard) and is not loose and also check any cable connections are tight.
Regarding the crashes. How did you make the Ubuntu CD ? Did you burn it at a slow speed (2x) and did you perform a checksum on the downloaded file ?
When do the crashes occur ? at the same point of installation of Ubuntu ? or when running the same program ?

---

### Post by croccio on 2010-06-04
> With the PC turned off please check that the display adapter card is  properly seated in the motherboardthis it's ok!
> How did you make the Ubuntu CD ?with nero express on windows xp> Did you burn it at a slow speed (2x) and did you perform a checksum on  the downloaded file i set it the default option! i don't do a checksum on the downloaded file!> When do the crashes occur ? at the same point of installation of Ubuntu ?  or when running the same program ?i'm writing from ubuntu! i install ubuntu! the crashes occur when i run games as zaz, xmoto, supertuxracer and other games!!! only pereinstalled games work!!! it crashes when i'm navigate on internet or i'm working with open office!!

---

### Post by Kevbert on 2010-06-04
OK. Please be a little more specific when reporting a problem (with more detail). Please go to the Applications-Accessories-Terminal and enter the following command 
```
sudo apt-get install -f
```
and post back here any reported problems. This will detect any broken packages/programs.
Also what is the make and model of your video adapter ? You can get this via terminal with
```
lspci
```
Have you installed any display driver ? The display may seem to be OK or may be offset to the right without the driver. You can install a driver for the display by going to System-Admin-Hardware Drivers. If it recommends a graphic driver select that one (it may take several minutes to download). Next reboot the PC and report back any problems.

---

### Post by croccio on 2010-06-04
sudo apt-get install -f
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.

lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
05:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
> Have you installed any display driver ? no!>  You can install a driver for the display by going to  System-Admin-Hardware Drivers. If it recommends a graphic driver select  that one (it may take several minutes to download). Next reboot the PC  and report back any problems.ir don't search any driver!

---

### Post by croccio on 2010-06-04
look this video! i'm running super tux kart! my screen crash!
[http://www.youtube.com/watch?v=v81b6iray5w](http://www.youtube.com/watch?v=v81b6iray5w)
if i reboot my compuer from the botton then my compuer turn on in blue screen (screen of death)!!! 



lokk thi video too!!! when i turn on my compuer it show me some write!
and when i turn off it it shows other write!
[http://www.youtube.com/watch?v=aotv0Yf9dEo](http://www.youtube.com/watch?v=aotv0Yf9dEo)

---

### Post by dino99 on 2010-06-04
remove xorg.conf if any, into a console:

sudo rm -f /etc/X11/xorg.conf

you need to check the video driver: system admin hardware driver, is it activated ?

which graphic/chipset card is in use ?

If you really want to know why your system crash, you have to glance at logs:

- into /home : .xsession-errors (unhide it with menu)
- into "system admin log viewer": watch and search errors in the logs

---

### Post by croccio on 2010-06-04
> ystem admin hardware driver, is it activated ?
here is a screen
[IMG]http://dl.dropbox.com/u/7688709/driver.png[/IMG]
> which graphic/chipset card is in use ?i don't know! how can i see?
[COLOR=Red]**.xsession-errors**[/COLOR]
download from [here]("http://dl.dropbox.com/u/7688709/.xsession-errors")

---

### Post by Kevbert on 2010-06-04
It may be that you need to activate some software sources first. Close that window and then select System-Admin-Software Sources. Make sure that Restricted and Multiverse Repositories are ticked (see attachment). If not select them so that the boxes are ticked as shown. If you have ticked any of these boxes the PC will ask you to reload the repositories. Assuming that you have made changes now go back to System-Admin-Hardware Drivers and you should see a list of recommended drivers.

---

### Post by croccio on 2010-06-04
i've them chec but dontt show nothing in drive hrdware

---

### Post by croccio on 2010-06-05
help me please =(

---

### Post by Kevbert on 2010-06-05
This adapter has been causing problems in the past especially with Compiz (the rotating cube) and screensavers. Please take a look at [http://www.backports.ubuntuforums.org/showthread.php?t=1448684](http://www.backports.ubuntuforums.org/showthread.php?t=1448684)
You can enable the backports repository by going to System-Admin-Software Sources and selecting the Updates Tab. Click on Unsupported Updates so that it's ticked.

---

### Post by croccio on 2010-06-07
i've done it but anything is changed =(

---

