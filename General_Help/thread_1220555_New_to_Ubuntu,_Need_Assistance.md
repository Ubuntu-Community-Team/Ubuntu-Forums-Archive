---
title: "New to Ubuntu, Need Assistance"
date: 2009-07-22
forum: General Help
---

### Post by soori007 on 2009-07-22
Hi,

I'm new to ubuntu. Wish to switch from Windows XP. Before going in, I need all the pre requirements ready.

[B]My Confuguration:
[/B]Dell Inspiron 200 Laptop
Intel Celeron 1.13 Ghz
384 MB RAM, 20 GB HDD
D Link DFE-690TXD CardBus PC Card
Intel 82801CA/CAM AC'97 Audio Controller

Choose Ubuntu 9.04.

Need the following on my System: (I have chosen some of them)

[LIST=1]
[*]Office Software - Possibly Open Office
[*]Drivers: I need Drivers for the above Hardware - Motherboard, Dlink Card & Sound Card
[*]Suitable PDF Writer & Reader
[*]Java
[*]Media Player - Something like Winamp
[*]Compression Tool alternative to WinRAR
[*]Antivirus Software
[*]Instant Messengers I use: Yahoo, GTalk.
[/LIST]

Let me know if these work on Ubuntu or you have any alternative. It would be good if someone can provide me the links for those _system drivers especially_. 

Thanks for your guidance.

Regards,
Captain James (Soori)

---

### Post by Vaphell on 2009-07-22
1. open office is in fresh install of Ubuntu already
2. most hardware is covered by default though, you can try Ubuntu without installing - just run it from CD in LiveCD mode.
3. there are many, one can argue if on par with adobe bloatware
4. available
5. lots of them
6. no problem here - default system compression tool can use many formats, you can add more by installing 'plugins'
7. not really needed, but there are some, ie ClamAV
8. Pidgin present in default installation can communicate with over 10 different IM networks

i suggest dual booting, in case you have some really annoying problems you can always fall back to XP to do the tasks in question.

---

### Post by JOHNNYG713 on 2009-07-22
Ubuntu has every thing you need! Items 1,2,3,4,5,6,,8 Got em! 7 not really needed but GOT em! the hardest part about ubuntu is finding the equivalent program to windows, there are usually about 2 or 3 or more to choose from so it is just a matter of finding the program that best suits your needs, ubuntu has come leaps and bounds from just a few years ago there is plenty of FREE opensource software  out there and then some ! so come on in the ubuntu is great! :D

---

### Post by darolu on 2009-07-22
1. OpenOffice.org; it comes with the system, ready to use right after you install Ubuntu.
2. You shouldn't be worried about drivers; seems like your system will work fine, the drivers are already there and will be installed when you install your system; it should be ready to use after you install.
3. Ubuntu already has what you need to work with PDF files; you can create them with OpenOffice.org and save as PDF, the easiest way IMO. There is a linux version of Adobe Reader in adobe.com but you won't *need* it, I wouldn't recommend installing it with 384MB of RAM only.
4. Java can be installed with the add/remove tool (under applications menu).
5. There are programs similar to Winamp, the most populars are XMMS and Audacious; I recommend audacious as xmms is no longer developed; you install it with add/remove too, is very simple.
6. Ubuntu already has all you need to work with rar, zip, tar, etc... to decompress you only need to right click the files.
7. Virus??? what exactly virus are?? you won't find virus under Linux (striclty talking, there are no such things are virus; other malware does exist but you won't have a single problem as regular user). You don't really need an antivirus antispyware anti-etcetera but there are some options out there.
8. Pidgin the default Instant Messenger covers most IM protocols (msn, yahoo, google talk, icq, aol, etc...), there are many other programs too, I like pidgin, emesene and kopete.

You can install all this apps with the Add/remove option.

I recommend installing the "ubuntu-restricted-extras" package, it has popular stuff like mp3, wma, mp4, etc... support, flash plugin, fonts, etc.

---

### Post by soori007 on 2009-07-23
Hi All,

Thanks for the response. Really nice to know more about this.
Can I use the same drive for installing Ubuntu as with XP or I may need a new partition?
I have downloaded the Desktop package and will try to run it Live before using it.

-Captain James :)

---

### Post by Vaphell on 2009-07-23
you can install it on windows partition (using wubi) but separate partition is recommended. When you use wubi, ubuntu installs itself like any other application in windows (you can find it in add/remove) and you can choose it at the boot menu but the drawback is that it's slower than separate installation because it 'lives' in a single file on window partition, so there is some waste introduced by that additional layer.

---

### Post by yeats on 2009-07-23
> 2.  Drivers: I need Drivers for the above Hardware - Motherboard, Dlink Card & Sound Card

One word of caution - there are several known issues with Intel integrated graphics cards in Jaunty, and I would suspect that your system would be affected.  Read here:

[http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards](http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards)

But don't let that scare you off! :-)

---

### Post by soori007 on 2009-07-23
Hi,

Thanks for that one. Possibly I can create another partition on windows with partition magic and use it for ubuntu. 
Let me try it once!

---

### Post by soori007 on 2009-07-23
can anyone guide me through wubi installation?

---

### Post by overdrank on 2009-07-23
> **soori007 said:**
> can anyone guide me through wubi installation?

[Wubi]("https://help.ubuntu.com/community/Wubi")

---

### Post by soori007 on 2009-07-23
Some of the websites (bank sites) work good only on IE. Does IE work on ubuntu?

---

