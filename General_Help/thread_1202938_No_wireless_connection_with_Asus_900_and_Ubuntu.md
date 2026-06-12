---
title: "No wireless connection with Asus 900 and Ubuntu"
date: 2009-07-02
forum: General Help
---

### Post by jimn63 on 2009-07-02
Hi everybody! I've just bought an Asus eee 900 netbook on ebay. The original owner had deleted Window XP OS, and installed Ubuntu 8.04. I have a wireless router , i can not connect to the network to surf the internet. Everytime i want to connect to internet i have to hook up a cable from router to the netbook and it works. I followed many instructions to set up a wireless connecting, but failed. Should i buy a wireless adaptor for the Asus or buy a Window XP support CD to reinstall Window XP back...? Thanks in advance for any advice to help me

---

### Post by synapsys on 2009-07-02
Open up a terminal Applications >> Accessories >> Terminal

And type this:

```
lspci | grep Wireless
```

Then please post the output here.

---

### Post by jimn63 on 2009-07-02
I typed lspci then itpop up a lot like : PCI bridge, IDE interface,...
Ethernet controller: Attansic Technology Corp. L2 100 Mbit Ethernet dapter (rev a0)...
Sorry, I don't know what is "grep wireless" mean, thanks

---

### Post by t4thfavor on 2009-07-02
type exactly what he said into the terminal,

lspci means list pci hardware
grep wireless means show only lines that have "wireless" in them

so lspci |grep wireless means list pci hardware and only show me wireless.


I have a 900a and it's wireless works fine, I believe its an atheros 24xx chip.

---

### Post by synapsys on 2009-07-02
Don't forget the capital W in Wireless....very important. If you have an atheros chipset like t4thfavor then we should be able to get it working relatively easily. 

If you're having trouble simply copy and paste into the terminal.

---

### Post by jimn63 on 2009-07-02
Thank you guys very much, i'm going to try it more and more after i get home, i have to take the kids to CiCi Pizza now cause it is July 4 coming, thanks...:popcorn: thanks

---

### Post by Hobgoblin on 2009-07-02
> **jimn63 said:**
> Hi everybody! I've just bought an Asus eee 900 netbook on ebay. The original owner had deleted Window XP OS, and installed Ubuntu 8.04

Easy way, install Ubuntu 9.04 and it will work.

---

### Post by synapsys on 2009-07-02
> **Hobgoblin said:**
> Easy way, install Ubuntu 9.04 and it will work.

Good idea... i forgot ath5k comes standard with 9.04. Save yourself the headache and do what Hobgoblin says. I installed it on a laptop with ath 24xx chipset and it worked 'right out of the box'. Also, I would go with the full blown 9.04 as opposed to the netbook remix, unless you have one of those mini solid state hard drives.

---

### Post by t4thfavor on 2009-07-02
Its what I run on my 900a, and I said it works perfectly.

---

### Post by Hobgoblin on 2009-07-02
> **synapsys said:**
> Also, I would go with the full blown 9.04 as opposed to the netbook remix, unless you have one of those mini solid state hard drives.

I would also go for the desktop rather than the netbook remix, mainly because of the Intel video issues. 

It can be made bearable using the tips [here](http://ubuntuforums.org/showthread.php?t=1130582) though I found the .30 kernel broke CPU scaling (using p4_clockmod).  I fixed it by putting the 900 on ebay and buying a 900A (with the atom CPU), which doesn't appear to have the Intel video issues.

---

### Post by t4thfavor on 2009-07-02
I like your fix... I never had video issues on either of my 900a's They are actually snappy even running compiz. The only complaint I have is the slow flash disk.

The answer to your question is now:

Ebay the 900 and get a 900a. Or install 9.04 and don't upgade the kernel.

---

### Post by synapsys on 2009-07-02
I just can't see myself buying a netbook until the Atom dual cores become mainstream. 
Also solid state drives are not where they need to be yet.
Stick with the old spinning platters.

[http://ark.intel.com/Product.aspx?id=35641](http://ark.intel.com/Product.aspx?id=35641)

---

### Post by jimn63 on 2009-07-03
I typed lspci | grep Wireless but nothing happened...I tried to type iwconfig it says 
 lo       no wireless extensions
 eth0   no wireless extensions
Should i load Ubuntu 9.04? This Asus has 1Gb Ram and 16Gb SSD harddrive
[FONT=Century Gothic][SIZE=2]Chipset: Intel Mobile Chipset
Processor: Intel Mobile CPU 900MHz [/SIZE][/FONT]

---

### Post by Hobgoblin on 2009-07-03
> **jimn63 said:**
> 
Should i load Ubuntu 9.04? This Asus has 1Gb Ram and 16Gb SSD harddrive


I would try it from a live CD (or the liveCD image on a USB stick), but it will fix your wireless problems at the expense of some video problems.

> **synapsys said:**
> I just can't see myself buying a netbook until the Atom dual cores become mainstream. 


My 900A is a dual core Atom..... at least system monitor shows two CPUs with different (fluctuating) usage percentages.

And the 16GB SSD is just great for what I want, an ultra portable I can easily carry on my bicycle.  And no worries about old fasioned moving parts. ;)

---

### Post by synapsys on 2009-07-03
> **Hobgoblin said:**
> And the 16GB SSD is just great for what I want, an ultra portable I can easily carry on my bicycle.  And no worries about old fasioned moving parts. ;)

