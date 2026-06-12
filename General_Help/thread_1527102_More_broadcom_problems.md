---
title: "More broadcom problems"
date: 2010-07-08
forum: General Help
---

### Post by Nick_Jinn on 2010-07-08
So this is an older Broadcom internal laptop card from early 2005, came with an Acer Aspire 3000, a budget model from back in the day. This isnt exactly the same model that I have seen talked about, but its a 54 something airforce something again.....sorry about the less than precise phrasing, but I am on a different PC as I erase Mint with Xubuntu on the one I am working on.

So I am trying to trouble shoot this....is there a better way to install the proper drivers via the command line that works better than just installing the hardware drivers from the control center? That one, at least in Mint, was buggy, and did not allow me to connect to the internet unless I used an additional external wireless card....not what my client wants. 

I dont believe I have the disk for the windows driver. If needed I could try to get the exact model number from the internal wireless card again.

---

### Post by NFblaze on 2010-07-09
Try looking for the .deb of the hardware drivers and install them using those. I've usually had bad luck with jockey-gtk (the hardware drivers gui). Though, I have usually been successful with .debs

---

### Post by Nick_Jinn on 2010-07-09
I no longer have the hardware drivers since I completely erased Windows on this PC. This is an internal card.

The problem with this card seems to exist in Ubuntu, Xubuntu and Mint. When I install the default version it disables wireless and wont detect anything, EVEN when I use an external wireless that WAS working before I installed it. The default driver makes it worse by preventing me even from connecting with other cards.


Where do I go from here? What do I try next?

---

### Post by bobcollard on 2010-07-09
> **Nick_Jinn said:**
> I no longer have the hardware drivers since I completely erased Windows on this PC. This is an internal card.

The problem with this card seems to exist in Ubuntu, Xubuntu and Mint. When I install the default version it disables wireless and wont detect anything, EVEN when I use an external wireless that WAS working before I installed it. The default driver makes it worse by preventing me even from connecting with other cards.


Where do I go from here? What do I try next?
   Open Terminal:
                               ```
sudo apt-get install b43-fwcutter
```
                                   *Step by step link at:*
 

 *[http://dimitar.me/?p=728](http://dimitar.me/?p=728)*

---

### Post by Nick_Jinn on 2010-07-10
I appreciate the help, but this is BCM 4318.

That tutorial seems to be for BCM4311-, BCM4312-, BCM4313-, BCM4321-, and BCM4322. I am not sure if its going to work.


I have an Acer Aspire 3000 that I am working on, and this particular card is a real pain to work on.

---

### Post by Nick_Jinn on 2010-07-10
This didnt work.

Also, this is an older card and not one of the ones listed in that link.



I also went to the thread specifically for my card, and no luck there either. Any ideas on what to try next?

---

### Post by bobcollard on 2010-07-10
> **Nick_Jinn said:**
> This didnt work.

Also, this is an older card and not one of the ones listed in that link.



I also went to the thread specifically for my card, and no luck there either. Any ideas on what to try next?
Perhaps a hardware solution for around $30.00 US?  My Broadcom card burnt out and I'm using a  Netgear WG111v3 USB Wireless Device.  It has the driver built in to the dongle.

---

### Post by NFblaze on 2010-07-10
Well, looking up the model you provided it states that th BCM4318 cant use the Broadcom STA.

I did find these steps on the Ubuntu wireless page try these out

> Installing BCM43xx drivers

8.04.x (Hardy Heron), 9.04 (Jaunty Jackalope), 9.10 (Karmic Koala), 10.04 (Lucid Lynx)

The Ubuntu kernel in versions 8.04.x (Hardy Heron) and higher do provide the b43 drivers, however due to copyright restrictions not the proprietary firmware which is required to run your card. See here for a list of known PCI devices and their available modes as well as supported/unsupported chipsets.

The following instructions explain how to extract the required firmware.

b43 - Internet access

If you have some other kind of internet access on your computer, you can download the firmware by simply installing the b43-fwcutter package which does the download and setup for you automatically.

b43-fwcutter.png

To install b43-fwcutter issue the following command in a terminal and follow the prompts:

~$ sudo apt-get install b43-fwcutter

Back to top

b43 - No Internet access

If you do not have any other means of internet access on your computer, you will have to install b43-fwcutter and setup manually (without the firmware automatically downloading and being set up).

b43-fwcutter is located on the Ubuntu install cd under ../pool/main/b/b43-fwcutter/ or in the official repositories online.

Double click on the package to install or in a terminal navigate to the folder containing the package and issue the following command:

:/b43-fwcutter/$ sudo dpkg -i b43-fwcutter*

Step 1.

On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Step 2.

Copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware:

~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o

Note: A computer restart may be required before using the wifi card. 

---

### Post by Famicube64 on 2010-07-10
I have the same chipset (BCM4318] and have use the instructions at[ this]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/") site since Ubuntu 8.10. 9.10 and up, however, you'll need to run wifi.sh every time you boot up in order to connect.

Edit: This works on any Linux disto when you install ndiswrapper and the utils.

---

### Post by Nick_Jinn on 2010-07-10
> **Famicube64 said:**
> I have the same chipset (BCM4318] and have use the instructions at[ this]("http://sampbar.com/2009/04/broadcom-bcm4318-ubuntu-intrepid/") site since Ubuntu 8.10. 9.10 and up, however, you'll need to run wifi.sh every time you boot up in order to connect.

Edit: This works on any Linux disto when you install ndiswrapper and the utils.


While *I* might do that, this is for a client, so I dont really feel comfortable with that solution.

---

