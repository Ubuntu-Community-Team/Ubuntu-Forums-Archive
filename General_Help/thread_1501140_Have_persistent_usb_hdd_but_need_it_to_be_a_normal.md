---
title: "Have persistent usb hdd but need it to be a normal installation"
date: 2010-06-03
forum: General Help
---

### Post by john &amp; on 2010-06-03
So I've searched a lot on this, but all I could find was how to make the usb hdd install as a 'try ubuntu' type of installation, so on each boot, it asks me if I want to install or try.

I had a pc with 9.04 so I downloaded 10.04 iso and used the Startup Disk Creator and I tried to use a ex2 partition on my usb hdd, but SDC didn't like it and it wanted to format the usb hdd so I let it.  Then it was happy to continue.

The reason I wanted to have it use a partiton of the entire usb hdd was so that I could do an install to the other area of the usb hdd once I connected it via ide to the box after pulling the 9.04 ide hdd, because I had a feeling this was going to happen.

I now have the entire ide hdd running as the 'trial' version, it works, but it takes longer to boot up, maybe bc it's configured as the trial version?

I was hoping that there was an app to do a standard full install to a usb hdd like one would in a tech shop when setting up drives to then pop in to PC's, I was surprised to not find it, or did I miss it?

So how do I mod this into a normal full os install?

---

edit: so i decided to use parted majic to shrink the fat32 partition, now all I have is: "Boot error"  My plan was to shrink the fat32 partition and then boot back into 10.04 and use install app to install to the remaining space on ide hdd, not gonna happen now.

---

edit2: this is now totally different.  I booted using plop floppy to boot a usb stick I have netbook remix on and I'm installing to the hdd.  So I'll now need to find out how to upgrade from this ver, i think it's 9.04 also, to 10.04

---

edit 3:  so there was no update to 10.04 option, so I am upgrading to 9.10, good news is that it's downloading at 1.5mbs! wow, now 1.7 sweet, that's the fastest data that ever flowed thru here

---

### Post by wilee-nilee on 2010-06-04
If what your trying to do is a full install to the usb HD you boot from a live cd hit, go to gparted and partition the HD how you want it. Hit install choose custom install in the partitioning gui click on the main partition for install and then the partition type you formatted it to, don't click on the format button and click on the dropdown and pick /=root then click okay then click on that partition again hit forward then in the last gui that has a advanced button, click on it and make sure grub is installed to the master boot record and not a partition if this is a usb HD it will probably be sdb.

Just for future reference the long description of your previous activities is not needed; just get to what you need to do, it was very hard to read and slightly confusing. ;) 

If you ramble on with impertinent information the chances of somebody responding to a first post of a person who seems to be new at this drops with each consecutive word.

---

### Post by john &amp; on 2010-06-04
I guess what i was trying to do was impossible.  I didn't have a cdr handy so i thought i could download 10.04 iso from within 9.04 to get 10.04 on the usb hd, but it only installed the tial version rather than full, def way too much to ask for.

---

### Post by wilee-nilee on 2010-06-04
You can load the ISO into a thumb with the ubuntu thumb loader or unetbootin and use it to install with probably.

What your trying to do can probably be done from a command line but good luck getting help to do so, as a loop for installing in the main HD is fairly easy but to a usb HD and making sure grub is installed correctly is not for the faint at heart or a beginner in Linux. Buy a cd and do it correctly, or use a thumb drive.

---

### Post by john &amp; on 2010-06-09
so I ended up doing 2 upgrades from 9.04, it was very inefficient.  The best way so far is undocumented, which is really required if the os is ever going to be taken seriously.

---

### Post by wilee-nilee on 2010-06-09
> **john & said:**
> so I ended up doing 2 upgrades from 9.04, it was very inefficient.  The best way so far is undocumented, which is really required if the os is ever going to be taken seriously.

That is a ridiculous sentiment, **you had no cd**. Blaming the OS for not just doing what makes sense is deflecting responsibility. You are a obviously not a experienced user.

---

### Post by dcstar on 2010-06-09
> **john & said:**
> so I ended up doing 2 upgrades from 9.04, it was very inefficient.  The best way so far is undocumented, which is really required if the os is ever going to be taken seriously.

Bah.

The Live USB is exactly what **it** says it is, not what **you** believe it should be.

If you wanted to upgrade your previous version you could have simply done a web search for things like this instead of complaining:

[http://www.webupd8.org/2010/05/upgrade-to-ubuntu-1004-lucid-lynx.html](http://www.webupd8.org/2010/05/upgrade-to-ubuntu-1004-lucid-lynx.html)

---

