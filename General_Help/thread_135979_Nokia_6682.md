---
title: "Nokia 6682"
date: 2006-02-25
forum: General Help
---

### Post by msak007 on 2006-02-25
Has anybody been able to successfully plug in and detect this phone? I don't have a flash card reader and in windoze I used to just plug the phone in using the USB data cable and used the Nokia suite to transfer files to the flash card - that's obviously not an option here, since Nokia doesn't make any Linux compatible phone software (not that I'm aware of). The phone has an indicator on it showing that it's connected via the data cable, but it's not showing up as removable storage in my computer. I've already searched the forums and googled it, and found absolutely nothing. I'm sure someone has done it, but I can't find any info. I would hate to add one more reason to continue dual-booting windoze, so if anybody knows how please let me know.

---

### Post by der_joachim on 2006-02-25
AFAIK the USB data cable is not supported in Linux. Apparently, there's more to it than just a USB port and a FAT file system. :(

There used to be a guide for setting up a Bluetooth connection for Nokia phones (6230) in Debian-like systems, but the link is dead, so I can't help you there either. 

Furthermore, you might try to install [gnokii]("http://gnokii.org/"). It is in the repositories.

---

### Post by Jucato on 2006-02-25
have you tried installing your nokia software in Wine?

---

### Post by msak007 on 2006-02-26
Thanks for the suggestions. To der_joachim, I'd prefer to stay with the USB cable. I don't have a Bluetooth USB dongle, and the cable would be faster anyway. I'm mostly transferring mp3 ringers, pics, and mp3s so the speed is important. There are plenty of guides on getting Bluetooth to work. Isn't it funny how Bluetooth is supported, but a simple (or so I assume) USB cable isn't?

To Fenyx, I haven't tried the phone tools through Wine...I'm trying to stay with Linux native / open source apps as much as possible, but it may come down to that. Besides, the only part of the tools I used was transferring data to / from the phone & memory card so I see no need to install the whole bloated package. However, I broadened my searches and after a while found a few links on using OpenOBEX / OBEXFTP with USB support. One link in particular has helped me quite a bit. Here it is in case you're interested:

[USB OBEX How-to]("http://members.dodo.com.au/~joaniemrc/nokia/Nokia-6670-USB.html")

I've gotten most of the how-to to work. The main difference is that the versions of OpenOBEX / OBEXFTP are different. It was updated in Januray so I'm not sure how much has changed since then, but OpenOBEX 1.1 is out and it does support USB so the CVS version is no longer needed.  However, the current version of OBEXFTP  (0.19) still doesn't support USB and I can't patch the files per the how-to - I get lots of errors applying the patch and during the make process. That's the only part I haven't gotten to work. I've installed OBEXTool successfully and launched it, so if I can get OBEXFTP to recognize the USB interface, I'll be all set. I'll let you all know how it works out.

---

### Post by der_joachim on 2006-02-26
I did some additional research on the gnokii webpage (see above for the proper hyperlink). Somewhere in the download section, there is a subdirectory with the most recent Ubuntu binaries. Install these, and you will have the most recent version.

---

### Post by msak007 on 2006-02-26
gnokii seems to be pretty similar to kmobiletools (well, the gnocky front-end anyway), which I already have installed and running. I couldn't get my phonebook or SMS messages to be read though, so I'll try gnokii. What I'm really looking for though is the ability to transfer files to / from my phone & memory card. It doesn't look like either app supports this function.

---

