---
title: "Brother printer driver issues"
date: 2009-07-08
forum: General Help
---

### Post by whitehousea on 2009-07-08
Hello,

I am newish to Linux and am having a problem installing the drivers for my Brother wireless printer.  I downloaded the proper drivers and when I try and install them I am getting this error for both the LPR and CUPS drivers.  Any help would be greatly appreciated as I feel I am missing something very simple and newbyish.  Thanks.

sudo dpkg -i --force-all --force-architecture lpr-mfc490cwlpr-1.1.2-2.i386.deb

dpkg: error processing lpr-mfc490cwlpr-1.1.2-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lpr-mfc490cwlpr-1.1.2-2.i386.deb

---

### Post by HereInOz on 2009-07-08
What happens if you just double click on the .deb file?  Does that also create the error when you attempt to run the install?

---

### Post by Shazaam on 2009-07-08
There are drivers for Brother printers in the repositories. Go to System>Administration>Synaptic Package Manager. First thing to do is hit the "Reload" button in the upper left then search for Brother.
What I have found with the downloaded Brother drivers is you don't have to run that command. Just do as HereInOz suggested.

---

### Post by whitehousea on 2009-07-08
Yes I have attempted to install the .debs by clicking on them but I get this error

Package: mfc490cwcupswrapper

Status: Error: Wrong architecture 'i386'

Shazaam - I tried that as well there are lots of Brother drivers available but none for my model of printer.

Any other suggestions ? and thanks for the input.

---

### Post by Shazaam on 2009-07-08
When you ran that command were you in the directory where the drivers were?
Lets say you downloaded them to your desktop. You would enter this first (cd is change directory)...
```
cd /home/yourusername/Desktop
```
or...
```
cd ~/Desktop
```
Then you would run the dpkg -i command.

---

### Post by whitehousea on 2009-07-08
Roger, I have the drivers in a folder called Downloads and I am in the proper dir with the drivers ls'd.  Then when I run the command it gives me those errors thats why I am confused because I know for sure I am in the proper dir.

whitehouse@whitehouse-laptop:~$ dir
Desktop    Downloads    Pictures  Templates
Documents  examples.desktop  Music            Public    Videos
whitehouse@whitehouse-laptop:~$ cd Downloads
whitehouse@whitehouse-laptop:~/Downloads$ ls
mfc490cwcupswrapper-1.1.2-2.i386.deb  mfc490cwlpr-1.1.2-2.i386.deb
whitehouse@whitehouse-laptop:~/Downloads$ sudo dpkg  -i  --force-all  --force-architecture lpr-mfc490cwlpr-1.1.2-2.i386.deb
dpkg: error processing lpr-mfc490cwlpr-1.1.2-2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 lpr-mfc490cwlpr-1.1.2-2.i386.deb

---

### Post by Shazaam on 2009-07-08
I see this...
```
mfc490cwlpr-1.1.2-2.i386.deb
```
in your directory and this...
```
sudo dpkg -i --force-all --force-architecture lpr-mfc490cwlpr-1.1.2-2.i386.deb
```
Maybe drop the first lpr- from the front of the command? So it would look like this...
```
sudo dpkg -i --force-all --force-architecture mfc490cwlpr-1.1.2-2.i386.deb
```

---

### Post by whitehousea on 2009-07-08
I gave that a try and it started unpacking then I got this error ....

```

whitehouse@whitehouse-laptop:~/Downloads$ sudo dpkg -i --force-all --force-architecture mfc490cwlpr-1.1.2-2.i386.deb
[sudo] password for whitehouse: 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 120368 files and directories currently installed.)
Preparing to replace mfc490cwlpr 1.1.2-2 (using mfc490cwlpr-1.1.2-2.i386.deb) ...
Unpacking replacement mfc490cwlpr ...
Setting up mfc490cwlpr (1.1.2-2) ...
mkdir: cannot create directory `/var/spool/lpd/mfc490cw': No such file or directory
chown: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc490cw': No such file or directory

```I just tried the cups driver and am currently here ...

```

hitehouse@whitehouse-laptop:~/Downloads/Drivers$ sudo dpkg -i --force-all --force-architecture mfc490cwcupswrapper-1.1.2-2.i386.deb
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package mfc490cwcupswrapper.
(Reading database ... 120368 files and directories currently installed.)
Unpacking mfc490cwcupswrapper (from mfc490cwcupswrapper-1.1.2-2.i386.deb) ...
Setting up mfc490cwcupswrapper (1.1.2-2) ...
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

