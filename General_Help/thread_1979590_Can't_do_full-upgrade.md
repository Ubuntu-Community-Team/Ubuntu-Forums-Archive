---
title: "Can't do full-upgrade"
date: 2012-05-13
forum: General Help
---

### Post by oshirowanen on 2012-05-13
After doing the following

    ```
Downloaded the 64bit Ubuntu 10.04.4 desktop iso
    Burned to CD (also tried this from a bootable USB drive)
    After installation, I did the following
    sudo aptitude update
    sudo aptitude full-upgrade[/QUOTE]I got the following error:

    [QUOTE]oshirowanen@desktop:~$ sudo aptitude full-upgrade
    [sudo] password for oshirowanen:
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Reading extended state information
    Initialising package states... Done
    The following partially installed packages will be configured:
      linux-generic linux-headers-2.6.32-41-generic linux-headers-generic
      linux-image-2.6.32-41-generic linux-image-generic
    0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
    Need to get 0B of archives. After unpacking 0B will be used.
    Setting up linux-image-2.6.32-41-generic (2.6.32-41.88) ...
    Running depmod.
    update-initramfs: Generating /boot/initrd.img-2.6.32-41-generic
    Running postinst hook script /usr/sbin/update-grub.
    Generating grub.cfg ...
    Found linux image: /boot/vmlinuz-2.6.32-41-generic
    Found initrd image: /boot/initrd.img-2.6.32-41-generic
    Found linux image: /boot/vmlinuz-2.6.32-38-generic
    Found initrd image: /boot/initrd.img-2.6.32-38-generic
    Found memtest86+ image: /boot/memtest86+.bin
    done
    Examining /etc/kernel/postinst.d.
    run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic
    Traceback (most recent call last):
      File "/usr/bin/nvidia-detector", line 8, in <module>
        a = NvidiaDetection(printonly=True)
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __init__
        self.printSelection()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 408, in printSelection
        driver = self.selectDriver()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 328, in selectDriver
        choice = self.driversForCards[self.driversForCards.keys()[0]][0]
    IndexError: list index out of range
    run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
    Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-41-generic.postinst line 1003.
    dpkg: error processing linux-image-2.6.32-41-generic (--configure):
     subprocess installed post-installation script returned error exit status 2
    dpkg: dependency problems prevent configuration of linux-image-generic:
     linux-image-generic depends on linux-image-2.6.32-41-generic; however:
      Package linux-image-2.6.32-41-generic is not configured yet.
    dpkg: error processing linux-image-generic (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of linux-generic:
     linux-generic depends on linux-image-generic (= 2.6.32.41.48); however:
      Package linux-image-generic is not configured yet.
    dpkg: error processing linux-generic (--configure):
     dependency problems - leaving unconfigured
    Setting up linux-headers-2.6.32-41-generic (2.6.32-41.88) ...
    No apport report written because the error message indicates it's a follow-up error from a previous failure.
               No apport report written because the error message indicates it's a follow-up error from a previous failure.
                          Examining /etc/kernel/header_postinst.d.
    run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic
    Traceback (most recent call last):
      File "/usr/bin/nvidia-detector", line 8, in <module>
        a = NvidiaDetection(printonly=True)
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __init__
        self.printSelection()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 408, in printSelection
        driver = self.selectDriver()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 328, in selectDriver
        choice = self.driversForCards[self.driversForCards.keys()[0]][0]
    IndexError: list index out of range
    run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
    Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-41-generic.postinst line 110.
    dpkg: error processing linux-headers-2.6.32-41-generic (--configure):
     subprocess installed post-installation script returned error exit status 2
    No apport report written because MaxReports has already been reached
                                                                        dpkg: dependency problems prevent configuration of linux-headers-generic:
     linux-headers-generic depends on linux-headers-2.6.32-41-generic; however:
      Package linux-headers-2.6.32-41-generic is not configured yet.
    dpkg: error processing linux-headers-generic (--configure):
     dependency problems - leaving unconfigured
    No apport report written because MaxReports has already been reached
                                                                        Errors were encountered while processing:
     linux-image-2.6.32-41-generic
     linux-image-generic
     linux-generic
     linux-headers-2.6.32-41-generic
     linux-headers-generic
    E: Sub-process /usr/bin/dpkg returned an error code (1)
    A package failed to install. Trying to recover:
    Setting up linux-image-2.6.32-41-generic (2.6.32-41.88) ...
    Running depmod.
    update-initramfs: Generating /boot/initrd.img-2.6.32-41-generic
    Running postinst hook script /usr/sbin/update-grub.
    Generating grub.cfg ...
    Found linux image: /boot/vmlinuz-2.6.32-41-generic
    Found initrd image: /boot/initrd.img-2.6.32-41-generic
    Found linux image: /boot/vmlinuz-2.6.32-38-generic
    Found initrd image: /boot/initrd.img-2.6.32-38-generic
    Found memtest86+ image: /boot/memtest86+.bin
    done
    Examining /etc/kernel/postinst.d.
    run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic
    Traceback (most recent call last):
      File "/usr/bin/nvidia-detector", line 8, in <module>
        a = NvidiaDetection(printonly=True)
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __init__
        self.printSelection()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 408, in printSelection
        driver = self.selectDriver()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 328, in selectDriver
        choice = self.driversForCards[self.driversForCards.keys()[0]][0]
    IndexError: list index out of range
    run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
    Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-41-generic.postinst line 1003.
    dpkg: error processing linux-image-2.6.32-41-generic (--configure):
     subprocess installed post-installation script returned error exit status 2
    dpkg: dependency problems prevent configuration of linux-image-generic:
     linux-image-generic depends on linux-image-2.6.32-41-generic; however:
      Package linux-image-2.6.32-41-generic is not configured yet.
    dpkg: error processing linux-image-generic (--configure):
     dependency problems - leaving unconfigured
    Setting up linux-headers-2.6.32-41-generic (2.6.32-41.88) ...
    Examining /etc/kernel/header_postinst.d.
    run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-41-generic /boot/vmlinuz-2.6.32-41-generic
    Traceback (most recent call last):
      File "/usr/bin/nvidia-detector", line 8, in <module>
        a = NvidiaDetection(printonly=True)
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __init__
        self.printSelection()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 408, in printSelection
        driver = self.selectDriver()
      File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 328, in selectDriver
        choice = self.driversForCards[self.driversForCards.keys()[0]][0]
    IndexError: list index out of range
    run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
    Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-41-generic.postinst line 110.
    dpkg: error processing linux-headers-2.6.32-41-generic (--configure):
     subprocess installed post-installation script returned error exit status 2
    dpkg: dependency problems prevent configuration of linux-generic:
     linux-generic depends on linux-image-generic (= 2.6.32.41.48); however:
      Package linux-image-generic is not configured yet.
    dpkg: error processing linux-generic (--configure):
     dependency problems - leaving unconfigured
    dpkg: dependency problems prevent configuration of linux-headers-generic:
     linux-headers-generic depends on linux-headers-2.6.32-41-generic; however:
      Package linux-headers-2.6.32-41-generic is not configured yet.
    dpkg: error processing linux-headers-generic (--configure):
     dependency problems - leaving unconfigured
    Errors were encountered while processing:
     linux-image-2.6.32-41-generic
     linux-image-generic
     linux-headers-2.6.32-41-generic
     linux-generic
     linux-headers-generic
    Reading package lists... Done
    Building dependency tree
    Reading state information... Done
    Reading extended state information
    Initialising package states... Done
    
    oshirowanen@desktop:~$
```Anyone know why this is happening?

---

### Post by zvacet on 2012-05-14
```
sudo dpkg --configure -a
```

---

