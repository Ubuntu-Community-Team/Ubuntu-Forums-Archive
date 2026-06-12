---
title: "hp deskjet 3050 work on 10.10"
date: 2010-12-19
forum: General Help
---

### Post by joelkat on 2010-12-19
??????

---

### Post by searchfgold6789 on 2010-12-19
Yes.

---

### Post by kgarbutt on 2010-12-19
Hey Joel,

I am not sure about 10.10, but I have a HP Deskjet 3845 running just fine on 9.10. The only thing I did to get it going was go to System>Administration>Printing and added it.

Should that not work I know that hplip will work. You would have download the latest hplip from here:

[http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/)

After you download it move it to the desktop to make install easier.

You must run it from the terminal like this :

(Cut & Paste into terminal:)
sh hplip-3.10.9-run

Then just follow the prompts. It will get your HP printer running for sure. But try the add printer first.

---

### Post by joelkat on 2010-12-19
Thanks for the answer but I need to know for 1000000% sure.

---

### Post by joelkat on 2010-12-19
so does anyone have the answer?

---

### Post by Sol29 on 2010-12-20
Thanks a lot [kgarbutt]("http://ubuntu-ky.ubuntuforums.org/member.php?u=719803"), I followed your instructions and the printer works fine! The only thing, when I saved the file on my desktop, I had to right click on it, select properties, go to permissions, and then check "allow executing file as a program". Then I double clicked on the file, and chose "run from terminal". It did the rest by itself, but make sure the printer is already connected to the network so that the setup can take place automatically! I'm using ubuntu 10.04 though, not 10.10..

---

### Post by theasprint on 2010-12-20
Hi,

Just to assure you.
I have an OFFICEJET. That means Scanning, Printing and Faxing.
And all the features work on Ubuntu 10.04

So that means your printer should 100% work.

Just get the HP Linux software from Ubuntu Software Center and you'll be fine.

---

### Post by joelkat on 2010-12-20
im on 10.10

---

### Post by joelkat on 2010-12-20
I am getting one for x-mas and I need to know if itll work...

---

### Post by kanishkdudeja on 2010-12-20
it should work.

Check this page..

