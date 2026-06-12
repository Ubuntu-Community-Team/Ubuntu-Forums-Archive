---
title: "Install Lubuntu without internet"
date: 2012-01-28
forum: General Help
---

### Post by ciaopaulo on 2012-01-28
Hi,

I'm trying to install Lubuntu on an old Toshiba Satellite with 128Mb RAM.

From the LiveCD I can click install, but the install will not progress beyond the screen which checks for hard disk space, power and internet.

This machine doesn't have RJ45 or Wireless internet.

How can I complete this install?

---

### Post by Rex Bouwense on 2012-01-28
128 Mbs of Ram is a bit tight but it should install.  You should not need the Internet simply to install.  Two questions.  
First, did you check the MD5Sum after you downloaded the ISO?  
Second, did you burn the ISO at the lowest possible speed to get a good burn?  Boot from the CD and check that all of your hardware is working and the programs work on your machine.

---

### Post by kurt18947 on 2012-01-28
I too think 128 Mb. is pushing it.  Any chance of adding another 256 Mb.(presuming you have an empty slot)?  I don't have Lubuntu running right now but when I did on a PIII Thinkpad, I recall it used just over 100 Mb. with just a browser open. Old RAM can be difficult to find.  I bought  my last 256 Mb. DIMM off Ebay, <$10 delivered.  It had a 7 day return after delivery.  I immediately installed it and ran memtest86 for a few hours.  It tested fine,  geriatric Thinkpad is happy.

---

### Post by Rodney9 on 2012-01-28
[https://help.ubuntu.com/community/Lubuntu#System_requirements](https://help.ubuntu.com/community/Lubuntu#System_requirements)

System requirements
A Pentium II or Celeron system with 128MB of RAM is probably a bottom-line configuration that may yield slow yet usable system with Lubuntu. It should be possible to install and run Lubuntu with less memory, but the result will likely not be suitable for practical use.

Install guide - 

[https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by kalehrl on 2012-01-29
Lubuntu just won't install using GUI even with 256MB of RAM.
You will have to use mini.iso but since you don't have internet access that won't work either.
The only way I see is using alternate install cd and choosing command line installation.

---

### Post by Rodney9 on 2012-01-29
> **kalehrl said:**
> Lubuntu just won't install using GUI even with 256MB of RAM.
You will have to use mini.iso but since you don't have internet access that won't work either.
The only way I see is using alternate install cd and choosing command line installation.

I beg to differ - 

[https://lists.launchpad.net/lubuntu-desktop/msg04386.html](https://lists.launchpad.net/lubuntu-desktop/msg04386.html)

[http://www.youtube.com/watch?v=48hxkd8x4NI](http://www.youtube.com/watch?v=48hxkd8x4NI)

Rodney

---

### Post by kalehrl on 2012-01-29
Neither 10.04 nor 11.10 would install using live CD in normal GUI way.
The installer would crash somewhere in the middle of disk partitioning.
However, using mini.iso and command line installation, both versions installed fine.
The only conclusion I could draw is that the RAM was not enough for GUI installation.
Once installed, Lubuntu works fine with 256MB of RAM.

---

### Post by ciaopaulo on 2012-01-29
> **kalehrl said:**
> The installer would crash somewhere in the middle of disk partitioning.

*Would* or *does*?

If the live install requires a certain amount of RAM then this should be an express requirement, and not manifest itself as a strange bug, which seems to be the assumption here.

---

### Post by ciaopaulo on 2012-01-29
> **Rodney9 said:**
> I beg to differ - 

[https://lists.launchpad.net/lubuntu-desktop/msg04386.html](https://lists.launchpad.net/lubuntu-desktop/msg04386.html)

[http://www.youtube.com/watch?v=48hxkd8x4NI](http://www.youtube.com/watch?v=48hxkd8x4NI)

Rodney

Neither of those posts say they used the GUI to install.

---

### Post by JC Cheloven on 2012-01-29
Hi, Lubuntu CD should install in your system if you choose directly "install Lubuntu" instead of "try Lubuntu". Please make sure you set some (256 Mb?) swap space during partitioning.

BUT perhaps it doesn't install, as it depends on a number of factors (memory being shared/used by graphics and other things). No need to argue then: if it doesn't, it doesn't. Let's see what could be done in that case:

As mentioned, swap is essential in your case. I would suggest to use a [gparted live disk]("http://gparted.sourceforge.net/livecd.php"), for the only purpose of partitioning in advance, perhaps one ext4 partition and a swap partition. Afterwards, the Lubuntu installer will use that swap space as ram, and willl (hopefully) complete the install. It will take a bit longer though.

Hope this helps.

---

### Post by ciaopaulo on 2012-01-29
> **JC Cheloven said:**
> Hi, Lubuntu CD should install in your system if you choose directly "install Lubuntu" instead of "try Lubuntu". Please make sure you set some (256 Mb?) swap space during partitioning.

That avenue didn't work either.

[See this thread.]("http://ubuntuforums.org/showthread.php?t=1915690")

---

### Post by JC Cheloven on 2012-01-29
Ok, it didn't, no argument :)
Let's see then if the swap-in-advance way works. I'm confident it will.

EDIT: I just had a read on the thread you mentioned, and didn't see a mention to any attempt of installing from the "Install Lubuntu" option. Just to be sure: I mean the option at the very startup of the live cd, after asking for the language and before the system is even loaded.

EDIT2: If that fails, we're in the swap-in-advance possibility. If that also fails, perhaps it isn't a ram issue, and we can try playing with boot options like noapic, nolapic, and i915modeset. If eventually that also happen to fail, I still have a last resort suggestion : puppy. Let's see what you do report for each step, ok?

---

### Post by mike555 on 2012-01-29
if you have access to another computer and a USB drive you could format the USB drive as swap and try using it to help with install.

---

### Post by kalehrl on 2012-01-30
> **ciaopaulo said:**
> *Would* or *does*?

If the live install requires a certain amount of RAM then this should be an express requirement, and not manifest itself as a strange bug, which seems to be the assumption here.
It crashed two times with two different Lubuntu versions.
My conclusion was that there wasn't enough RAM.

---

