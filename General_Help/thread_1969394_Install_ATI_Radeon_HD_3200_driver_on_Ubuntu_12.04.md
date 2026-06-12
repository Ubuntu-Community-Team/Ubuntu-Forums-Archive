---
title: "Install ATI Radeon HD 3200 driver on Ubuntu 12.04"
date: 2012-04-30
forum: General Help
---

### Post by pakoelchako on 2012-04-30
[SIZE=3]The title is pretty much what I want to know, how can I install the driver for the aforementioned card on the latest version of Ubuntu? Thanks for your help.[/SIZE]

---

### Post by cottfcfan on 2012-04-30
You can do 2 things.
1. Search for additional drivers in the dash, & install what it offers, or
2. Go to the AMD web site:
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
and manually download & install the Driver.
To do this you will have to read the release notes carefully, and be a bit Linux savy, but its not to difficult.

ps if you use the 2nd option, you will have to enter the directory where you downloaded the driver 1st, and also run as root "sudo".

---

### Post by pakoelchako on 2012-05-28
I've downloaded the correct driver for my card, but I can't seem to install it. It is a .run file and when I open it, gedit opens and gets stuck. :(

---

### Post by cottfcfan on 2012-05-28
You can't just open the file.
You need to run the installation command as per the rellease notes on the download page.
for eg. download the file to your desktop, then open a terminal.
```
cd Desktop
```
then
```
sudo sh ./ati-driver-installer-x86.x86_64.run
```
Then follow the prompts.

---

### Post by GreatDanton on 2012-05-28
Easiest way to install drivers is

(top right)
-System settings
-Additional drivers

choose one and click Activate

---

### Post by NHellFire on 2012-08-09
> **GreatDanton said:**
> Easiest way to install drivers is

(top right)
-System settings
-Additional drivers

choose one and click Activate

That will not work. The current ATI driver only supports the 5000+ series.

> **pakoelchako said:**
> I've downloaded the correct driver for my card, but I can't seem to install it. It is a .run file and when I open it, gedit opens and gets stuck. :(

sudo sh ./amd-driver-installer-12.6-legacy-x86.x86_64.run --buildandinstallpkg Ubuntu/precise
Make sure you have the legacy driver: [http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/legacy/Pages/legacy-radeon_linux.aspx)

It worked for me (until I updated to a 3.4 kernel, so now I'm back on the open-source one).

---

