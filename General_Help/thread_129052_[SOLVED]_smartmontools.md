---
title: "[SOLVED] smartmontools"
date: 2006-02-12
forum: General Help
---

### Post by rfruth on 2006-02-12
Anyone using the smartmontools on your S.M.A.R.T. drive and if so good/bad or just so-so results [http://http://smartmontools.sourceforge.net/]("http://http://smartmontools.sourceforge.net/")

[-(

---

### Post by hw-tph on 2006-02-13
Yes, I am using it on all my Linux boxes. I have had two drives replaced when smartd indicated they were about to fail (I printed the reports and went to the store with them and the disks). It has worked very well for me, and in a corporate environment I wouldn't want to live without it.

For those who don't use it yet, read Bruce Allen's [primer on SMART](http://www.linuxjournal.com/article/6983) in LinuxJournal.


Håkan

---

### Post by nanotube on 2006-02-13
wow, hw-tph, thanks for the cool link. :)
question for you - what are your settings for smartd? what would you recommend?

---

### Post by hw-tph on 2006-02-13
Check your /etc/smartd.conf. It is very well documented.

On my laptop I one of the simplest tests straight out of the examples in the configuration file. On my servers and desktops (that see much longer uptimes that the laptop) I have different settings depending on what they do.

This is straight out of smartd.conf too, only with email notification turned on if the simple health test (-H) indicates failure:
```
/dev/hda --smart=on --offlineauto=on --saveauto=on /dev/hda -H -m hakan@mydomain.com
```

It all depends on what you want. Read smartd(8), smartd.conf(5) and of course the config file itself. You can monitor temperatures and whatnot if your drives support it.


Håkan

---

### Post by edafe on 2007-01-08
How to configure smartmontools with email notification:

[http://www.edafe.org/ubuntu/index.html#smartmontools](http://www.edafe.org/ubuntu/index.html#smartmontools)

Regards,
Edafe

---

### Post by aidanr on 2007-01-08
i have it installed, use it every now and again to check the smart status on my drives, works fine no real complaints, a gui frontend would be nice though

---

### Post by dcstar on 2007-01-09
> **aidanr said:**
> i have it installed, use it every now and again to check the smart status on my drives, works fine no real complaints, a gui frontend would be nice though

I have smartmontools and hddtemp working on my system, the HD temp appears in my Gkrellm display.

---

### Post by Magnes on 2007-01-09
I use it from time to time. It's very good tool.

---

