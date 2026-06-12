---
title: "Simple-scan freezes in Ubuntu i64 but not Ubuntu i32 while talking to an HP4570C USB"
date: 2011-02-07
forum: General Help
---

### Post by bdudek on 2011-02-07
Hello,

When running simple-scan in Ubuntu 10.10 i64 it freezes after about 10% of the scan and produces this error:

$ simple-scan 
[hp5590] hp5590_get_ack: USB-in-USB: not accepted (status 0) 
[hp5590] hp5590_get_ack: USB-in-USB: not accepted (status 0) 
[hp5590] hp5590_control_msg: USB-in-USB: invalid response received (needed 0000, got 0024) 

** (simple-scan:5202): WARNING **: Unable to start device: Device busy 
[hp5590] hp5590_get_ack: USB-in-USB: error getting acknowledge

BUT WAIT

When the scanner is plugged into the Ubuntu 10.10 i32 machine there is no problem at all. Simple-scan works fine!



Below is the entire process that I followed to create this error with notes and it is repeatable.


Fresh boot of machine

bdudek@bruce:~$ uname -a

Linux bruce 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

bdudek@bruce:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.



found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1305 [hp scanjet scanner], chip=HP4500C/4570C/5500C/5550C/5590/7650) at libusb:002:005

  # Your USB scanner was (probably) detected. It may or may not be supported by

  # SANE. Try scanimage -L and read the backend's manpage.



  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.

bdudek@bruce:~$ simple-scan

[hp5590] hp5590_bulk_read: USB-in-USB: incomplete bulk read (requested 65536 bytes, got 33280 bytes)



** (simple-scan:2638): WARNING **: Unable to read frame from device: Error during device I/O

[hp5590] hp5590_control_msg: USB-in-USB: error sending control message



At this point simple-scan starts the scan and then dies.

Now I run another sane-find-scanner.

bdudek@bruce:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.



found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1305 [hp scanjet scanner], chip=HP4500C/4570C/5500C/5550C/5590/7650) at libusb:002:006

  # Your USB scanner was (probably) detected. It may or may not be supported by

  # SANE. Try scanimage -L and read the backend's manpage.



  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.



The port that the scanner is on seems to have changed? Is this what I am seeing?

First run:
libusb:002:005

Second run:
libusb:002:006



Now I run simple-scan again.

bdudek@bruce:~$ simple-scan

[hp5590] hp5590_get_ack: USB-in-USB: not accepted (status 0)

[hp5590] hp5590_control_msg: USB-in-USB: error getting response

[hp5590] hp5590_control_msg: USB-in-USB: error sending control message



** (simple-scan:2660): WARNING **: Unable to start device: Device busy

[hp5590] hp5590_control_msg: USB-in-USB: error sending control message



simple-scan is not able to talk to the scanner. So I run sane-find-scanner again and get this:

bdudek@bruce:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.



  # No USB scanners found. If you expected something different, make sure that

  # you have loaded a kernel driver for your USB host controller and have setup

  # the USB system correctly. See man sane-usb for details.



  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.

bdudek@bruce:~$ 


Now there are no scanners. Does this look like a sane issue or libusb? For me to get the scanner talking again I have to power cycle it. I know the scanner works because I can plug it into the Ubuntu i32 machine and there is no problem as well as any Windows machine.

---

### Post by bdudek on 2011-02-08
I figured it out... Turns out when running the scanner through a USB 2.0 hub (D-Link DUB-H7) or from the front panel USB inputs it causes the scanner to have communication issues. When directly connected to the USB ports that are mounted on the motherboard in the back there is no issue.

> **bdudek said:**
> Hello,

When running simple-scan in Ubuntu 10.10 i64 it freezes after about 10% of the scan and produces this error:

$ simple-scan 
[hp5590] hp5590_get_ack: USB-in-USB: not accepted (status 0) 
[hp5590] hp5590_get_ack: USB-in-USB: not accepted (status 0) 
[hp5590] hp5590_control_msg: USB-in-USB: invalid response received (needed 0000, got 0024) 

** (simple-scan:5202): WARNING **: Unable to start device: Device busy 
[hp5590] hp5590_get_ack: USB-in-USB: error getting acknowledge

BUT WAIT

When the scanner is plugged into the Ubuntu 10.10 i32 machine there is no problem at all. Simple-scan works fine!



Below is the entire process that I followed to create this error with notes and it is repeatable.


Fresh boot of machine

bdudek@bruce:~$ uname -a

