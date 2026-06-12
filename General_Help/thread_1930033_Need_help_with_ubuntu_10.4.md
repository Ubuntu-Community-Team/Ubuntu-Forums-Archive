---
title: "Need help with ubuntu 10.4"
date: 2012-02-23
forum: General Help
---

### Post by jamesdavis111 on 2012-02-23
I'm using ubuntu 10.4 no dual boot. i am new to this but im trying to install a netgear wna3100 wireless adapter(usb) now everytime i try to install it i get this error


Archive:  /media/WNA3100/Autorun.exe
[/media/WNA3100/Autorun.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/WNA3100/Autorun.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/WNA3100/Autorun.exe or
          /media/WNA3100/Autorun.exe.zip, and cannot find /media/WNA3100/Autorun.exe.ZIP, period.

i tried using windows wireless drivers an i get an auto run install error it says invalid driver can someone please help me???? i would appreciate it .

---

### Post by SuaSwe on 2012-02-23
Hi there!

Am I correct in thinking that you're attempting to install an .exe file just as you would on Windows? This will not work on Ubuntu.

Quite often you'll find that devices are picked up automatically and you don't have to do anything (so in this case, try connecting the adapter and checking the network symbol, normally top-right somewhere, to see if it registers wireless availability), and if not it might appear as a restricted driver (see [this link]("http://www.howtogeek.com/howto/17495/how-to-add-proprietary-drivers-to-ubuntu-10.04/")). 

On some occasions you need to install the Windows driver, for which you would use a program called [Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by jamesdavis111 on 2012-02-23
i installed ndiswrapper but how can you tell if it is installed correctly it doesn't pick it up automatically but when i run lsusb it says netgear inc so it must recognize my adapter correct?

---

### Post by raja.genupula on 2012-02-23
> **jamesdavis111 said:**
> i installed ndiswrapper but how can you tell if it is installed correctly it doesn't pick it up automatically but when i run lsusb it says netgear inc so it must recognize my adapter correct?

Hi Even-though your device was recognized by system , if you dont have a interface to work with that particular device .then no use . here the interface is your driver .

If drivers are properly installed then only you can work with the device . how much extent the recolonization of the device can help you is , is that device properly working or not .

so i am looking .exe in the post of you . tell me what are the contents of your pkg .

---

### Post by jamesdavis111 on 2012-02-23
im new to this so im not shore i know for a fact it works becouse i have another pc in the house an it installs and works on it i pulled up my computer and it says teac usb hsms card can you explain what your talking about i just started using this yesterday an both of you thanks for the reply

---

### Post by raja.genupula on 2012-02-23
Ok i got something for you .,
[http://blog.ferhatelmas.com/search/label/Ubuntu](http://blog.ferhatelmas.com/search/label/Ubuntu)

all the best . follow the instructions , if you got something wrong let us know .

all the best ,

---

### Post by jamesdavis111 on 2012-02-23
do you know how to tranfer the driver? also i wrote in sudo ndiswrapper and it says -a devid  use installed driver for devid (dangerous) what does that mean?

---

### Post by raja.genupula on 2012-02-23
> **jamesdavis111 said:**
> do you know how to tranfer the driver? also i wrote in sudo ndiswrapper and it says -a devid  use installed driver for devid (dangerous) what does that mean?

Hi man , actually i havent used that device practically . But i have got something for you which step by step process that have a complete tutorial with example output . 

you can get that from here . [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

but this link and above link have a relation that first you need to get ndiswrapper . 

all the best ,

---

### Post by jamesdavis111 on 2012-02-23
how do you use ndiswrapper?

---

### Post by mastablasta on 2012-02-23
Ubuntu help site: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
USB devices that work with ndiswrapper: [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)

---

### Post by jamesdavis111 on 2012-02-23
can any one tell me how to install all this im really new to this and i dont understand please help i need this explaned please

---

### Post by raja.genupula on 2012-02-23
Hi in the links given by our friend mastablasta all the instructions mentioned clearly to install that app . read the instructions carefully and follow them , if you got problem , post here . we will do our best .


All the best  .

---

### Post by mastablasta on 2012-02-23
> **jamesdavis111 said:**
> can any one tell me how to install all this im really new to this and i dont understand please help i need this explaned please
 
take a look at the first link i posted and read. You can copy and paste those commands into the terminal. you need to be connected to the internet (probably via wire) for the commands to work.
 
commands are used in the guide here because they work on all desktops (e.g. Ubuntu, Kubuntu, Xubuntu...).
 
when all is installed your USB network device should work (if it is compatible with the wrapper).

---

### Post by praseodym on 2012-02-23
Hi,

this stick is shipped with three different chipsets (2x Broadcom, 1x Atheros). Please open a terminal with CTRL+ALT+T and show the outputs of these three commands:

```
lsusb
lsmod
rfkill list
```

---

