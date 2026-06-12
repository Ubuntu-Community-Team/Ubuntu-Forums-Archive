---
title: "Out of my depth - HELP!!!"
date: 2011-07-04
forum: General Help
---

### Post by User1138 on 2011-07-04
Ok, here's my problem.

I installed Ubuntu 11.04 and lo and behold, the Network Manger app wasn't letting me connect yo my wireless network. After browsing threads on this forum, I decided to uninstall Network Manager and install wcid 1.7.0

Installed wcid, but now when I restart Ubuntu I get the following message after typing in my password for wcid:

"Could not connect to wcid's D Bus interface. Chech the wcid log for error messages."

What do I do? Bear in mind I'm a complete and total novice to Linux. Only just worked out how to change directories in the terminal, so it's a small miracle I made it this far. So, where do I go from here? 

Any help would be appreciated, as I really really want to switch from Windows to Linux.

---

### Post by gandaran on 2011-07-04
what about the wireless card driver? does it need to install drivers or should the wireless just work?
if you don't know the wireless device chip brand type in terminal
```
lspci
```
post the output

---

### Post by in-dust-rial on 2011-07-04
hey crash kid,

:)
seems like you are learning things by exploring all options.

about logs:
[http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/](http://www.cyberciti.biz/faq/ubuntu-linux-gnome-system-log-viewer/)
maybe the wcid log is somewhere else, but i think it should not.

especially keep
[HTML]=> /var/log/dmesg : Linux kernel ring buffer log[/HTML]
this log in mind.
typing dmesg will display it to your command window.
normally the first thing to check if things are going bad or are not working.
see link for detailed information:
[http://www.linfo.org/dmesg.html](http://www.linfo.org/dmesg.html)

within logs there is hopefully enough information to fuel a detailed google search :)

good luck

ps:
if you install your /HOME directory onto another partition, you might be less frustrated next time you have to reinstall linux :)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
or 
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by User1138 on 2011-07-04
The wireless should just work. When Network Manager was installed, it detected the wireless network I wanted to connect to, but it just wouldn't accept my security key. And yes, before you ask, I checked to make sure I'd typed it in correctly countless times. I have absolutely no clue what to do.

---

### Post by User1138 on 2011-07-04
Guess I'll keep on trying. Learning by doing seems to be the best way forward. At least then I earn myself some techie points :P

Thanks for the help guys.

---

### Post by gandaran on 2011-07-04
> **User1138 said:**
> The wireless should just work. When Network Manager was installed, it detected the wireless network I wanted to connect to, but it just wouldn't accept my security key. And yes, before you ask, I checked to make sure I'd typed it in correctly countless times. I have absolutely no clue what to do.
maybe you haven't the right driver or firmware, I would still like to see the output of 'lspci'

---

### Post by gandaran on 2011-07-04
what type of security do you have on wireless? wpa, wpa2 or both?

---

### Post by User1138 on 2011-07-04
Unless someone can help me, I'm never touching Linux again with a ten foot barge pole. 

Installed Ubuntu 11.04.

Network Manager wouldn't connect to my wireless network. Uninstalled it, tried to install wicd, but keep getting error messages about the DBUS not working or some pile of crap.

Can't reinstall Network Manager. Can't uninstall the botched wicd I have at the minute. Don't have a clue what people are going on about with regards to typing commands in the terminal. I'm a computer user, not a computer scientist.

Any help at all? In words I can understand?

---

### Post by 3Miro on 2011-07-04
Have you tried "Additional Drivers" also called "jockey". You probably need an extra driver for your wireless. Although it is possible that the hardware manufacturer did not provide a driver nor needed specifications, so some wireless cards don't have drivers for Linux.

If you have trouble installing/uninstalling programs you can try "Synaptic Package Manager". It gives you a more fine control over what you install, although it is more complicated than the Software Center.

---

### Post by CrusaderAD on 2011-07-04
What kind of machine are you using? I've installed Ubuntu on probably about 50 different machines and haven't had this kind of problem before. Are you using some strange "alien" ware or converted mac hardware? Mac uses hardware designed for Mac's OS. Maybe try doing a little research. If you don't want to do that, if you don't like learning, then go to a technically savy person to setup your machine... regardless of what OS you put on it.

---

### Post by walt.smith1960 on 2011-07-04
3Miro is giving you good advice.  Open Symantic in a SUDO account (administrator in Windows) then open Synaptic package manager, search for"WICD", click it then uninstall.   Select network-manager and network-manager-gnome and install. You may have to restart.  What do you see when you click the network manager icon in the upper right hand corner?  It might also be worthwhile to post the output of this command typed in a terminal "lspci".  You'll get several lines of text.  The line(s) of interest are the ones that mention "ethernet" or "network controller". lspci assumes an internal wireless adapter.  If your wireless device is usb, type "lsusb".  Network Controller is typically the wifi device. That command will tell us what kind of wifi device you have.  Mine looks like this: "Bus 002 Device 003: ID 0846:9030 NetGear, Inc."  If I go to Google and input "0846:9030"  I would find that I have a Netgear WNA1100 using an Atheros ath9k chip.  Some chips particularly Broadcom may need extra attention. Hang in there, you get around this like you get around a plate of pasta--one bite at a time.

---

### Post by el_koraco on 2011-07-04
Did you completely uninstall Network Manager? If so, you're not gonna be able to connect to the internet easily. 

[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

---

### Post by CrusaderAD on 2011-07-04
> **el_koraco said:**
> Did you completely uninstall Network Manager? If so, you're not gonna be able to connect to the internet easily. 

[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")

Makes sense. Good point.

---

### Post by in-dust-rial on 2011-07-04
hi there,

am i seeing it correctly, that you are posting this issue the second time?
and even though there is more information - i have the feeling the problem is not well explained, still.
(and the thread name is still useless)
I am sorry the command line help is not good enough for you.

if you are not willing to get down into command line, maybe you should practice yourself in patience.

ah,
and maybe you want to post the log entries?
they were in the center of the problem already several minutes ago in your last threat.
[maybe this tool is installed?]("http://www.thegeekstuff.com/2009/11/ubuntu-tips-how-to-view-system-log-files-in-gui/")

"good luck"

---

### Post by howefield on 2011-07-04
Threads merged.

---