Linux bruce 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

bdudek@bruce:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.



found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1305 [hp scanjet scanner], chip=HP4500C/4570C/5500C/5550C/5590/7650) at libusb:002:005

  # Your USB scanner was (probably) detected. It may or may not be supported by

  # SANE. Try scanimage -L and read the backend's manpage.



  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.

bdudek@bruce:~$ simple-scan

[hp5590] hp5590_bulk_read: USB-in-USB: incomplete bulk read (requested 65536 bytes, got 33280 bytes)



** (simple-scan:2638): WARNING **: Unable to read frame from device: Error during device I/O

[hp5590] hp5590_control_msg: USB-in-USB: error sending control message



At this point simple-scan starts the scan and then dies.

Now I run another sane-find-scanner.

bdudek@bruce:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.



found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x1305 [hp scanjet scanner], chip=HP4500C/4570C/5500C/5550C/5590/7650) at libusb:002:006

  # Your USB scanner was (probably) detected. It may or may not be supported by

  # SANE. Try scanimage -L and read the backend's manpage.



  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.



The port that the scanner is on seems to have changed? Is this what I am seeing?

First run:
libusb:002:005

Second run:
libusb:002:006



Now I run simple-scan again.

bdudek@bruce:~$ simple-scan

[hp5590] hp5590_get_ack: USB-in-USB: not accepted (status 0)

[hp5590] hp5590_control_msg: USB-in-USB: error getting response

[hp5590] hp5590_control_msg: USB-in-USB: error sending control message



** (simple-scan:2660): WARNING **: Unable to start device: Device busy

[hp5590] hp5590_control_msg: USB-in-USB: error sending control message



simple-scan is not able to talk to the scanner. So I run sane-find-scanner again and get this:

bdudek@bruce:~$ sane-find-scanner



  # sane-find-scanner will now attempt to detect your scanner. If the

  # result is different from what you expected, first make sure your

  # scanner is powered up and properly connected to your computer.



  # No SCSI scanners found. If you expected something different, make sure that

  # you have loaded a kernel SCSI driver for your SCSI adapter.



  # No USB scanners found. If you expected something different, make sure that

  # you have loaded a kernel driver for your USB host controller and have setup

  # the USB system correctly. See man sane-usb for details.



  # Not checking for parallel port scanners.



  # Most Scanners connected to the parallel port or other proprietary ports

  # can't be detected by this program.



  # You may want to run this program as root to find all devices. Once you

  # found the scanner devices, be sure to adjust access permissions as

  # necessary.

bdudek@bruce:~$ 


Now there are no scanners. Does this look like a sane issue or libusb? For me to get the scanner talking again I have to power cycle it. I know the scanner works because I can plug it into the Ubuntu i32 machine and there is no problem as well as any Windows machine.

---

### Post by lprofil on 2011-07-12
The same issue here.

I am using a HP Scanjet 5590 on an very old machine. It is a Socket7 AMD Computer with serveral Bios settings for the USB-modes.
There is also legacy-USB support which i disabled. First it seamed that this would do the job but the scanning process still hangs from time to time
which is really anoying when you are scanning more than 1 page.

In my case there is no USB-Hub in the middle. So what can it be?
Any help is appreciated.

Thank you!

/lprofil

---

### Post by bdudek on 2011-07-12
I assume you have tested the scanner on another Linux machine or a Windows machine to verify it works. 

My next step would be to try every USB port on the machine and enable the legacy support again. I have had strange issues with USB ports over the years. I have had machines not boot off a USB thumb drive using the bottom USB port but the top port worked. I would try all the ports and another cable too.

---

### Post by lprofil on 2011-07-13
Hello bdudek,

thanks for your reply!

> **bdudek said:**
> I assume you have tested the scanner on another Linux machine or a Windows machine to verify it works.

Not yet.

The reason i use this scanner under linux is that i do not need any drivers.
On a Windows XP machine it has some weired Internet-Explorer dependancies
and the mess with the driver and the scan software is a p*** in the a**.


> **bdudek said:**
> My next step would be to try every USB port on the machine and enable the legacy support again.

I will try that next time i'm in the office.


> **bdudek said:**
> I have had strange issues with USB ports over the years. I have had machines not boot off a USB thumb drive using the bottom USB port but the top port worked.

The same here. What a coincidence. ;)
 
> **bdudek said:**
> I would try all the ports and another cable too.

Another good hint - thank you.

/lprofil

---

