---
title: "Printer Samsung ML 1865 doesn't work"
date: 2011-12-24
forum: General Help
---

### Post by EasyNow on 2011-12-24
I'm running Ubuntu 10.10. All works fine, except a printer which I bought today - Samsung ML 1865 with all Mac and Linux support. Which I already doubt. I successfully installed a needed driver, which was downloaded from samsung.com, and I can see in System/Preferences/Printing my printer with green check on it. Which I supposed to be a good sign. But every time I inquire to print something I have then a printed list with the following statement:
Internal Error - please use the proper driver.

Position : 0x0 (0)
system : h6fw_5.49/xl_op
Line: 180
Version : SPL 5.49 10-20-2010

I rebooted my computer then and ran windows 7. On startup I installed a driver for the printer and try to print ubuntu.com homepage. And it worked.
So I rebooted back on my ubuntu and every time it's printing something I see only an internal error on the blank white paper.

---

### Post by EricWilliamson on 2011-12-24
Me too :-(
" internal error -Please use proper driver"
I think I haven't installed "unified printed driver" properly.
It thinks I have ML-1860.
Cant remove "unified printed driver" either.
Says I need Super User -
Doesnt allow mw to put in SUDO ???
I think I'm doing something wrong.
Hellllllllppppppppppp.
I've fallen and I can't use SUDO properly.
(the following should be read with a William Shatner voice)
Printer.................Won't.....................Work
Must...................ask ........................For..........................Help......................
Please.....................Help...........................................Kirk Out

---

### Post by EricWilliamson on 2011-12-24
Solved

[http://ubuntuforums.org/archive/index.php/t-1847122.html](http://ubuntuforums.org/archive/index.php/t-1847122.html)

---

### Post by EricWilliamson on 2011-12-24
avantgardaclue
September 20th, 2011, 05:58 AM

Just  bought one of these nifty laser printers and struggled like mad to get  it to work until I sussed how to do it and it was simplicity itself!

Process....

Add to repositories under update manager...

"deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra" without the quote marks!

Then get the apt-key

Refresh your repository listings

Go to synaptic and do search for... samsungmfp

Install  samsungmfp-data & samsungmfp-driver

Plug in, turn on samsung laser, 'Add Printer' and presto should work!!

More info at [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

---

### Post by EasyNow on 2011-12-25
[COLOR="Red"]Very important:[/COLOR] **you must have completely removed all prior installations of the Unified Linux Driver before following next steps!**

1. Alt+F2
2. paste /etc/apt/sources.list
3. then add to repositories: deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra
4. Open terminal
5. sudo -s (it will ask for your password - type it)
6. after becoming root paste into your terminal window:
   wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
7. Go to [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg)
8. Save the file\page as suldr.gpg in your home derictory
8. Go back to the terminal and paste:
   sudo apt-key add suldr.gpg
9. To refresh everything, paste into your terminal:
   sudo apt-get update
10. Then go to System/Administration/Printing and make sure you have you ML-1865 shown in it, if not - add it and finally start to use it properly.

---

### Post by hounddog32 on 2012-01-09
Almost perfect instructions, EasyNow - here's how I did it.

[LIST=1]
[*]Opened "Software Sources" through Unity
[*]Selected the 'Other Software' tab, clicked 'Add...' then pasted in *deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra*
[*]Hit ctrl + alt + t for terminal then ran *sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -* (it asked me for my password for sudo, of course)
[*]Ran *sudo apt-get update* to load the new source into the computer
[*]Opened the Software Centre from unity, searched for *samsung config* and installed *Samsung Unified Driver Configurator (QT4 interface)*, along with the driver.
[*]Searched for *Samsung* in unity and ran the configurator. I hit refresh, then followed the steps to add the printer.
[/LIST]
Although the configurator application thinks that the printer is a 'Samsung ML-1860 series', it appears to work perfectly.

---

### Post by matza55 on 2012-10-12
Thanks for the god help. Now it worked fine! :popcorn:

---

### Post by -::Bas::- on 2013-06-30
I'm running Ubuntu 12.04 with the classic Gnome desktop and the above help didn't work for me.
What I ended up doing was (all through the terminal):

1. Using the terminal add the correct software source
```
sudo bash -c 'echo "deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra" >> /etc/apt/sources.list'
```

2. Add the key:
```
wget -O - http://www.bchemnet.com/suldr/suldr.gpg | sudo apt-key add -
```

3. Update the software sources
```
sudo apt-get update
```

4. Look for what driver number your printer needs on this page:
[http://www.bchemnet.com/suldr/supported.html](http://www.bchemnet.com/suldr/supported.html)

5. Install the driver in a terminal
```
sudo apt-get install suld-driver-4.00.35 
```(replace the last number with the driver you need and found in 4)

Now installing the printer through the normal 'add printer' dialog works fine.

---

### Post by scouser73 on 2013-06-30
I use this site to help install my Samsung printer [https://sites.google.com/site/easylinuxtipsproject/samsungprinters](https://sites.google.com/site/easylinuxtipsproject/samsungprinters)

---

