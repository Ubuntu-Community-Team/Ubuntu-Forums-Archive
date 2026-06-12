---
title: "internet connection with express card &quot;bandluxe&quot; modem"
date: 2010-02-15
forum: General Help
---

### Post by fxlovers on 2010-02-15
please help to configure internet connection in ubuntu 9.10,
i used bandluxe c100.
what the different between ubuntu 9.04 vs ubuntu 9.10?
before installing ubuntu 9.10, i used ubuntu 9.04
in ubuntu 9.04 i just  
1. Install wvdial
2. stop hal (sudo /etc/init.d/hal stop)
3. configure wvdial (sudo gedit /etc/wvdial.conf), and 
4. connect (sudo wvdial)
 
in my karmic koala, 
1. install wvdial <== done
2. stop hal (sudo /etc/init.d/hal stop) <== this command doesn't work
3. my modem couldn't detected
4. i can't make internet connection with ubuntu 9.10.
 
is necessary to stop hal service?
what is the command for ubuntu 9.04 with ubuntu 9.10 different?

:popcorn:

---

### Post by GeorgeVita on 2010-02-16
Hi **fxlovers**,
each version has some differences. From Ubuntu 9.04 HAL is starting to be deprecated (obsolete). On 9.10 modem-manager 'drives' your modem, ... , so it is better to try from start:

- boot without modem, **wait** for the system to load
- open a terminal window and try: **sudo dmesg -c**
this will show all system activity till then and will 'clear' this log. Next **dmesg** (without -c) will show only 'new' activity
- from terminal: **lsusb**
- check kernel version (from terminal): **uname -a**
- attach modem
- **wait** 30-40 seconds
- from terminal: **dmesg**
- from terminal: **lsusb**

- Notice any changes comparing 'lsusb' outputs. The 'new line' is your modem. Keep a note of 1234:5678 (vendorID, productID) and use them as search string to get new ideas/info.

- Search within second 'dmesg' for any driver used or any communication port created (**ttyUSB0** is /dev/ttyUSB0 and can be listed using: **ls /dev/ttyU***)

- If any virtual CD-ROM is created (will be listed as srX) it is possible to need an eject: **sudo eject srX**
Then the 'real modem' will appear (check again **lsusb** and **dmesg**)

>>> Ubuntu 9.10 needs update to recent kernel as initial version (LiveCD) had a bug that affects most 3g modems

>>> Possibly usb_modeswitch not needed on 9.10 (just eject the virtual CD-ROM)

>>> Although wvdial can connect you most times, you must check if recent network-manager & modem-manager works! (?)

>>> If still have problems (possibly from modem-manager) the equivalent to 'stop HAL' is to run (BEFORE attaching the modem):
```
sudo stop network-manager
sudo killall modem-manager

```

Post any new data to follow up, but DO NOT post output of the 'sudo dmesg -c' as this is huge and without data for your modem!

Regards,
George

---

### Post by fxlovers on 2010-03-22
> **GeorgeVita said:**
> Hi **fxlovers**,

.....
George

thanks for your assist george. and sorry for my long time respond.

i face a new problem right now george. could you help me please :popcorn:

[http://ubuntuforums.org/showthread.php?t=1435870](http://ubuntuforums.org/showthread.php?t=1435870)

---

### Post by ddreamer on 2010-08-19
Hi, please refer to [http://swiss.ubuntuforums.org/showthread.php?p=9739114&highlight=bandluxe+c120#post9739114](http://swiss.ubuntuforums.org/showthread.php?p=9739114&highlight=bandluxe+c120#post9739114)
In this way, my C120 work quite well with NetworkManager under Ubuntu 10.04. Others have reported that the method is suitable for 9.04 and 9.10 just as fine.

Good Luck

---

### Post by joelazz on 2011-02-27
Dear all, I have just gone through the process of making a Bandluxe 3G modem work on kubuntu 10.10.  It was working on 10.04 on my netbook but I have a new laptop and the previous settings did not work.  For the record, I'm using goeverywhere 3G service offered by GO provider in Malta, but probably it will work for all networks provided you change the APN appropriately.

One more thing, I could not get wvdial to work on the kubuntu 10.10.  However, I encountered sakis 3G which solved that problem for me.  The main problem I was encountering was that the modem was not listed in the /dev directory if I plug it it in after the computer has started.

Anyway, here are the instructions:
1) attach the express card to your PC

2) check if it has been mounted as a USB storage device:
        - df -h
        - find the device path (e.g. /dev/sr0)
        - eject that device:
                - sudo eject /dev/sr0
        - note that you may have the device listed as /dev/sr1 instead of /dev/sr0

3) check that it is located in your devices:
        - ls -l /dev/tty*
        - you should have 2 entries as: /dev/ttyUSB0 and /dev/ttyUSB1

4) If the device is not found anywhere, you need to do the following:
        - sudo rmmod option
        - sudo rmmod usb-storage
        - sudo modprobe option
        - sudo modprobe usb-storage
        -> now check if the /dev/ttyUSB* are found

5) download and install sakis 3G software from sakis3g.org

6) run it with the following settings:
        - USB modem
        - Bandluxe ***
        - Custom APN -> goeverywhere
        - username -> user
        - password -> pass

7) You should now be connected, use the ifconfig command to check that you have an entry ppp0 with an IP address assigned


IN CASE OF PROBLEMS:
    - check the existence of the following modules:
            - /lib/modules/2.*-generic/kernel/drivers/usb/storage/usb-storage.ko
            - /lib/modules/2.*-generic/kernel/drivers/usb/serial/option.ko

    - if these do not exist:
              - download the driver -> [http://www.bandrich.com/Download%5CAcer%20Aspire%20One.zip](http://www.bandrich.com/Download%5CAcer%20Aspire%20One.zip)
        - unzip
        - run (as root) bandrich.sh -> sudo ./bandrich.sh
        - let your computer reboot once this is done with the USB 3G modem connected.
        - check that you now have the entries /dev/ttyUSB0 and /dev/ttyUSB1, or /dev/sr0 (or /dev/sr1)

---

