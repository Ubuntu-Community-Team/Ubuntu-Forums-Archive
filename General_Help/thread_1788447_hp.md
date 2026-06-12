---
title: "hp"
date: 2011-06-22
forum: General Help
---

### Post by nikola_vince on 2011-06-22
dear friends

I installed   ubuntu 11.04 and i have a frustrating problem about my  printer Hp-1018. whenever i reboot my cpu, it ask me install Hp plug in .  

And other problem about bluetooth. whenever i reboot my cpu, bluetooth become invisible
everytime  i must carry out sudo killbluetooth and sudo bluetooth.

Do you have any idea for solutions?

 bluetooth problem is not  considerable but hp-1018 is very important

i m waiting your suggestions

thanks a lot.

---

### Post by linuxsyst on 2011-06-22
1) Open the terminal.

Don't copy the $ thing!

2)cut and paste the whole command line below to download the driver.
    ```
$ wget -O **foo2zjs.tar.gz**
```
Now unpack it:

   ```
 $ tar zxf **foo2zjs.tar.gz**
    $ cd foo2zjs
```
Now compile and install it:
    
```
$ make

Get extra files from the web, such as .ICM profiles for color correction,
and firmware.  Select the model number for your printer:
    $ ./getweb cpwl	# Get Minolta Color PageWorks/Pro L .ICM files
    $ ./getweb 2200	# Get Minolta 2200 DL .ICM files
    $ ./getweb 2300	# Get Minolta 2300 DL .ICM files
    $ ./getweb 2430	# Get Minolta 2430 DL .ICM files

    $ ./getweb 1000	# Get HP LaserJet 1000 firmware file
    $ ./getweb 1005	# Get HP LaserJet 1005 firmware file
    $ ./getweb 1018	# Get HP LaserJet 1018 firmware file
    $ ./getweb 1020	# Get HP LaserJet 1020 firmware file

    $ ./getweb 1025	# Get HP LaserJet Pro CP1025nw .ICM files

Install driver, foomatic XML files, and extra files:
    $ su			OR	$ sudo make install
    # make install

(Optional) Configure hotplug (USB; HP LJ 1000/1005/1018/1020):
    # make install-hotplug	OR	$ sudo make install-hotplug

(Optional) If you use CUPS, restart the spooler:
    # make cups			OR	$ sudo make cups
```\

Now create printer entries for your spooler. Create at least one queue for monochrome, and another queue for color printing. Create the queues first, then edit them and set the device options as desired.

I didn't write all of it myself I copied some and edited **alot**
And what title is it!
_**hp**_

---

