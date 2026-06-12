---
title: "[HELP] AOL - Broadband - Router"
date: 2006-04-21
forum: General Help
---

### Post by RedFoxEvan on 2006-04-21
Hi, Im on AOL Platinum - Broadband - , with a router/wireless connection. Yes Im a bit of a Noob, but I can take what you ask! I have searched but what i found isnt broadband, it is dialup, in which doesnt help. I have tried the Live CD'S And They are BRILLIANT! And If only i could connect to the internet, would top it off! :D 

If anyone needs information, i will be happy to say. 
Regards
Evan

---

### Post by RedFoxEvan on 2006-04-21
Anyone please?

---

### Post by yyagol on 2006-04-21
what is the problem ?
you got a router so ther is no need for a dialup

---

### Post by RedFoxEvan on 2006-04-21
I cant connect to the internet?!

---

### Post by RedFoxEvan on 2006-04-22
Yes i have a router, yet my belking device isnt there or cant find the connect, in which im Very Stuck.. same applies with ubuntu,

Thankyou very much for help

Evan

---

### Post by Jason_25 on 2006-04-22
Please post your network adapter model.

---

### Post by RedFoxEvan on 2006-04-22
You mean my router or usb connecter device?
EDIT: My router:[http://speedtouch.com/prod780.htm](http://speedtouch.com/prod780.htm)
My Wireless connector:  [http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1484636789.1145652017@@@@&BV_EngineID=ccfcaddhiilhlhkcflgceggdhhmdgmi.0&page=Product&fm=null&sm=null&tm=null&sku=138020&category_oid=](http://www.pcworld.co.uk/martprd/store/pcw_page.jsp?BV_SessionID=@@@@1484636789.1145652017@@@@&BV_EngineID=ccfcaddhiilhlhkcflgceggdhhmdgmi.0&page=Product&fm=null&sm=null&tm=null&sku=138020&category_oid=)

---

### Post by RedFoxEvan on 2006-04-22
Im Also on a laptop, forgot to mention, I used the install cd, got to partitioning and i REALLY didn't understand, should i put in /root or /home and the fat is my backup or something... :@

---

### Post by Jason_25 on 2006-04-22
Please don't use separate threads for the same problem.  Does your wireless device show up in networking?  If not, you will probably need to use ndiswrapper.  From what I have read, your device does not have a native driver.

---

### Post by RedFoxEvan on 2006-04-22
No it doesnt show up, and (off topic) I tried installing ubuntu, and it says someonething, but doesnt say resize, in which i have read and is what i should use, as i would like to keep windows XP too...

Many thanks again

---

### Post by Jason_25 on 2006-04-22
You should start a new thread if you have a partitioning problem.  Here is the wiki page for setting up ndiswrapper:

[https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

If your PC doesn't have internet access by some other means, then you will need to copy the i386 deb from this page to a usb drive and then insert it in your ubuntu pc:

[http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils](http://packages.ubuntu.com/breezy/misc/ndiswrapper-utils)

To install the deb
```

sudo dpkg -i nameofdeb.deb

```

---

### Post by RedFoxEvan on 2006-04-22
I was doing it on alive cd, but if i can't partition/install i can't do that :@ 
and spamming the forums isnt very good, and so i thought to ask here ;/

---

### Post by Jason_25 on 2006-04-22
Really the double posting isn't bad because it's spam.  It's bad because it's confusing.  Definitely do post a separate question for partitioning help if you need it.  The ndiswrapper page looks more complicated than it really is.  Post back if you decide to tackle it.

---

### Post by RedFoxEvan on 2006-04-23
Well, I took on partitioning, and used free space, yet it now boots up using Ubuntu, and I still can't connect to the internet. And that ndiswrapper looks *really* confusing, is there any way to scale it down?
Btw- Im on a different coomputer here, in which i can download things etc..

Thanks in advance
-E

---

### Post by Jason_25 on 2006-04-23
There is a link on that page to ndiswrapper-utils.  Grab the deb for your ubuntu version.  You need to copy that and the windows drivers for your wireless card onto a usb flash drive or cd and then copy them to the ubuntu pc that way.Info about windows drivers for your card is [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/list").  To install the deb, from the terminal
```

sudo dpkg -i nameofdeb.deb

```
Now cd to the directory with your drivers, and type 
```

sudo ndiswrapper -i nameofinf.inf

```
To verify all that worked
```

ndiswrapper -l

```
The final step is to load the kernel module which should create the actual interface.
```

sudo modprobe ndiswrapper

```
and this is to check for problems loading the module
```

dmesg | tail

```

---

### Post by RedFoxEvan on 2006-04-23
hanks for the reply;
I dont understand the:
> sudo dpkg -i nameofdeb.deb
and
> The final step is to load the kernel module which should create the actual interface.

Thankyou

---

### Post by RedFoxEvan on 2006-04-23
Ok Ive managed to undertsnad and DO The sudo dpkg -i name of deb etc
then i dont understand the next instruction>  sudo ndiswrapper -i nameofinf.inf Shall i insert my belkin disk.. ? sorry for being a noob, im doing my best to learn!

Thanks in advance

EDIT: I don't have a card I have a USB Dongle, Obvisouly not on the wiki...

**EDIT AGAIN**: Found Belkin F5D7051 (USB 2.0 Adaptor 802.11g 125Mbps)

---

### Post by RedFoxEvan on 2006-04-23
*Removed* I guess i will wait a bit longer..but i really dont know what to do, and yes its a much of an urgencie!
Oh and I tried using ethernet through my router, and didn't work :@

Evan

---

### Post by RedFoxEvan on 2006-04-23
Bump?!

---

### Post by Jason_25 on 2006-04-23
What's the problem?  Your card _IS_ listed on the wiki link I posted.

---

### Post by RedFoxEvan on 2006-04-23
Yes, and I said above that i found it :@
I got annoyed with it, deleted a partion (Not sure what) and re-installed windows, I dont think i have deleted ubuntu, yet i have no idea/how to access it as i dont have any dual boot options on startup. Shall i make a new thread? Because once this is solved, i can carry on doing what you said. Oh and the drivers for my card arent in the CD, I tried hidden files etc, nothing there, which gets me stuck on Instruction [2].

Thanks for the reply,
Evan

---

### Post by Jason_25 on 2006-04-23
You'll have to run 
```

grub-install /dev/hda

```
from a live cd to reinstall grub.  Either google for drivers on your card or check the manufacturer's website.

---

### Post by RedFoxEvan on 2006-04-23
Ok thanks i'll give it ago, and if that works can you help me with wireless again please?

thanks in advance

---

### Post by RedFoxEvan on 2006-04-25
Ok ive sorted out dual booting and partitioning, now how can I get my wireless working please, Also Im a noob, so could you explain in *human* form :x? Thanks alot for your help, very grateful!

---

### Post by Jason_25 on 2006-04-27
I have a feeling the drivers should have been on your install cd.  Sometimes to get the actual drivers and infs you need to use a windows pc to run the installer and then copy the folder the installer generates from the temp folder.  There's probably a fancy way of doing that in linux too but I don't know how.  Anyway, if that doesn't work, check belkin's website or google for drivers.

---

### Post by RedFoxEvan on 2006-04-27
oK Ill give it a go and report back soon

-E

---

### Post by RedFoxEvan on 2006-04-30
I have found no drivers on the cd hidden,or not I can't find them.. Its weird because i remember finding them a few months or so ago.

-E

---

### Post by RedFoxEvan on 2006-05-01
..bump

---

### Post by Jason_25 on 2006-05-01
[http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1](http://www.belkin.com/support/download/downloaddetails.asp?download=1871&lang=1)

---

### Post by RedFoxEvan on 2006-05-01
yeah, used that, couldnt find them either :S

---

### Post by Jason_25 on 2006-05-01
Read post #25.  You will need to scan your windows temp folder while the windows installer is running if the files don't get extracted to an obvious place.  There is probably a more clean way of doing it I just don't know how.

---

