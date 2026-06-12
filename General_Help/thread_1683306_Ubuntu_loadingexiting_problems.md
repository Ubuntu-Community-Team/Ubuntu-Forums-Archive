---
title: "Ubuntu loading/exiting problems"
date: 2011-02-07
forum: General Help
---

### Post by teaquack on 2011-02-07
I had Windows 7 installed on my laptop. I decided to install Ubuntu parallel to it. I'm running Ubuntu 10.04. Sometimes when I load Ubuntu it goes to either black screen with white underscore or to a grayish gradient that gradually changes color and it stops there. Sometimes this happens when I reload from Ubuntu. I have to press the button on the keyboard to turn off the laptop and then turn it on again and sometimes it loads normally.

I installed Ubuntu right after I got my laptop, so Windows 7 was clean at the time. Also, Windows loads and exits without problems.

I'm new to Ubuntu and can't figure out the problem. Also couldn't find anything helpful on the Internet. Any help appreciated, would like to resolve this. =(

---

### Post by ahsan101 on 2011-02-07
Did it gave you or prompted for something? Also which bootloader is actually working? If it is Grub then press and hold SHIFT while computer starts and fromt he Grub menu go to recovery mode and look for log files then. Hope it helps.

---

### Post by quadproc on 2011-02-07
> **teaquack said:**
> I had Windows 7 installed on my laptop. I decided to install Ubuntu parallel to it. I'm running Ubuntu 10.04. Sometimes when I load Ubuntu it goes to either black screen with white underscore or to a grayish gradient that gradually changes color and it stops there. Sometimes this happens when I reload from Ubuntu. I have to press the button on the keyboard to turn off the laptop and then turn it on again and sometimes it loads normally.

You might be experiencing a problem which I have on version 10.10 - the symptoms sound similar.

Which graphics driver are you using?  What kind of graphics hardware does your system use?

I found that this problem occurs for me with the default open source driver but not when I use the proprietary driver for my graphics card.  See launchpad bug # 7110566 for the details.

quadproc

---

### Post by teaquack on 2011-02-09
**quadproc**, I opened Hardware Drivers and installed ATI/AMD proprietary FGLRX graphics driver. I think my graphics card is Redwood [Radeon HD 5600 Series]. The proprietary driver helped, although not completely. Now I only get black screen with blinking underscore and the keyboard works (Num Lock and CTRL+ALT+DELETE work). Looked up launchpad bug # 7110566 and yes, this does seem like my problem.

What graphics card do you have? Did the problem go away completely after you installed proprietary driver?

**ahsan101**, I have Grub bootloader working. I can do this, but I don't know what I need to look for in logfiles...

---

### Post by quadproc on 2011-02-09
> **teaquack said:**
> **quadproc**, I opened Hardware Drivers and installed ATI/AMD proprietary FGLRX graphics driver. 
This means that you did not get a chance to choose which driver version was loaded, right?
> 
I think my graphics card is Redwood [Radeon HD 5600 Series]. If you type into a terminal window
```
lspci | grep ATI
``` you will see what model number you have.

> 
The proprietary driver helped, although not completely. Now I only get black screen with blinking underscore and the keyboard works (Num Lock and CTRL+ALT+DELETE work). Looked up launchpad bug # 7110566 and yes, this does seem like my problem.

What graphics card do you have? Did the problem go away completely after you installed proprietary driver?I am running two HD4870 cards.  With fglrx installed the problem appears to be gone completely.  However, I have uninstalled fglrx for the moment because I wish to be able to try out any bug fixes that may be forthcoming.  I am now running the default open source driver, and every so often, I get the failure to display a proper login window.

quadproc

---

### Post by teaquack on 2011-02-16
Ok. My problem evolved.

Every time I reload from Ubuntu, it doesn't go to Grub. It goes to black screen with blinking underscore. I waited a while after that and it gave me this:

Reboot and select proper Boot device
or Insert Boot Media in selected Boot device and press a key

I searched the problem and it doesn't seem to be an easy fix. Would I have to reinstall something? It would be nice to have an option somewhere to tell to go load to Grub in that case. After I shut down the laptop and turn it back on, it loads to Grub fine. It also reloads fine from Windows.

---

### Post by teaquack on 2011-03-02
Up. I still have this problem, any suggestions?

---