[http://h71028.www7.hp.com/enterprise/cache/587603-0-0-0-121.html?jumpid=go/linuxprinting](http://h71028.www7.hp.com/enterprise/cache/587603-0-0-0-121.html?jumpid=go/linuxprinting)

It it contains your printer in this list, then it wil work.

---

### Post by joelkat on 2010-12-20
the sites down or something

---

### Post by kanishkdudeja on 2010-12-20
You will have to wait then. :(

---

### Post by joelkat on 2010-12-20
its been down for like a week f m l

---

### Post by kanishkdudeja on 2010-12-20
well i searched the forum for you.

And theres not much positive.

Look into:

[http://ubuntuforums.org/showthread.php?t=629654](http://ubuntuforums.org/showthread.php?t=629654)

[http://www.uluga.ubuntuforums.org/showthread.php?p=10229117](http://www.uluga.ubuntuforums.org/showthread.php?p=10229117)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10258462](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=10258462)

---

### Post by joelkat on 2010-12-20
the 2 bottom ones said it will but whatever it better work... I hope it does hplip seems like itll work..

---

### Post by kanishkdudeja on 2010-12-20
hmm. yeah. hope so. otherwise you can dual boot :P

---

### Post by Sol29 on 2010-12-20
I bought this printer yesterday and works fine with ubuntu 10.04, so I don't see why it should not work with 10.10. The printer was not recognised initially, but now works after I installed the drivers (as described above).

---

### Post by Flywaver on 2010-12-22
I also have a DeskJet 3050 and when I run hp-setup it always tells me: error: No devices found on bus: usb...I tried on all of my USB ports! :(
I am running Ubuntu 10.10 and I did d/l and run sh hplip-3.10.9.run...it detected my distro, asked for password and then the terminal screen closes!

---

### Post by G.A. Heath on 2010-12-22
I signed up here just to let you know I got this printer working just a few minutes ago via wifi using the following steps:
1: goto [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/) and click on the link to download hplip-3.10.9.run
2: find the file hplip-3.10.9/ppd/hpcups/hp-deskjet_3050_j610_series.ppd.gz and extract its contents to a known location.
3: add the printer, and when given the chance, choose to provide your own ppd file and provide that file.

This was done on a relatively new install of 10.10 on two different machines.

---

### Post by Marky Mark on 2010-12-23
> **G.A. Heath said:**
> I signed up here just to let you know I got this printer working just a few minutes ago via wifi using the following steps:
1: goto [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/) and click on the link to download hplip-3.10.9.run
2: find the file hplip-3.10.9/ppd/hpcups/hp-deskjet_3050_j610_series.ppd.gz and extract its contents to a known location.
3: add the printer, and when given the chance, choose to provide your own ppd file and provide that file.

This was done on a relatively new install of 10.10 on two different machines.

Thanks for that, I'll give it a go tonight. The scanner bit works fine, but still can't print.  foomatic-rip-hplip missing, hopefully the above will solve this.

MyM

---

### Post by Flywaver on 2010-12-23
> **G.A. Heath said:**
> I signed up here just to let you know I got this printer working just a few minutes ago via wifi using the following steps:
1: goto [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/) and click on the link to download hplip-3.10.9.run
2: find the file hplip-3.10.9/ppd/hpcups/hp-deskjet_3050_j610_series.ppd.gz and extract its contents to a known location.
3: add the printer, and when given the chance, choose to provide your own ppd file and provide that file.

This was done on a relatively new install of 10.10 on two different machines.

Thanks a LOT it worked perfectly!! :D

---

### Post by joelkat on 2010-12-25
anyone im running 10.10 and when it turns on you know how it prints it own test page and makes you scan it? all it does is tell me error scan with computer

---

### Post by Marky Mark on 2010-12-26
> **Flywaver said:**
> Thanks a LOT it worked perfectly!! :D


Me too, many thanks.

---

### Post by joelkat on 2010-12-26
please some help with my problem

---

### Post by narcisgarcia on 2010-12-31
In Ubuntu GNU/Linux 10.04 (Lucid Lynx)

I've solved it with a HP DeskJet 3050 plugged on USB installing [HPLIP 3.10.9]("http://hplip.sourceforge.net/") and making the wizard to uninstall previous HPLIP versions.

I added some packages needed, such as python-dev

* Take care of running **hplip-3.10.9.run** in a terminal, to see any error message if installer breaks instead of complete.

---

### Post by cgul1 on 2011-03-31
I realize that this is an old thread, but instead of starting a new one...

I just got this printer, I was able to install hplip via the download page. Installing via software center, the program did not detect the printer as some others have experienced.

From what I can tell the the printer works basic print (no duplex) and xsane scan works ok. It looks like the gui is not supported in 10.10? disappointing - anyone else get the gui to work with this printer and maverick?

thanks:cool:

---

### Post by kkbubu on 2011-05-07
> **Flywaver said:**
> Thanks a LOT it worked perfectly!! :D

This didn't work for me: I am not sure how to find the ppd file (the instructions given were a bit sparse, and I'm a newbie).  For example, I couldn't execute the .run file, or extract the ppd file mentioned.

I'm running 10.04

---

### Post by iris-n on 2011-09-17
For the newbies here (or for those who just don't like manually installing things), there's a simpler solution.

Just add hp's ppa [https://launchpad.net/~hplip-isv/+archive/ppa](https://launchpad.net/~hplip-isv/+archive/ppa)
and run sudo apt-get update && sudo apt-get upgrade

This will upgrade your hplip to the latest version, which includes support for the 3050 and others. I just did this now, and it is printing and scanning without problems.

---

