---
title: "Is there a program that will tell me what hardware I have install on my laptop?"
date: 2010-11-06
forum: General Help
---

### Post by grs on 2010-11-06
Is there any application/tool that will give me a read out of the make and model of hardware I have on my laptop?
I'm using Ubuntu 10.10.
In windows it would be device manager or speccy.

Also, is there any way of allow Ubuntu to automatically install updates once it has them downloaded?
At the moment it asks for a password every time to install

---

### Post by ki4jgt on 2010-11-06
I'm not really tech savvy, but most of the time when I need that info I use ls*** example lsusb will tell you all the usb deviced hooked up to your computer and the harware your computer uses.

sorry, silly me. Terminal command.

---

### Post by btindie on 2010-11-06
There's a few tools you can use depending on what information you require - dmidecode, lspci, lsusb, /proc/cpuinfo. Not that I've used it but there's a program called gnome-device-manager that might provide the information you require.

dmidecode is a really powerful program and needs to be run sudo root, it provides you with a lot of low level information about your hardware.

---

### Post by sikander3786 on 2010-11-06
I don't know about any gui tool specifically but terminal commnads as mentioned already can do the job for you. e.g,

```
sudo lshw
```

See the man pages for lshw as it is a very powerful command with many oppurtunities like it can save the output to an html file if you want to, give the output for certain hardware etc.

Regarding updates, it needs password to start downloading the files but installs them automatically. And it is better/wise to let it ask your password as it makes the system secure.

---

### Post by bapoumba on 2010-11-06
gnome-device manager is what you are looking for (needs to be installed first, as it is not shipped by default).

---

### Post by linux-hack on 2010-11-06
or you can always take a profit of the power of the terminal...

commands like ..dmesg,lspci,lsusb,dmidecode ... etc...

---

### Post by grs on 2010-11-06
Thanks for the advice.

Just installed device manager, was I was after was the brand of track pad it uses but it doesn't seem to list it, I'll have a closer look though

As for the updates you are right, it looks for the new updates and then tells me what they are then asks for the password to download and install. When you talk about security how does removing that password make it less secure?

---

### Post by oldfred on 2010-11-06
If you want to be like windows then you can let all the virus' be installed in the background. Security is several things. One is confirming that you are installing an application (not something running in background). Others are the permissions and ownership, but once at root you have permission and ownership.

I like this version:
HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

 udevadm info --export-db > file.txt

sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

