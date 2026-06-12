---
title: "Ubuntu 11.10 64-bit will not print to Samsung after latest kernel upgrade"
date: 2012-01-23
forum: General Help
---

### Post by JCCaIDC on 2012-01-23
I'm running 11.10 64-bit and after updating to the latest kernel (3.0.0-15-generic), I can no longer print to my Samsung SCX-4100 multi-function printer.  

I can still scan without issues, but the printer is stuck in the following state: 
"Processing - Waiting for printer to become available."

Any print jobs that are submitted, including a "test page", just stack up on the queue. I have tried the following steps, but haven't made any progress yet:

1) full reboot - all print jobs remain on the queue, but the printer remains in the "Waiting" state.
2) removed printer and re-installed - after the new printer is installed, the same issue
3) removed and re-install printer drivers - after new drivers are installed, the same issue

I have attached the output of the printer troubleshooter.  Also, I have my system information below.  Please help! :)

_**System information:**_
uname -a 
Linux UbuntuJCC 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

_**Printer driver information**_
samsungmfp-driver   v3.00.90-2
samsungmfp-network  v3.00.90-2
samsungmfp-data     v3.00.90-2
samsungmfp-scanner  v3.00.90-2
Samsung Unified Linux Driver Repository <http://www.bchemnet.com/suldr/>

---

### Post by philinux on 2012-01-23
> **JCCaIDC said:**
> I'm running 11.10 64-bit and after updating to the latest kernel (3.0.0-15-generic), I can no longer print to my Samsung SCX-4100 multi-function printer.  

I can still scan without issues, but the printer is stuck in the following state: 
"Processing - Waiting for printer to become available."

Any print jobs that are submitted, including a "test page", just stack up on the queue. I have tried the following steps, but haven't made any progress yet:

1) full reboot - all print jobs remain on the queue, but the printer remains in the "Waiting" state.
2) removed printer and re-installed - after the new printer is installed, the same issue
3) removed and re-install printer drivers - after new drivers are installed, the same issue

I have attached the output of the printer troubleshooter.  Also, I have my system information below.  Please help! :)

_**System information:**_
uname -a 
Linux UbuntuJCC 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

_**Printer driver information**_
samsungmfp-driver   v3.00.90-2
samsungmfp-network  v3.00.90-2
samsungmfp-data     v3.00.90-2
samsungmfp-scanner  v3.00.90-2
Samsung Unified Linux Driver Repository <http://www.bchemnet.com/suldr/>

Reboot and press the shift key to bring up the grub menu. Select the previous kernel and test your printer. It this works then just use the older kernel for now. And report the bug using :-

```
ubuntu-bug linux
```

---

### Post by lintoon on 2012-01-23
I was just going to recommend the latest Samsung Unified driver so I done a search for it and found this page which may be helpful.

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)

---

### Post by JCCaIDC on 2012-01-23
> **philinux said:**
> Reboot and press the shift key to bring up the grub menu. Select the previous kernel and test your printer. It this works then just use the older kernel for now. And report the bug using :-

```
ubuntu-bug linux
```

Thanks for the quick reply, philinux!

I booted to 3.0.0-14 and all printer functions are normal. :D  I will report the bug as you've suggested.

-JCCaIDC

---

### Post by philinux on 2012-01-23
> **JCCaIDC said:**
> Thanks for the quick reply, philinux!

I booted to 3.0.0-14 and all printer functions are normal. :D  I will report the bug as you've suggested.

-JCCaIDC

Nice, it looks like there could be a kernel regression there.

---

### Post by JCCaIDC on 2012-01-23
> **lintoon said:**
> I was just going to recommend the latest Samsung Unified driver so I done a search for it and found this page which may be helpful.

[http://ubuntuforums.org/showthread.php?t=341621](http://ubuntuforums.org/showthread.php?t=341621)


Thanks lintoon - I've actually been through that thread before (a couple of times) and that is how I got my Samsung multi-function working correctly in the first place.  I had already removed the usb black-listing, etc.

In this case, it seems to be an issue related to the updated kernel.  Booting to the prior kernel version (as a workaround) gets me back to full functionality. I'm opening a bug as suggested by philinux.

-JCCaIDC

---

