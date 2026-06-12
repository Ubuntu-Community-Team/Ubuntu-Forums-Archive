---
title: "Wireless Adapter not working! :("
date: 2012-03-14
forum: General Help
---

### Post by SystemsGO on 2012-03-14
hey guys first post here. i just installed ubuntu with a dual boot of windows 7. i can't get my wna wireless adapter to work on ubuntu. i tried following this guide, but it didn't the link for the download did not work. i can't find it anywhere else. anyone else able to help me get this working? thanks!

My wireless adapter is a wna3100 model by Netgear.

[http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter](http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter) This was the tutorial I tried following. But the url for the driver download fails?

---

### Post by Bucky Ball on 2012-03-14
Have you plugged in an ethernet cable, gotten online, gotten updates and checked 'Additional Drivers' (or 'Hardware Drivers' depending on release).

If it's a USB dongle make sure it is plugged in while getting updates.

---

### Post by SystemsGO on 2012-03-14
> **Bucky Ball said:**
> Have you plugged in an ethernet cable, gotten online, gotten updates and checked 'Additional Drivers' (or 'Hardware Drivers' depending on release).

If it's a USB dongle make sure it is plugged in while getting updates.


yes, i have an ethernet cable plugged in now. i just checked the update manager, there no updates to install. i checked additional drivers and there are no drivers that need to be installed. 

any ideas?

---

### Post by Bucky Ball on 2012-03-14
What release are you using?

---

### Post by SystemsGO on 2012-03-14
> **Bucky Ball said:**
> What release are you using?

sorry about that. i'm using ubuntu 11.10 with unity.

---

### Post by SystemsGO on 2012-03-14
> **SystemsGO said:**
> sorry about that. i'm using ubuntu 11.10 with unity.

Here is the tutorial I originally tried to following. The problem with this is that the URL for the file download fials. [http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter](http://askubuntu.com/questions/48563/could-anyone-help-me-get-my-netgear-wna3100-broadcom-bcm43231-wireless-adapter)

---

### Post by SystemsGO on 2012-03-14
Anyone?

---

### Post by jerome1232 on 2012-03-14
Do you still have the installation cd for the dongle? You may want to give ndiswrapper a try.

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

---

### Post by SystemsGO on 2012-03-14
> **jerome1232 said:**
> Do you still have the installation cd for the dongle? You may want to give ndiswrapper a try.

[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)


I download NDIS Wrapper, and I do still have the installation CD. I'm not quite sure what to do with either at this point?

---

### Post by jerome1232 on 2012-03-14
Basically you need to use the cd to install the driver into a Windows environment, from the site i linked

> If you install cd that comes with the adapter on Windows 64 bit machine, files of the driver is installed to C:\Program Files (x86)\NETGEAR\driver\WIN764 and its name is bcmwlhigh6.

If you install it on 32 bit, you will already get correct driver, bcmwlhigh5. However, you use it under ndiswrapper on 64 bit Ubuntu, you will get a lot of uninitialized variables. 

You need to use ndiswrapper to install that driver file.

something like

```
sudo ndiswrapper -i /path/to/inf/file
```

If you check that link I gave it gives examples and tells you what to do should you encounter certain errors. Hopefully that gives you a nudge in the right direction.

edit: Sorry if I'm clear as mud, I'm trying I really am

If you don't have a windows environment (real or in virtualbox maybe) you may be able to find the correct inf file with some dedicated googling.

---

### Post by SystemsGO on 2012-03-14
> **jerome1232 said:**
> Basically you need to use the cd to install the driver into a Windows environment, from the site i linked



You need to use ndiswrapper to install that driver file.

something like

```
sudo ndiswrapper -i /path/to/inf/file
```

If you check that link I gave it gives examples and tells you what to do should you encounter certain errors. Hopefully that gives you a nudge in the right direction.

edit: Sorry if I'm clear as mud, I'm trying I really am

If you don't have a windows environment (real or in virtualbox maybe) you may be able to find the correct inf file with some dedicated googling.

Okay, it says that my driver is installed, but I still can't connect or find my wireless network?

---

### Post by jerome1232 on 2012-03-15
Maybe this will help you with configuring it, (mostly section 3, blacklisting anyother drivers) also have you tried rebooting?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I've only messed with ndiswrapper once, so I can't provide real hands on help, I'm just trying to get you pointed in the right direction with things I would be trying.

---

### Post by jerome1232 on 2012-03-15
Also posting the output of the below code may be helpful

```
ndiswrapper -l
```

---

### Post by SystemsGO on 2012-03-15
> **jerome1232 said:**
> Also posting the output of the below code may be helpful

```
ndiswrapper -l
```

~$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9020) present
bcmwlhigh6 : invalid driver!


