---
title: "Installing BlueGriffon 10.10"
date: 2011-01-22
forum: General Help
---

### Post by sunnyd47 on 2011-01-22
Is there a walk through to follow anywhere for installation on 10.10? I  am new to Ubuntu and am not sure which version or download extension I  should be using and also if it will auto install.

Any help appreciated.

---

### Post by dcottingham on 2011-01-22
You probably want to visit this page, it gives some guidance on what to download and what then to do with it:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Not sure what you mean by "auto install."

---

### Post by samigina on 2011-01-22
Hes talking abou the BlueGriffon installation (a kompozer fork)...

You should install the .deb version thats the autoinstall option, just double clik it.

[http://www.bluegriffon.org/freshmeat/nightlies/latest/BlueGriffon-0.8.1-Linux-x86.deb](http://www.bluegriffon.org/freshmeat/nightlies/latest/BlueGriffon-0.8.1-Linux-x86.deb)

---

### Post by sunnyd47 on 2011-01-22
> **samigina said:**
> Hes talking abou the BlueGriffon installation (a kompozer fork)...

You should install the .deb version thats the autoinstall option, just double clik it.

[http://www.bluegriffon.org/freshmeat/nightlies/latest/BlueGriffon-0.8.1-Linux-x86.deb](http://www.bluegriffon.org/freshmeat/nightlies/latest/BlueGriffon-0.8.1-Linux-x86.deb)

Thanks samigina. I have done that and run the installer but I caanot find it anywhere on my Ubuntu system to run it. The files appear to be located within Home> downloads> bluegriffon and they are extracted but thats it, what do I have to do next as it is not in Applications> Programming to run it.

---

### Post by samigina on 2011-01-23
Press ALT+F2 and try typing bluegriffon...

---

### Post by sunnyd47 on 2011-01-27
> **samigina said:**
> Press ALT+F2 and try typing bluegriffon...

Done that and the error states "no such file or directory".

> **samigina said:**
> Hes talking abou the BlueGriffon installation (a kompozer fork)...

You should install the .deb version thats the autoinstall option, just double clik it.

[http://www.bluegriffon.org/freshmeat/nightlies/latest/BlueGriffon-0.8.1-Linux-x86.deb](http://www.bluegriffon.org/freshmeat/nightlies/latest/BlueGriffon-0.8.1-Linux-x86.deb)

Did this too, the "BlueGriffon-0.8.1-Linux-x86_64-Install" is in "downloads" but cannot get it to run still. Is there a different version as it states 64 and my comp is a 32 bit (or is this not what the 64 refers to?)

---

### Post by jalmado on 2011-03-13
In order to install the "BlueGriffon-0.9-Linux-x86-Install" file, righ-click on it, then "properties", then "permissions", and then tick the box "Allow to execute the file as a programme". Then double click on the file and it will install.

---

### Post by lykeion on 2011-03-13
Reading comments on the BlueGriffon webpage it seems that the 10.04 deb package is corrupted and trying it out it doesn't install. The 10.10 installer seems to be broken as well. After downloading it, making it executable and running it in a terminal I get error message "cannot execute binary file". Trying to run the installer as root (made me really nervous since it seems so buggy) doesn't work either.

They use bugzilla and have a google group. Maybe you can get more help there. Personally I wouldnt bother with buggy software like that.

---

### Post by VANZWAY on 2011-04-13
This is how I got it working on **Ubuntu 10.10**:

**Install dependencies:**

sudo apt-get build-dep firefox
sudo apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev libxt-dev libiw-dev mesa-common-dev autoconf2.13 yasm

**Download and install the most recent binary, for your hardware platform (ie. 64/32-bit):**

[http://bluegriffon.org/pages/Download](http://bluegriffon.org/pages/Download)

Install the .deb (by double clicking the file, using synaptic or using dpkg terminal command)

Note: tested with Bluegriffon 0.9.1

**Launch the program:**

The program files are located in /usr/local/bin/bluegriffon.

run the script called bluegriffon by double clicking it (or running ./bluegriffon from that directory in the terminal)

---

### Post by Cfossy2 on 2011-08-11
> **VANZWAY said:**
> This is how I got it working on **Ubuntu 10.10**:

**Install dependencies:**

sudo apt-get build-dep firefox
sudo apt-get install mercurial libasound2-dev libcurl4-openssl-dev libnotify-dev libxt-dev libiw-dev mesa-common-dev autoconf2.13 yasm

**Download and install the most recent binary, for your hardware platform (ie. 64/32-bit):**

[http://bluegriffon.org/pages/Download](http://bluegriffon.org/pages/Download)

Install the .deb (by double clicking the file, using synaptic or using dpkg terminal command)

Note: tested with Bluegriffon 0.9.1

**Launch the program:**

The program files are located in /usr/local/bin/bluegriffon.

run the script called bluegriffon by double clicking it (or running ./bluegriffon from that directory in the terminal)




I followed the instructions from this website which worked quite well in Narwal. Just used the nightly build, and was able to install and run the BlueGriffon website designer.
[http://www.webupd8.org/2011/01/bluegriffon-new-wysiwyg-editor-which.html](http://www.webupd8.org/2011/01/bluegriffon-new-wysiwyg-editor-which.html)

---

### Post by stafio on 2011-08-16
There is a [package available on the GetDeb site]("http://www.getdeb.net/software/BlueGriffon").

---

### Post by cmcanulty on 2011-08-29
I am also trying to install it. I can't find a .deb file. Do I download the installer or the .tar file? The getdeb site mentioned has a version for 10.04 ans 11.04 but nothing for 10.10. I installed the above dependencies already.Oh sorry I got it now.

---

### Post by Eripio on 2013-02-03
> **sunnyd47 said:**
> Is there a walk through to follow anywhere for installation on 10.10? I  am new to Ubuntu and am not sure which version or download extension I  should be using and also if it will auto install.

Any help appreciated.
Hi,
unpack the tarball, you will get a folder with all the program files in it. Look for a Shell-Script "bluegriffon" inside the program folder, create a symbolic link of that script and place the link on your desktop. Click the script, a pop up window will ask what you want to to do. click on "Run" ....

---

### Post by Bucky Ball on 2013-02-03
***Thread Closed***

Necromancy. This thread is nearly a year and a half dead and inactive. A lot has changed since then; 10.10 is no longer supported for a start.

Welcome to the forums. ;)

---

