---
title: "ClamTK Virus Scanner"
date: 2011-09-17
forum: General Help
---

### Post by crutch145 on 2011-09-17
When scanning my Documents folder, after the scan is complete it says it only scanned 4 files.  It is not scanning the child folders within the top-level folder.  Is there a way I can get it to scan my entire hard drive?  Do I need to run it as root/sudo via the terminal to do this?  

Thanks,

Justin

---

### Post by haqking on 2011-09-17
> **crutch145 said:**
> When scanning my Documents folder, after the scan is complete it says it only scanned 4 files.  It is not scanning the child folders within the top-level folder.  Is there a way I can get it to scan my entire hard drive?  Do I need to run it as root/sudo via the terminal to do this?  

Thanks,

Justin

Hi and welcome to the forums

Just select directory and then specify / if you want to scan everything or whatever you want to specify.

Though malware in general can infect a Linux machine it is rare due to a number of reasons, not to say it cant happen at all though.

Linux does not suffer from Viruses like other OS, there are no known viruses in the wild, the main reason using AV on linux is to scan incase you share files with windows users.

It can still suffer from trojans, rootkits etc, but that comes down to vigilence and making sure you stick to the security model and not disabling passwords or enabling root etc.

Common sense, dont tell your system you want it to do something unless you are sure etc. Linux assumes you know what you are doing ;-)

In browsers you can still suffer from XSS or CSFR, other script related issues so use things like NoScript plugin for firefox, Ad-block etc.

See here for Anti-Virus information:

[http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[http://www.neowin.net/news/a-history-of-viruses-on-linux](http://www.neowin.net/news/a-history-of-viruses-on-linux)

And make sure your read the link in my signature about [Your Ubuntu Password]("https://help.ubuntu.com/community/RootSudo")

---

### Post by crutch145 on 2011-09-17
Thanks.  The Virus Scanner I am using is GUI, and when I open it, I select Directory.  Then the only place I can specify the / is if I click the little pencil icon (if I hover cursor over it, it says "type file name").  If I put the / in there and click OK, it only scans 3 files and then says it is complete.

---

### Post by Triblaze on 2011-09-17
In the GUI, click Advanced>Preference>Scanning Preferences, then check "scan all files and directories within a directory".

---

### Post by varunendra on 2011-09-18
Or a one-step method : **Scan > Recursive** scan then choose the directory or drive you want to scan.

What *Triblaze* suggested will make this to happen everytime you use the buttons in the GUI, so is good if you wish so to happen. But the 'Scan' menu gives you both choices. Take your pick :)

---

