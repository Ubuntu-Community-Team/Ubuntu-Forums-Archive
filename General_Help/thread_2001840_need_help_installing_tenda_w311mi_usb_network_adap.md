---
title: "need help installing tenda w311mi usb network adaptor"
date: 2012-06-11
forum: General Help
---

### Post by the pheonix on 2012-06-11
i need some help installing my new usb network adapter. Make is tenda and model is w311mi. i have searched around on the internet but it seems tenda's page has been taken down and the other forums posts i have read haven't helped. i am a noob when it comes to terminal and such so please explain thoroughly.
Thanks in advance

---

### Post by the pheonix on 2012-06-16
anyone?

---

### Post by strictland on 2012-06-23
I am having the same issue, I have a Tenda W311MI and trying to use on Ubuntu 12.04.

Any help is greatly appreciated.

---

### Post by bupe on 2012-07-27
Try running the below from a terminal ([source/credit1]("http://linuxforums.org.uk/index.php?topic=852.0"), [source/credit2]("http://ubuntuforums.org/showthread.php?t=1800178")):

1. Initial steps (making sure system is up-to-date and finding your kernel version)

```
sudo apt-get update
sudo apt-get upgrade
uname -r

```

The output of the last command for me is:

> 3.2.0-27-generic

We will need this in the next step.

2. Preparing the build environment

```
sudo apt-get install -y build-essentials linux-headers-´uname-r´
```

If you are unable to input the special character ´ then just use the output from the first step, in this case your install line would look like this (using my above example):

```
sudo apt-get install -y build-essentials linux-headers-3.2.0-27-generic
```

3. Downloading and extracting the Ralink driver

Go to [the Ralink driver download page]("http://www.ralinktech.com/en/04_support/support.php?sn=501"). Here get the latest driver (at the time of writing it is called RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB (2.5.0.3).

Extract the driver file and go to its folder. You need to change the os/linux/config.mk file if you want to use WPA/WPA2 encryption (generally it is a good idea). Modify the following lines:

'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'

4. Installing the driver

You need to elevate your priviliges in order to compile and start using the downloaded driver:

```
sudo su
make
make install
modprobe rt5370
```

If you need additinal help I recommend checking credit/source2 above.

---

### Post by bodzan on 2012-07-28
I need help with this also...

When I try to do what bupe suggested in line 2 of his post I get this:
[PHP]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials[/PHP]

What am I to do about this error or should I ignore it?

---

### Post by bodzan on 2012-07-28
Ignore the previous post - I went to bupe's source/credit2 and it did all I needed so now I have wireless connection... :)

Thanx for all help bupe... :)

---

