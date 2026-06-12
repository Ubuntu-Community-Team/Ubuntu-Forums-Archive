---
title: "Transfer Files"
date: 2011-10-12
forum: General Help
---

### Post by mbhammerbro on 2011-10-12
Hey guys,

I am currently running Ubuntu 11.04 on one of my spare pc's and running gnump3d off of it.  I was wondering if there is any way that I can transfer files from this PC (windows 7) using RDP or possibly some other way to my Ubuntu server.  This would be very useful because I have many PC's I would like to transfer files from, and no flash drive or anything to transfer with.  Thanks.

---

### Post by mbhammerbro on 2011-10-12
bump..

---

### Post by Mark Phelps on 2011-10-12
Don't bump every few hours -- that's considered RUDE.  The rule around here is no more than once very 24 hours.  Someone will get back to you -- in time.

---

### Post by mbhammerbro on 2011-10-12
Sorry didn't know.  Just saw that the post got pushed back so far so quickly.

---

### Post by cryptotheslow on 2011-10-12
So if I understand your question correctly, you wish to transfer files *from* a Win7 machine (or several of) *to* an Ubuntu machine?

Probably the most Win7 click-happy way of achieving it would be to run a Samba service to provide SMB (Windows standard) file shares on the Ubuntu machine.

This is easily achieved.

Is you 11.04 installation an Ubuntu Server install (i.e. command line only), or is it an Ubuntu Desktop install (i.e. with desktop / graphical environment) that you just happen to be using as a "server"? Reason I ask is so we know whether to provide command-line instructions or point-and-click instructions :D

---

### Post by mbhammerbro on 2011-10-12
> **cryptotheslow said:**
> So if I understand your question correctly, you wish to transfer files *from* a Win7 machine (or several of) *to* an Ubuntu machine?

Probably the most Win7 click-happy way of achieving it would be to run a Samba service to provide SMB (Windows standard) file shares on the Ubuntu machine.

This is easily achieved.

Is you 11.04 installation an Ubuntu Server install (i.e. command line only), or is it an Ubuntu Desktop install (i.e. with desktop / graphical environment) that you just happen to be using as a "server"? Reason I ask is so we know whether to provide command-line instructions or point-and-click instructions :D

Yes, your correct.  And I am running a desktop interface (think i may switch this soon since there is really no point since I'm only using it to run the server).

---

### Post by cryptotheslow on 2011-10-12
OK - there is a fairly simply walkthrough on the Ubuntu help pages here:
[https://help.ubuntu.com/11.04/ubuntu-classic/internet/C/networking-shares.html](https://help.ubuntu.com/11.04/ubuntu-classic/internet/C/networking-shares.html)

Scroll down to either the "Sharing folders via Nautilus" section or the "Sharing folders via the Shared Folders application" section just above.

Once you have walked through that to share whatever directories/folders you wish. Then you simply need to connect to the shared folder from your Win7 machine. I don't have a copy of Win7 - only XP so can't really offer specific click level instructions for that bit.

Typically you just open up the Windows explorer and in the location bar enter:  \\ubuntuservername\sharename

..... obviously using the name of your server and the name you gave to the share when setting it up.

To make the share access persistent across reboots of the Win machine look for the "Map Network Drive" option (it's in the explorer Tools menu on XP). That allows you to map a drive letter to the shared folder on the server.

---

### Post by HermanAB on 2011-10-12
Filezilla is probably the easiest way. Put the server on one machine and the client on the other.

---

### Post by Slim Odds on 2011-10-12
> **HermanAB said:**
> Filezilla is probably the easiest way. Put the server on one machine and the client on the other.

If you install the openssh server on the linux side, you can filezilla from Windows to the linux machine using sftp.

---

### Post by cryptotheslow on 2011-10-12
So many options of course :)

I just went with what I thought would be the most intuitive for someone who seems to be mostly Windows based. (Leaving relative throughput considerations aside).

---

### Post by Morbius1 on 2011-10-12
How about one more option if you have a desktop on that server. 
> **Morbius1 said:**
> If you just need to transfer files from A to B then you might consider using Dukto: [http://code.google.com/p/dukto/downloads/list](http://code.google.com/p/dukto/downloads/list)

Place it on the Windows and the Ubuntu machine and transfer away. From their Wiki:
> Dukto is a standalone software, it doesn't need installation, it  doesn't  creates any configuration file or registry key on your PC, it  doesn't  require any software (apart from the operating system) to run,  it  doesn't require configuration or account registration. And it runs  on  Windows, Mac OS X and Linux. [QUOTE]Dukto usage is very simple, just start it on the two PC connected  over  the LAN (or directly connected). On the buddy list will be showed  the  other peer. Now simply drag and drop your files and folders over  the  dukto window and they'll be transferred to the other end. That's  all.                      [COLOR=Blue]Just to be clear, this isn't a replacement for Samba or any other file  sharing protocol as there is  no authentication mechanism involved or  permanent mounts. It's simply a very easy way to get files from A to B  without any setup.[/COLOR][/QUOTE]

---

### Post by mbhammerbro on 2011-10-12
Thanks guys.  I've got a lot of options to go through once I get home from work.

---

