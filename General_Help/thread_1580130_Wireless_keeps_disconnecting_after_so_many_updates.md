---
title: "Wireless keeps disconnecting after so many updates"
date: 2010-09-22
forum: General Help
---

### Post by YMS_1975 on 2010-09-22
I have noticed a consistent issue with Ubuntu. I have it running on an older Pentium with 1 GB ram.

After every three or four...maybe if I'm lucky five updates, for whatever reason, the wireless connectivity stops working.

Then I come back to these forums and have to research how to fix it. I keep the Ubuntu up to date, but....can't figure out why this keeps happening.

It's not like we're adding any software to the PC (externally or from the Ubuntu Software Centre) so why does this keep happening?  :confused:

BTW, I do not change my SSID or password (I've used the same credentials since I set up my network) so it's not like I've inputted in something incorrectly.

This PC is strictly used to surf the net and once in a blue moon, use Open Office (which Ubuntu is obviously equipped to run). The networking card is relatively new; Heck, I've posted about it on this site before. I got Ubuntu to work with it, so it's not the network card.....

Any thoughts?](*,)

---

### Post by YMS_1975 on 2010-09-26
No takers huh?

---

### Post by coffeecat on 2010-09-26
> **YMS_1975 said:**
> No takers huh?

There might have been if you had posted some relevant information. Such as...

What wireless NIC are you using? Is this a laptop or desktop? If desktop, pci card or usb? Do you know the chipset? If you don't, open a terminal and post the output of:

```
lspci
```.. if the nic is a PCI or internal laptop one. Or:

```
lsusb
```... if a usb device.

Also - can you confirm that you are still running 9.10 as your profile says, or a later version. And what "fixes" have you applied to your system?

Do you have any other machines or operating systems connecting to your wireless network and is there any problem with any of them?

That'll be enough to be going on with. :) You might not get any more from me for the next few hours. Late here.

---

### Post by YMS_1975 on 2010-10-25
I know it's been a while since I posted the original post, but I just thought I'd post something new to it since I feel it's relevant to this scenario.

That PC was working just fine until I updated it last, and then the wireless stopped (again). It's been dead up until yesterday.

I noticed that 10.10 was out and decided to download the ISO (on another computer in the house, burned it to CD) and update it. As soon as I updated it (via CD), guess what? It worked again.

Wireless connection is back up and running.  :confused:
It's working great now, but I wonder how many updates before it stops working again. 

Oh well....just glad she's working again.   :)

---

### Post by idealsceneprod on 2011-03-04
I had a problem with Maverick wireless network turning on and off by itself after waking from sleep.  Turns out the problem was I had nm-applet running along with wicd-daemon. "Killall wicd" resolved the issue and I was able to put it to sleep and wake it up, no issues.  I posted it on my blog here: [http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/](http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/)

---

### Post by idealsceneprod on 2011-03-04
For anyone out there who still has this problem, my solution was to kill wicd-daemon... I had nm-applet and wicd running together and they were conflicting.  [http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/](http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/)  Val

---

### Post by YMS_1975 on 2013-01-22
Can't believe I'm still having connectivity issues in 2013!!!
My younger son has been after me to install the latest version of Ubuntu on his Dell Studio 540 desktop. I did, and now it won't recognize the wireless connection. The SSID and the password are correct, but it won't connect.

I also noticed I keep getting different types of error messages. I just installed 12.10 and I kept getting a screen dump (full of text) that I could never seem to capture as the PC became unresponsive. I formatted and reinstalled 12.10 a few times. Now the screen dump seems to have corrected itself, but I just can't connect.

I created another thread about this just a few days ago ([http://ubuntuforums.org/showthread.php?t=2106965](http://ubuntuforums.org/showthread.php?t=2106965)) to see if I could get some help, but since it related to my original thread (from back in 2011) I thought I'd just post my latest experience here as well. **How is it that something as basic as connectivity is always a struggle with Ubuntu?** How hard would it be for them (I honestly don't know) to have all the necessary network drivers included on their .ISO image so that Ubuntu can work out of the box? Clearly they have increased the size of the image file (as it no longer fits on a CD), so why do I have to tinker around with my network cards drivers?

Sorry for the rant; THIS IS VERY FRUSTRATING!!!!!!

---

### Post by bogan on 2013-01-23
Hi!, **YMS_1975,**

You never did Post any system details, so you do not have very good grounds for ranting here.

I ve had similar problems for years and am still trying to solve them, with much help from these forum and **chili55**5 especially .

The latest development is a generalised update to network drivers called:  'backports-modules-[COLOR=Red]cw[/COLOR]'. I have found it a great improvement, but not the perfection you seem to want.

> There is a package of newer updated drivers, including Realtek, called  compat-wireless. This is just the Ubuntu-customized version.You need to install the version for your ubuntu distribution, example for 12.10:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```Thanks due to **chili** for this.

Chao!, **bogan.**

---

### Post by bogan on 2013-01-24
Hi!, **YMS19_75,**
deleted'
Wrong Thread

---

### Post by coffeecat on 2013-01-24
> **YMS_1975 said:**
> 
I created another thread about this just a few days ago ([http://ubuntuforums.org/showthread.php?t=2106965](http://ubuntuforums.org/showthread.php?t=2106965)) to see if I could get some help

Since your other thread is active, I'll close this one so that community support is not diluted.

Thread closed.

---