Just so you know this is the 64 bit version of Ubuntu. 

[http://forum.linuxmint.com/viewtopic.php?f=53&t=79209](http://forum.linuxmint.com/viewtopic.php?f=53&t=79209)

I tried to follow this guide, to no avail. 

When I open the GUI Windows Driver installation program it still says it's invalid, but that it's present

---

### Post by Bucky Ball on 2012-03-15
Read post #3 here:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/networking-woes-with-netgear-wna3100-in-kubuntu-11-10-a-916105/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/networking-woes-with-netgear-wna3100-in-kubuntu-11-10-a-916105/)

Like most pages on this, seems you need to use bcmwlhigh5 not bcmwlhigh6. There is a link to download it there also. If you're still stumped try digging through this:

[http://www.google.com.au/#hl=en&sclient=psy-ab&q=wna3100+ubuntu+11.10&oq=wna3100+ubuntu+11.10&aq=f&aqi=g1g-m1&aql=&gs_sm=3&gs_upl=4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0&gs_l=hp.3..0j0i5.4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597](http://www.google.com.au/#hl=en&sclient=psy-ab&q=wna3100+ubuntu+11.10&oq=wna3100+ubuntu+11.10&aq=f&aqi=g1g-m1&aql=&gs_sm=3&gs_upl=4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0&gs_l=hp.3..0j0i5.4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597)

It does appear, though, that the only way people have gotten this working is with the old warhorse ndiswrapper. Strange, as Broadcom is generally well supported nowadays ...

---

### Post by SystemsGO on 2012-03-15
> **Bucky Ball said:**
> Read post #3 here:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/networking-woes-with-netgear-wna3100-in-kubuntu-11-10-a-916105/](http://www.linuxquestions.org/questions/linux-wireless-networking-41/networking-woes-with-netgear-wna3100-in-kubuntu-11-10-a-916105/)

Like most pages on this, seems you need to use bcmwlhigh5 not bcmwlhigh6. There is a link to download it there also. If you're still stumped try digging through this:

[http://www.google.com.au/#hl=en&sclient=psy-ab&q=wna3100+ubuntu+11.10&oq=wna3100+ubuntu+11.10&aq=f&aqi=g1g-m1&aql=&gs_sm=3&gs_upl=4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0&gs_l=hp.3..0j0i5.4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597](http://www.google.com.au/#hl=en&sclient=psy-ab&q=wna3100+ubuntu+11.10&oq=wna3100+ubuntu+11.10&aq=f&aqi=g1g-m1&aql=&gs_sm=3&gs_upl=4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0&gs_l=hp.3..0j0i5.4003l5106l2l5617l6l6l0l0l0l0l255l1443l2-6l6l0.&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=4887cfbcfb0a79dc&biw=1024&bih=597)

It does appear, though, that the only way people have gotten this working is with the old warhorse ndiswrapper. Strange, as Broadcom is generally well supported nowadays ...

Well, it's too late for that now. I already completely removed Ndiswrapper from my system. I've been trying to follow a different guide for reinstalling it now, but I keep getting errors trying to install ndiswrapper-1.57 from the source files.

 make -C utils
make[1]: Entering directory `/home/kolton/ndiswrapper-1.57/utils'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/kolton/ndiswrapper-1.57/utils'
make -C driver
make[1]: Entering directory `/home/kolton/ndiswrapper-1.57/driver'
make -C /usr/src/linux-headers-3.0.0-17-generic M=/home/kolton/ndiswrapper-1.57/driver
make[2]: Entering directory `/usr/src/linux-headers-3.0.0-17-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make[1]: Leaving directory `/home/kolton/ndiswrapper-1.57/driver'
-TZ68A:~/ndiswrapper-1.57$ make install
make -C driver install
make[1]: Entering directory `/home/kolton/ndiswrapper-1.57/driver'
mkdir -p -m 755 /lib/modules/3.0.0-17-generic/misc
mkdir: cannot create directory `/lib/modules/3.0.0-17-generic/misc': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/kolton/ndiswrapper-1.57/driver'
make: *** [install] Error 2


Do you know how to fix this?

---

### Post by Bucky Ball on 2012-03-15
You need to either use:

```
sudo make
```... and sudo before all commands or use:

```
sudo su
```... which will make you root until you exit then input your commands. For instance:

```
sudo make -C utils
```

or:

```
sudo su
make -C utils
etc ...
```

Is the solution that simple?

---

### Post by SystemsGO on 2012-03-15
> **Bucky Ball said:**
> You need to either use:

```
sudo make
```... and sudo before all commands or use:

```
sudo su
```... which will make you root until you exit then input your commands. For instance:

```
sudo make -C utils
```

or:

```
sudo su
make -C utils
etc ...
```

Is the solution that simple?

Well, that did fix it. Logging in as root allowed me to install it. However, it installed version 1.56 as opposed to 1.57. 

I navigated to my source files(1.57) which cd ./ndiswrapper-1.57
Then did a "Make uninstall"
Then "Make"
Then logged in as root and did "make install"--- Everything seems fine at this point.

So I check my version "Ndiswrapper -v" Shows version 1.56 and not version 1.57(which I want to install from the source files). 

Sorry for being such a noob and bothering you with this. 

I tried to continue on anyway.. After that I did lsusb, it shows my device is present and my drivers are installed.. So I'm doing a mod probe, and it just hangs forever. 

Anyway to be sure I install version 1.57?

---

### Post by SystemsGO on 2012-03-15
> **SystemsGO said:**
> Well, that did fix it. Logging in as root allowed me to install it. However, it installed version 1.56 as opposed to 1.57. 

I navigated to my source files(1.57) which cd ./ndiswrapper-1.57
Then did a "Make uninstall"
Then "Make"
Then logged in as root and did "make install"--- Everything seems fine at this point.

So I check my version "Ndiswrapper -v" Shows version 1.56 and not version 1.57(which I want to install from the source files). 

Sorry for being such a noob and bothering you with this. 

I tried to continue on anyway.. After that I did lsusb, it shows my device is present and my drivers are installed.. So I'm doing a mod probe, and it just hangs forever. 

Anyway to be sure I install version 1.57?

It may be a Kernel issue. It says in the ndiswrapper readme I need a recent kernel, at least 2.6.1. With header files for the directory. Here is my kernel version. 
3.0.0-17-generic

Should I update the headers and kernel to 3.1 just incase?

---

### Post by Bucky Ball on 2012-03-15
> **SystemsGO said:**
>  It says in the ndiswrapper readme I need a recent kernel, at least 2.6.1. With header files for the directory. Here is my kernel version. 
3.0.0-17-generic



You have a very recent kernel and way beyond 2.6.1 so wouldn't imagine that is the problem.

---

### Post by SystemsGO on 2012-03-15
> **Bucky Ball said:**
> You have a very recent kernel and way beyond 2.6.1 so wouldn't imagine that is the problem.

I fixed it, my card now works. It just wont reinitialize after logging out.

Edit: Fixed that too.

---

### Post by Bucky Ball on 2012-03-15
Great news. Enjoy! ;)

---

