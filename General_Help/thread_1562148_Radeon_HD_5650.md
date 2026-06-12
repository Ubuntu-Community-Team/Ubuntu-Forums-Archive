---
title: "Radeon HD 5650"
date: 2010-08-27
forum: General Help
---

### Post by BlaiddDrwg on 2010-08-27
Hello guys,

This is my first post here and I hope I will get the right answer to my question.

I just bought a new laptop that has Radeon 5650 and have been wondering what kind of driver should I install on my Ubuntu x86. There seems to be several options:

1) Official ATI Catalyst™ Display Driver from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx*It](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx*It) was released a few days ago and supports my video card(as shown in the release notes of the driver)

2) I also heard about fglrx

3) Installing the driver from Ubuntu's embedded hardware manager

Which way is the best way?

Thanks in advance

---

### Post by TwoEars on 2010-08-27
Installing via Ubuntu's hardware manager would be the way I recommend, it's most likely to be stable and updated .
fglrx is the ATI driver, so don't worry about that.

If you have issues with the driver installed via the hardware manager, then I suggest you use EnvyNG to install the drivers.

Also, you aren't from Cymru by any chance?

---

### Post by alphacrucis2 on 2010-08-27
> **BlaiddDrwg said:**
> Hello guys,

This is my first post here and I hope I will get the right answer to my question.

I just bought a new laptop that has Radeon 5650 and have been wondering what kind of driver should I install on my Ubuntu x86. There seems to be several options:

1) Official ATI Catalyst™ Display Driver from [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx*It](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx*It) was released a few days ago and supports my video card(as shown in the release notes of the driver)

2) I also heard about fglrx

3) Installing the driver from Ubuntu's embedded hardware manager

Which way is the best way?

Thanks in advance

The Catalyst driver **is** fglrx. The version AMD just released is 10.8. The one in the Ubuntu repos is either 10.4 or 10.5 (I forget which). The way to install the one from the repos is via System - Administration Hardware Drivers. If you don't do that then by default you will have the open source driver. If you decide to install the latest from AMD then carefully read the binary driver howto first.

---

