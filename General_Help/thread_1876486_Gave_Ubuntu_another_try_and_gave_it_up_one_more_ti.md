---
title: "Gave Ubuntu another try and gave it up one more time"
date: 2011-11-06
forum: General Help
---

### Post by breezey on 2011-11-06
Every time Ubuntu released new version (since 8.10 as I remember) I try to install it to my desktop and I have never been able to make it running without issues with minimum effort (not much fiddling around post install).

I really hope that after a while (as my hardware become older) drivers won't be an issue any more with newer releases. But apparently that's not the case. Just installed Ubuntu 11.10 and Xubuntu 11.10 and found out that there is still issues with both ethernet and graphic adapters.

On Ubuntu 11.10, I needed to put extra options (noacpi and noapic) to be able to boot the DVD and installation was successful despite being very slow. After installation I was notified that ATI driver is available for update, I did an update and was failed. Then I downloaded the driver right from ATI website and successfully installed it, only to get blank screen after reboot.

I re-installed it, and this time I just left graphic adapter alone. But then I found out that for some reason my (wired) internet connection dropped intermittently. Connection is fast and normal each time I refreshed the connection, but after few minutes, it was getting slow again.

Then I installed Xubuntu, was prompted to update graphic adapter again, but I got the same black screen after reboot. Reinstalled it, left the graphic adapter as is, and I could not configure it to run dual monitor.

I really want to use Ubuntu as my main operating system but I am not sure if I will actually get it running perfectly without issue out of the box.

Btw, I am running ABIT IP-35 PRO, Intel Q6600 @2.4GHz, ATI HD 2600 XT.

---

### Post by kurt18947 on 2011-11-06
Those setting changes are not written anywhere except to the machine's RAM.  When you reboot, any changes are gone.  What might work for you (or not) is to create a bootable USB drive.  I use Unetbootin, there is a "startup disk creator" included with Ubuntu, not sure about Xubuntu.  If you  create a persistence partition the USB drive may remember those setting changes.  I say may because I have very little first hand experience with persistence.  

I use a boot manager and just create a small partition on the internal hard drive. 10 GB. is plenty for a testing installation.  I install to the hard drive then settings and changes are remembered.  if I don't like the install for whatever reason, deleting the partition makes it all go away. The boot manager I use can create 100+ primary partitions so the 4 partition limit isn't a factor and each partition is isolated, what happens in one has absolutely no effect on any other.

---

### Post by breezey on 2011-11-06
Hi kurt18947,

Thank you for your response. I didn't install it on USB though? I did dual boot install with my existing Windows 7.

---

### Post by philinux on 2011-11-06
> **kurt18947 said:**
> Those setting changes are not written anywhere except to the machine's RAM.  When you reboot, any changes are gone.

Errr..  He installed to his desktop so installing graphics drivers is not temporary.

I think the problem is with the ATI drivers. I have a NVIDIA card by choice as I knew it would be ok. Hopefully someone with ATI experience can help the OP.

---

### Post by kurt18947 on 2011-11-06
> **breezey said:**
> Hi kurt18947,

Thank you for your response. I didn't install it on USB though? I did dual boot install with my existing Windows 7.

:oops: Sorry, I misread your post.

---

### Post by Mark Phelps on 2011-11-06
There is no ATI restricted driver that will work with your card and any Ubuntu version newer than 8.10.  AMD (who bought out ATI) relegated your card, and lots of others, to unsupported status years ago, and quit writing Linux drivers for those cards.

Any driver you download now is NOT going to work with your card and recent versions of Ubuntu.

The default open-source drivers, which are installed automatically, are the only ones that will work now.

---

### Post by breezey on 2011-11-07
Thank you for your info Mark Phelps. It's good to know that. So I need to wait until I got a new video card.

Is Nvidia still linux friendler than ATI now?

---