Just out of curiosity, how does the read/write speed compare to an 'old fashioned' hard drive? I've heard the write speed blows on those things.

---

### Post by joemun on 2009-07-03
I have an Asus eee 900 too...with 9.04 ubuntu everything works fine, the only caveat is the known bug with de intel video drivers (the workaround is in the sticky Jaunty bugs section)...I've read on the eeeforums that if you use a version such as intrepid or before intrepid, you should install Adam's kernel, which contains all the required drivers...My advice go Jaunty, and if your asus is the linux version (20GB=4GB SSD + 16GB SSD (slow)), install root (/) on the first SSD and home on the second (16GB) just as it was with Xandros...and one more thing I am using ext4 file system and so far (knock wood! just in case) no problems...

---

### Post by t4thfavor on 2009-07-04
> **Hobgoblin said:**
> 
My 900A is a dual core Atom..... at least system monitor shows two CPUs with different (fluctuating) usage percentages.


Its just a snazzy hyperthreading setup, as a dual core Atom would be in the a 3xx instead of a 2xx series. I have the same one, and its deinately not dual core.

---

### Post by jimn63 on 2009-07-04
Thank you joemun! My Asus is original Window XP version and reloaded Linux. I never been using Linux before and it is not easy for me , at first i tried to get a support DVD in order to load it back to window XP but i could find one. Then i wonder if i should buy a wireless adapter to plug in USB port , i'm not sure this resolve the problem??? Now , to your advice i'll try to do as you say. To make it more understandable, could you give me steps how to do it? Thank you very much

---

### Post by joemun on 2009-07-04
Download from Ubuntu.com the desktop 32 bit version. If you are using a Windows PC, burn the ISO downloaded to a CD or DVD (use ImgBurn from download.com and burn the image to CD or DVD). What I did: I bought a very cheap IDE to USB (generic) adapter, I don't have an external dvd, the IDE to USB came with 2 cables (the IDE cable and the power adapter); I used my desktop DVD drive as an external DVD (remove desktop cover, unplugged both cables from my DVD drive, plugged the 2 cables from the IDE to USB to the DVD drive, connected the USB to the Asus, and plugged the AC cable to the AC outlet then inserted the CD or DVD burned to the DVD tray. Turned ON the Asus, press Esc key, and selected DVD drive. Ubuntu live loaded and then clicked install. After that, since your Asus only have one SSD (16GB), then you can follow the installation as usual (select idiom, region, keyboard) it will format your SSD and takes about 15 min to complete the procedure. After that reboot and remove the DVD. 
If you want to do it from a pendrive, i recommend you to follow this instructions:

[http://blog.bokhorst.biz/1712/computers-en-internet/installing-ubuntu-jaunty-jackalope-asus-eee-pc/](http://blog.bokhorst.biz/1712/computers-en-internet/installing-ubuntu-jaunty-jackalope-asus-eee-pc/)

Hope it helps...

---

### Post by jimn63 on 2009-07-05
Thank you joemun, i'm doing it now

---

### Post by Hobgoblin on 2009-07-09
> **synapsys said:**
> Just out of curiosity, how does the read/write speed compare to an 'old fashioned' hard drive? I've heard the write speed blows on those things.

It's not noticeable, certainly compares well to my aging P4 laptop but then wouldn't writes to disk be cached anyway?

---

