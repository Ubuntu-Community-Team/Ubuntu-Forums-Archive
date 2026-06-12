---
title: "Highspeed USB issues"
date: 2010-11-22
forum: General Help
---

### Post by ivanovnegro on 2010-11-22
After some googling I found out that there might be a problem with highspeed external USB drives in Linux in general.
Im using Ubuntu 10.10 32 bit and have now this problem I think. My external hard drive is working fine but when I type dmesg in a terminal I can see message errors that appear randomly with all my external hard drives.
The problem is now, I have all my music on this drive and randomly I will have hangs while listening to music and the performance while tranferring data between my notebook and the USBs is poor.
Anybody know a workaround for this problem or have the same experience or have more details about it? I would appreciate it as this problem becomes really annoying in my case.
My principle USB device that I use is an iOmega 500 GB what I use on my Compaq 6730s.
The other USB device is a Toshiba 1 TB.
I tried to transfer the files into my homefolder to avoid this problem but there is no chance as on my notebook is no more space.

---

### Post by lmarmisa on 2010-11-22
I do not have your problem. Try to post some of these error messages. This could help to identify your problem more accurately.

---

### Post by ivanovnegro on 2010-11-22
> **lmarmisa said:**
> I do not have your problem. Try to post some of these error messages. This could help to identify your problem more accurately.

For example the output of dmesg | tail:
```
[ 4650.313649] sd 7:0:0:0: [sdc] Mode Sense: 00 00 00 00
[ 4650.313656] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4650.322457] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4650.322476]  sdc:
[ 4650.582547] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[ 4650.582560] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[ 5696.232556] WARNING! power/level is deprecated; use power/control instead
[ 5696.316769] usb 2-1: USB disconnect, address 4
[21580.112538] usb 2-6: reset high speed USB device using ehci_hcd and address 3
[24478.160588] usb 2-6: reset high speed USB device using ehci_hcd and address 3
```

---

### Post by lmarmisa on 2010-11-22
Is your Iomega USB drive powered through the USB connection?.

---

### Post by ivanovnegro on 2010-11-22
No, its powered via electrical connection.

---

### Post by lmarmisa on 2010-11-22
Some kind of problem is detected in your USB interface and then a reset procedure is started.

The references I have found are related to old versions of kernel, old hardware or problems with cable or power:

[http://www.linuxquestions.org/questions/slackware-14/usb-external-hd-issue-reset-high-speed-usb-device-using-ehci_hcd-545519/](http://www.linuxquestions.org/questions/slackware-14/usb-external-hd-issue-reset-high-speed-usb-device-using-ehci_hcd-545519/)

Try to check if the problem occurs with both USB hard drives. Copy one or several huge files from/to the USB drive(s) in order to check if the frequency of the problem increases with high USB traffic.

---

### Post by ivanovnegro on 2010-11-22
> **lmarmisa said:**
> Some kind of problem is detected in your USB interface and then a reset procedure is started.

The references I have found are related to old versions of kernel, old hardware or problems with cable or power:

[http://www.linuxquestions.org/questions/slackware-14/usb-external-hd-issue-reset-high-speed-usb-device-using-ehci_hcd-545519/](http://www.linuxquestions.org/questions/slackware-14/usb-external-hd-issue-reset-high-speed-usb-device-using-ehci_hcd-545519/)

Try to check if the problem occurs with both USB hard drives. Copy one or several huge files from/to the USB drive(s) in order to check if the frequency of the problem increases with high USB traffic.

Thank you for your help. On this site I was also. 
I have the actual Kernel for Ubuntu 10.10. The problem occurs with both drives, different cables, the problem is identical. I tried everything, with an amount of data the performance slows down dramatically and the CPU usage is exploding always but I have not always the error messages, like I said, its randomly.
It happens with the one year old iOmega and with the new Toshiba drive, in Windows XP they are working without glitches.
I know some people having the same issues.
The drives are both NTFS, could this be the issue maybe?

---

### Post by ivanovnegro on 2010-11-30
Im hoping that some people around here can help me on this issue.
Still have this problem, I cannot be the only one.

---

### Post by ivanovnegro on 2010-12-13
Ok, what would happen if I format my external hard drive from the NTFS file system to ext4? Would I maybe have a better performance? I am only using Linux, so it would not be a problem that it is not compatible with Windows.

---

