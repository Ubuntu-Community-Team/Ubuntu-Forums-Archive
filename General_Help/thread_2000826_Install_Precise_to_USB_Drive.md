---
title: "Install Precise to USB Drive"
date: 2012-06-10
forum: General Help
---

### Post by jimmac49 on 2012-06-10
Hi All,
Having done full install of Ubuntu on USB Drives since 9.04, and indeed the latest Mint Distro, why can't I install 12.04 to my Kingston G3 Data Traveler USB Drive, the install goes through everything as installing to a normal hard drive, but at the end it states "failed to install grub" fatal error.
I run Lucid from from a similar drive as above, and have done from when 10.04 was released, without any installation problems.

As always all help, suggestions or ideas greatly appreciated.

jimmac49

---

### Post by ajgreeny on 2012-06-10
Some thoughts and suggestions:-

[LIST=1]
[*]Is the iso file you used good; did you check the md5sum?
[*]Did you burn the CD or make the live USB properly?
[*]Have you tried installing grub separately from the install?  You can do that by running the live system then using command ```
sudo grub-install /dev/sdx
```where sdx is the USB disk.
[/LIST]

---

### Post by roelforg on 2012-06-10
> **ajgreeny said:**
> Some thoughts and suggestions:-

[LIST=1]
[*]Is the iso file you used good; did you check the md5sum?
[*]Did you burn the CD or make the live USB properly?
[*]Have you tried installing grub separately from the install?  You can do that by running the live system then using command ```
sudo grub-install /dev/sdx
```where sdx is the USB disk.
[/LIST]


I think the OP's installing on USB drives using the same method you'd use for a normal hdd.

I prefer doing this stuff by hand though. (I don't trust automated tools to configure my often peculiar setups) I'm doing an install to usb myself right now and on this computer, I'm at installing the gui (it never seazes to amaze me how big the sheer volume of packages is for that).

---

### Post by sudodus on 2012-06-10
I have done what I think you want to do (and I have done it with 12.04).

- What is the size of your Kingston USB drive? Maybe it is too small.

- Have you checked that your USB drive is good, that there are no bad sectors (problems to read/write)? The lifetime is limited on USB pen-drives, particularly much fewer write cycles than on HDDs (or SSDs).

- It is a good idea to remove the internal HDD, so that there will be no confusion where to install the system and grub.

---