```Its currently at this point not doing anything I believe ... so confused.

---

### Post by whitehousea on 2009-07-08
Can anyone help me with this problem ? I still cannot figure it out.  I think the cups driver has installed OK but I am still having trouble with the LPR.  I am currently at this stage of the install and get this error ... basically I think its something with permissions as it will not allow me to make the folder for the lpd in the var/spool dir, any ideas?

```

whitehouse@whitehouse-laptop:~/Downloads/Drivers$ sudo dpkg -i --force-all --force-architecture mfc490cwlpr-1.1.2-2.i386.deb
[sudo] password for whitehouse: 
dpkg - warning, overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 120371 files and directories currently installed.)
Preparing to replace mfc490cwlpr 1.1.2-2 (using mfc490cwlpr-1.1.2-2.i386.deb) ...
Unpacking replacement mfc490cwlpr ...
Setting up mfc490cwlpr (1.1.2-2) ...
mkdir: cannot create directory `/var/spool/lpd/mfc490cw': No such file or directory
chown: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc490cw': No such file or directory

```Any help would me much appreciated.

---

### Post by whitehousea on 2009-07-08
Problem resolved, thanks guys.

---

### Post by Shazaam on 2009-07-08
Just for posterity, how did you solve it?

---

### Post by AlanRick on 2009-07-12
Also having brother problems...

I installed my wifi brother printer MFC-7804W  using printer setup and it worked beautifully, even though the driver MFC-7820N was used which is only a close fit (but it works).

Now I've made the effort to get the proper driver MFC-7840W from brother's website and installed the cups driver (grep verifies it is installed). 

Problem is that when I use the wizard at [http://localhost:631/printers](http://localhost:631/printers) to try and modify the settings to the correct driver (7840w) it does not show it in the list of possible drivers which is strange because ubuntu has installed it ok.

**Any idea how to switch the driver from 7820 to 7840W, preferably using a graphic UI to do it?**

Alan

---

### Post by AlanRick on 2009-07-12
Here's the results of the brother grep just in case it shares some light:
```
dpkg  -l  |  grep  Brother
ii  brmfc7840wlpr                              2.0.2-1                                              Brother MFC-7840W LPR driver
ii  brmfcfaxcups                               1.0.0-2                                              Brother MFC/FAX fax share function driver
ii  brmfcfaxlpd                                1.0.0-2                                              Brother MFC-FAX LPD driver
ii  brscan-skey                                0.2.1-3                                              Brother Linux scanner S-KEY tool
ii  brscan3                                    0.2.6-1                                              Brother Scanner Driver
ii  cupswrappermfc7840w                        2.0.2-1                                              Brother MFC7840W CUPS wrapper driver

```
The 7840W driver is shown so I don't understand why it doesn't appear in the cups drop down list to select.

---

### Post by VastOne on 2009-07-15
> **whitehousea said:**
> problem resolved, thanks guys.

how!!!!!!

---

### Post by AlanRick on 2009-07-16
I resolved my problem. 
Turns out the Brother driver installs as Brother MFC7840W whereas from the open distro they are Brother MFC-7.."  (note the hyphen)

So my driver was appearing at the *bottom* of the last rather than in the middle of the list with the other "hyphen" drivers thanks to the sort. ](*,)

Anyway I'm not sure the command

```

sudo aa-complain cupsd
sudo mkdir /usr/share/cups/mode

```
helps with the whitehouse problem but I had to use this before re-installing  the driver (even though this turned out to be a wild goose chase).

---

### Post by xfran on 2009-12-22
It worked for me doing as described in:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html")

But instead of installing from command line:
```
dpkg  -i  --force-all  (lpr-drivername)
```

which gave me the error here:
```
mkdir: cannot create directory `/var/spool/lpd/mfc490cw': No such file or directory
chown: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
chgrp: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
chmod: cannot access `/var/spool/lpd/mfc490cw': No such file or directory
```


I double clicked the .deb packages from nautilus, first the lpr driver, then the cupswrapper driver, and then followed the rest of the instructions.

I am using UNR 09.10 on EEE 1005HA, printer Brother mfc490cw.

Good luck!

---

### Post by sunbear on 2009-12-23
> **VastOne said:**
> how!!!!!!

In case anyone else needs to know. I successfully got my MFC-490cw printing on Ubuntu 9.05 64-bit by carefully following the directions on the Brother website:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

Some people are probably having problems because they missed some of the preparatory steps:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/before.html)

Note that you must install both the LPR and the CUPS driver

LPR instructions
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn3.html)

CUPS instructions
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

Hope this helps someone

---

