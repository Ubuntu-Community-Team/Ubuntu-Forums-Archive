---
title: "Trying to install Opera web browser"
date: 2011-09-03
forum: General Help
---

### Post by 3lud13 on 2011-09-03
I'm trying to install the opera web browser as it is not in the Ubuntu Software Center I went to the website and downloaded the package however I still can not seem to install it the first time I tried it seems to work fine but isnt actually installed and then when I downloaded it again and tried it says the package file is corrupt is there maybe another way I could download and install it.
Also Before people say I can use other web browsers yes I do realise this and I do but because of some stuff I do and visiting the same pages with multiple accounts I use multiple browsers to save logging in and out of accounts all the time.

---

### Post by claracc on 2011-09-04
You can try to install opera browser following the method in this link: [http://www.ubuntugeek.com/install-opera-web-browser-in-ubuntu.html](http://www.ubuntugeek.com/install-opera-web-browser-in-ubuntu.html)

---

### Post by raja.genupula on 2011-09-04
[http://www.opera.com/browser/download/?os=linux-i386&list=all](http://www.opera.com/browser/download/?os=linux-i386&list=all)

here choose what ever the version you want .

---

### Post by stinkeye on 2011-09-04
I was trying to install opera on Ocelot 11.10, and when trying to install
the downloaded deb file with Gdebi, had the error message 
***The package might be corrupted - check permissions**.*

Installing from the repo worked.(Installed Version 11.51, Build 1087)
    ```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
    ```
sudo sh -c 'echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list.d/opera.list'
```
    ```
sudo apt-get update
```
    ```
sudo apt-get install opera
```


You can also install testing releases of opera from this same repo.
The package is called **opera-next** and runs independently from the opera stable version so
you can install both if you like to test the latest releases.

---

### Post by 3lud13 on 2011-09-04
> **stinkeye said:**
> I was trying to install opera on Ocelot 11.10, and when trying to install
the downloaded deb file with Gdebi, had the error message 
***The package might be corrupted - check permissions**.*

Installing from the repo worked.(Installed Version 11.51, Build 1087)
    ```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
    ```
sudo sh -c 'echo "deb http://deb.opera.com/opera/ stable non-free" >> /etc/apt/sources.list.d/opera.list'
```
    ```
sudo apt-get update
```
    ```
sudo apt-get install opera
```


You can also install testing releases of opera from this same repo.
The package is called **opera-next** and runs independently from the opera stable version so
you can install both if you like to test the latest releases.

Tried this and after typing in the first command it came up with "gpg no valid openPGP data found."

Also tried the others once again with no success I'm really not sure if I am doing something wrong or what as everything I have installed has been fine

---

### Post by stinkeye on 2011-09-04
Should work, try again.
Just copy and paste in the terminal.
After entering the command you should see as in pic.
At this stage, type in your password and press enter.

---

### Post by 3rdalbum on 2011-09-04
Probably the first thing I'd check is whether Opera is actually installed on your computer from that first attempt. If a successful package installation was reported, it's highly unlikely that the contents of the package were not installed.

**Opera users, how do you start it in the terminal?**

3lud13, try putting this into the terminal to start Opera in the event that it is actually installed:

```
opera
opera-browser
```

Not sure which of these is correct, but it doesn't hurt to just try them. If Opera is installed but not showing up in your menu, that's pretty easily fixed.

---

### Post by no2498 on 2011-09-04
id say its in his/her repose not set to allow all
and will tell them to put the cd in

---

### Post by Frogs Hair on 2011-09-04
All I have ever had to do was download the Opera .deb package from the site , right click and install with the Gdebi package installer , which is in the software center .

The Opera stable source will be  added to the software sources during installation and Opera will update automatically . I have not used the terminal for installing Opera on past 3 Ubuntu releases .

---

### Post by Zill on 2011-09-04
The [OperaBrowser Community Documentation]("https://help.ubuntu.com/community/OperaBrowser") should help clarify things.

---

### Post by stinkeye on 2011-09-04
> **Frogs Hair said:**
> All I have ever had to do was download the Opera .deb package from the site , right click and install with the Gdebi package installer , which is in the software center .

The Opera stable source will be  added to the software sources during installation and Opera will update automatically . I have not used the terminal for installing Opera on past 3 Ubuntu releases .

Yes same here, but I installed  Ocelot 11.10 on another drive and the 
downloaded Opera deb fails to install with Gdebi or the Software Centre.
The same deb installs on Natty no problem.
Also debs for other progams I've copied over from Natty install no problem on Ocelot

---

### Post by 3lud13 on 2011-09-04
ok so opera is now installed not sure when this happened but its now there found it after typing opera into the terminal

---

### Post by ruario on 2011-10-18
This was/is the problem: [http://my.opera.com/community/forums/findpost.pl?id=10564932](http://my.opera.com/community/forums/findpost.pl?id=10564932)

---

### Post by MonolithImmortal on 2011-10-18
> And what about dpkg and apt? They work because they use xz to open it since the xz compression format is actually a continuation of the LZMA compression format. In fact if you setup a /usr/bin/lzma as a symlink pointing to /usr/bin/xz even Software Centre can open the Opera packages. So the bug is with Software Centre because unlike the lower level command line utilities it doesn't realise that it doesn't need the lzma executable, xz will do just fine!
Interesting.

---

### Post by billstei on 2011-10-18
Install the lzma package.  This "bug" is being tracked/fixed here: [https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/868188)

---

### Post by mc4man on 2011-10-18
the same affects chrome-browser & also gdebi
So for example  on 11.10 gdebi won't install chrome-browser  but just installing lzma fixes

---

### Post by MonolithImmortal on 2011-10-18
So is this thread solved?

---

### Post by ruario on 2011-10-19
Should be. By the way we (I am an Opera employee) are going to switch back to bzip2 comression within our debs for our next release, until the issue with Software Center is resolved.

---

### Post by ruario on 2011-10-19
Ok, we released Opera 11.52, which uses bzip2 compression for now and fixes a security issue.

---

### Post by stinkeye on 2011-10-19
Thanks just downloaded and installed with gdebi.

---

