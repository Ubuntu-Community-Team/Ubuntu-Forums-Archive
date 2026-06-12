---
title: "Live CD customization?"
date: 2006-02-23
forum: General Help
---

### Post by xen84 on 2006-02-23
Rather than just as a preview to Ubuntu, I like to use my Ubuntu live CD at the place of my current employment. I work part time as a tutor at my university, and I'm usually just sitting around waiting for tutees to walk in wanting instruction. The PC here uses XP, and while I have no problem with the OS, I have to reinstall Firefox every time I come in, not to mention collecting all the extensions I like to use and importing my bookmark list.

What I'd like to do is set up the Ubuntu live CD so that Firefox alread has the extensions I need installed, as well as my list of bookmarks, and ideally my configuration settings as well. Now, I have very little experience with Ubuntu (or Linux in general, for that matter), so I'm not sure how I'd go about doing this.

I do have a 256MB flash drive that I carry with me on my keychain. Might that be used to store customized settings for a live boot? Or am I going to have to alter the ISO image for the disc? Is there maybe another, better solution? How might I go about doing any of these?

I thank you in advance for whatever assistance you can provide.

---

### Post by taurus on 2006-02-23
Yes, saving all personal settings on the USB thumbdrive is the best way unless you want to hack the LiveCD version!

---

### Post by xen84 on 2006-02-23
Ok, so how do I go about making the live-boot firefox do that? or will I have to reinstall the extensions and re-import the bookmarks each time I do that?

---

### Post by lamego on 2006-02-23
I would say the LiveCD customization is what best fits your needs:

There is a nice doc for how to do it:

[https://wiki.ubuntu.com/LiveCDCustomizationHowTo]("https://wiki.ubuntu.com/LiveCDCustomizationHowTo")

---

### Post by dwanders on 2006-02-23
If you are reee-ally new to Linux, I would suggest trying out Knoppix [http://www.knoppix.org/](http://www.knoppix.org/) - they have settings for just what your wanting (e.g saving system settings to a thumbDrive etc...). I have been working on a LiveCD based on Ubuntu 5.10 breezy for a couple of weeks now. It is very do-able and the instuctions at the Wiki: 

[https://wiki.ubuntu.com/LiveCDCustomizationHowTo?highlight=%28livecd%29](https://wiki.ubuntu.com/LiveCDCustomizationHowTo?highlight=%28livecd%29)

are workable if you have the right size equipment (I have been using 2 8gig drives 1 for system 1 for swap) and 512RAM and the time. After about a week I have what I want but I am having troubles modifying the desktop to my liking and fine tuning things. So close and yet so far - With Knoppix I had what I wanted in all of a day playing with it - things really got cooking after I got a book:

 [http://www.oreilly.com/catalog/knoppixhks/](http://www.oreilly.com/catalog/knoppixhks/) 

- but I dont really care for the KDE, or the look and feel of Knoppix - I prefer the Ubuntu base I thing its cleaner. 

Hope this helps ya

---

### Post by dwanders on 2006-02-28
I think I finaly got the Ubuntu rebuilds to work and now feel you go either way. The Knoppix will have more hardware detection, and some better utilities for thumb drives etc...

---

### Post by cotcot on 2006-02-28
Are you sure about the jumper settings of the HDD's (master, slave, ...) ?

---

### Post by lapsey on 2006-02-28
at the risk of sounding like a traitor I say, if your system is usb-bootable try DSL (damn small linux)

> What does DSL have?

XMMS (MP3, CD Music, and MPEG), FTP client, Dillo web browser, links web browser, FireFox, spreadsheet, Sylpheed email, spellcheck (US English), a word-processor (FLwriter), three editors (Beaver, Vim, and Nano [Pico clone]), graphics editing and viewing (Xpaint, and xzgv), Xpdf (PDF Viewer), emelFM (file manager), Naim (AIM, ICQ, IRC), VNCviwer, Rdesktop, SSH/SCP server and client, DHCP client, PPP, PPPoE (ADSL), a web server, calculator, generic and GhostScript printer support, NFS, Fluxbox window manager, games, system monitoring apps, a host of command line tools, USB support, and pcmcia support, some wireless support.

all this running at 50Mb on a USB flash drive.

it's also quite lightweight thanks to fluxbox so it will run happily on older systems (if they are usb bootable that is )

[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by towsonu2003 on 2006-02-28
[QUOTE=xen84]I have no problem with the OS, I have to reinstall Firefox every time I come in, not to mention collecting all the extensions I like to use and importing my bookmark list.
(...)
I do have a 256MB flash drive that I carry with me on my keychain. [/QUOTE]
I think you will find portable firefox much more interesting than to deal with costumizing a live cd: 
portableapps.com (now down)
[http://sourceforge.net/projects/portablefirefox](http://sourceforge.net/projects/portablefirefox)

Download it, unzip it (to your flash drive), double click portablefirefox.exe. Setup your extensions and stuff. Done. You rflash drive has your firefox that you don't need to install ever.

As a side note, basically, all you need to carry is "profile" folder (smaller). You can: setup firefox as above, copy profile to flash when done, go to work, download portable firefox again, replace its "profile" folder with the one you have in your flash drive. I always carry my profile in my email account, just in case... 

PS. Never keep private data in flash drive (such as saved passwords or forms etc).

I *wish* we had this for linux... No need for a wiki to update **[currently vulnerable]("https://launchpad.net/products/firefox/+bug/32083")** firefox...

---

