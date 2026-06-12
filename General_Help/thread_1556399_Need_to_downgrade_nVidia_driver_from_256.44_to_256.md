---
title: "Need to downgrade nVidia driver from 256.44 to 256.35"
date: 2010-08-19
forum: General Help
---

### Post by Marcelo Ruiz on 2010-08-19
Hi All,

I am having a lot of problems with the nVidia 256.44 drivers: the X server crashes several times a day.
I am wondering if anyone knows a link to download the 256.35 drivers for Lucid x64. I read at some forums that downgrading the video driver solves the issue.
I checked in my /var/cache/apt/archives but the package is not there.
Thanks!

---

### Post by Marcelo Ruiz on 2010-08-19
Nobody? An e-mail will also do the trick! :lolflag:
I hope somebody has the previous version... otherwise we are all fried!!!:D

---

### Post by FahadMKS on 2010-08-19
Go to System >> Administration >> Hardware Drivers and you will have 2 drivers listed there among which one of them is an previous version.

Select that and then restart when completed.

Let me know when it is done.

---

### Post by mc4man on 2010-08-19
Not sure how you were installing the 256.44 in lucid or getting from ect., ect.

If you wanted to manually install the 256.35 then the .run for 64 bit is here
[http://www.nvidia.com/object/linux-display-amd64-256.35-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.35-driver.html)

---

### Post by Marcelo Ruiz on 2010-08-20
@ Fahad

Thanks for your answer, but the old version was not listed there. Maybe because this is a fresh install and the only recommended driver downloaded was the 256.44?

@ mc4man

Thanks for your answer. I installed the driver going to System -> Administration -> Hardware Drivers. I just deactivated the driver. I'm going to manually install 256.35 from the link you provided. Thanks!

---

### Post by Marcelo Ruiz on 2010-08-20
Hi,

Still no luck installing the nvidia driver manually. It gives me one error after another... 
Maybe someone running Lucid X64 with an nVidia graphic card can check /var/cache/apt/archives to see if the deb installer for version 256.35 is there...
Thanks!

Marcelo.

---

### Post by pvrm on 2010-08-22
Hi Marcelo,

I'm having the same problem here.

I have the old driver (256.35).

The new driver seems to be better to see movies and little faster than old one. But it makes the gpu hotter from time to time, I don't know why. 

I'm having a lot of trouble to install the driver manually, and the ppa have only the new driver. Did you asked them to help you with that? I think I saw a Marcelo asking something like this yesterday. 

How can I send it to you? Dropbox? Ubuntu one?

---

### Post by Marcelo Ruiz on 2010-08-22
Hi pvrm,

Thanks for your answer and for trying to help. It would be nice to have the 256.35 deb package. I installed dropbox, so my account is: (marcelo_javier_ruiz@yahoo.com.ar).

I finally managed to downgrade the driver. It was kind of a weird process, cause each time I tried a new solution the drives did not installed completely. It was always something missing (even with the installer from the nVidia site).

The steps I followed are here in case someone needs them:

1 - I removed the UbuntuX Swat Updated from the repositories list (using Ubuntu Tweak) to avoid new updates.

2 - I downloaded all the .deb packages matching my architecture (AMD64) from:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+builds?build_text=&build_state=built](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/+builds?build_text=&build_state=built)

and also the nVidia installer from:

[ftp://download.nvidia.com/XFree86/Linux-x86_64/256.35](ftp://download.nvidia.com/XFree86/Linux-x86_64/256.35)

3 - I installed all the deb packages, reboot the computer, enter into recovery mode, click the cancel button, changed to tty3 (Ctrl+Alt+F3) logged in, went to the Download folder and run the nvidia installer (the name will vary depending on the file you download, that's why I use NVIDIAxxxxxxx) with:
sudo sh NVIDIAxxxxxxx.sh

That was it.
I hope this helps somebody else.

Marcelo.

---

