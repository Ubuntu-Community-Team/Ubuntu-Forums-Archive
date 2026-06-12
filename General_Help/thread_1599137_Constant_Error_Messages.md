---
title: "Constant Error Messages"
date: 2010-10-17
forum: General Help
---

### Post by HoodedHooligan on 2010-10-17
I keep getting errors with almost everything I do in Ubuntu. I barely got the Ubuntu to install and now everytime I update or everytime I download something from the software center, I get error messages.

example:

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 134560 files and directories currently installed.)
Preparing to replace linux-libc-dev 2.6.35-1022.33 (using .../linux-libc-dev_2.6.35-1022.34_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace linux-headers-2.6.35-22 2.6.35-22.33 (using .../linux-headers-2.6.35-22_2.6.35-22.34_all.deb) ...
Unpacking replacement linux-headers-2.6.35-22 ...
Preparing to replace linux-headers-2.6.35-22-generic 2.6.35-22.33 (using .../linux-headers-2.6.35-22-generic_2.6.35-22.34_i386.deb) ...
Unpacking replacement linux-headers-2.6.35-22-generic ...
Preparing to replace nvidia-current 260.19.06-0ubuntu1 (using .../nvidia-current_260.19.12-0ubuntu1~xup1_i386.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
Preparing to replace linux-image-2.6.35-22-generic 2.6.35-22.33 (using .../linux-image-2.6.35-22-generic_2.6.35-22.34_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Preparing to replace tzdata-java 2010l-1 (using .../tzdata-java_2010m-0ubuntu0.10.10_all.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2010l-1 (using .../tzdata_2010m-0ubuntu0.10.10_all.deb) ...
Unpacking replacement tzdata ...
Processing triggers for man-db ...
Setting up tzdata (2010m-0ubuntu0.10.10) ...

Current default time zone: 'America/New_York'
Local time is now:      Sun Oct 17 12:03:55 EDT 2010.
Universal Time is now:  Sun Oct 17 16:03:55 UTC 2010.
Run 'dpkg-reconfigure tzdata' if you wish to change it.

(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 134562 files and directories currently installed.)
Preparing to replace intel-gpu-tools 1.0.2+git20100324-0ubuntu1 (using .../intel-gpu-tools_1.0.2+git20100830+c935c60-0ubuntu0sarvatt_i386.deb) ...
Unpacking replacement intel-gpu-tools ...
Preparing to replace libvte-common 1:0.26.0-0ubuntu1 (using .../libvte-common_1%3a0.26.0-0ubuntu2_all.deb) ...
Unpacking replacement libvte-common ...
Preparing to replace libvte9 1:0.26.0-0ubuntu1 (using .../libvte9_1%3a0.26.0-0ubuntu2_i386.deb) ...
Unpacking replacement libvte9 ...
Preparing to replace nvidia-current-modaliases 260.19.06-0ubuntu1 (using .../nvidia-current-modaliases_260.19.12-0ubuntu1~xup1_i386.deb) ...
Unpacking replacement nvidia-current-modaliases ...
Preparing to replace nvidia-settings 260.19.06-0ubuntu1 (using .../nvidia-settings_260.19.12-0ubuntu1~xup_i386.deb) ...
Unpacking replacement nvidia-settings ...
Preparing to replace python-vte 1:0.26.0-0ubuntu1 (using .../python-vte_1%3a0.26.0-0ubuntu2_i386.deb) ...
Unpacking replacement python-vte ...
Preparing to replace xserver-xorg-video-radeon 1:6.13.1-1ubuntu5 (using .../xserver-xorg-video-radeon_1%3a6.13.2-0ubuntu1~xup1_i386.deb) ...
Unpacking replacement xserver-xorg-video-radeon ...
Preparing to replace xserver-xorg-video-ati 1:6.13.1-1ubuntu5 (using .../xserver-xorg-video-ati_1%3a6.13.2-0ubuntu1~xup1_i386.deb) ...
Unpacking replacement xserver-xorg-video-ati ...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up linux-libc-dev (2.6.35-1022.34) ...
Setting up linux-headers-2.6.35-22 (2.6.35-22.34) ...
Setting up linux-headers-2.6.35-22-generic (2.6.35-22.34) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic        
 *       nvidia-173 (173.14.28)...        
[fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Setting up nvidia-173 (173.14.28-0ubuntu1) ...
Removing old nvidia-173-173.14.28 DKMS files...

------------------------------
Deleting module version: 173.14.28
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-173-173.14.28 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-173/173.14.28/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-173.0.crash'
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
Setting up nvidia-current (260.19.12-0ubuntu1~xup1) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-260.19.12 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/260.19.12/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
No apport report written because MaxReports is reached already
Setting up linux-image-2.6.35-22-generic (2.6.35-22.34) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-22.33 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
 * dkms: running auto installation service for kernel 2.6.35-22-generic        
 *       nvidia-173 (173.14.28)...        
[fail]
 *       nvidia-current (260.19.12)...        
[fail]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up tzdata-java (2010m-0ubuntu0.10.10) ...
Setting up intel-gpu-tools (1.0.2+git20100830+c935c60-0ubuntu0sarvatt) ...
Setting up libvte-common (1:0.26.0-0ubuntu2) ...
Setting up libvte9 (1:0.26.0-0ubuntu2) ...
Setting up nvidia-current-modaliases (260.19.12-0ubuntu1~xup1) ...
Setting up nvidia-settings (260.19.12-0ubuntu1~xup) ...
Setting up python-vte (1:0.26.0-0ubuntu2) ...
Setting up xserver-xorg-video-radeon (1:6.13.2-0ubuntu1~xup1) ...
Setting up xserver-xorg-video-ati (1:6.13.2-0ubuntu1~xup1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-173
 nvidia-current
Setting up nvidia-173 (173.14.28-0ubuntu1) ...
Removing old nvidia-173-173.14.28 DKMS files...

------------------------------
Deleting module version: 173.14.28
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-173-173.14.28 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-173/173.14.28/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-173.0.crash'
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up nvidia-current (260.19.12-0ubuntu1~xup1) ...
update-initramfs: deferring update (trigger activated)
Removing old nvidia-current-260.19.12 DKMS files...

------------------------------
Deleting module version: 260.19.12
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-260.19.12 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/260.19.12/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
   report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggError! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/260.19.12/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processinstalleding nvidia-current (--configure):
 subprocess installed post-instalProcessing triggers for python-support ...

---

### Post by HoodedHooligan on 2010-10-17
Im sorry for such a long post, Ubuntu disabled my keyboard randomly.
Back to my problem: Every since I moved from 8.04 I have had errors but never as bad as with 10.04 and 10.10. I dont know if there is even a way to fix.

---

### Post by digitaltc on 2010-10-19
> **HoodedHooligan said:**
> Im sorry for such a long post, Ubuntu disabled my keyboard randomly.
Back to my problem: Every since I moved from 8.04 I have had errors but never as bad as with 10.04 and 10.10. I dont know if there is even a way to fix.

I had this same error.
Open up your terminal and type in ```
sudo dpkg-reconfigure tzdata

```
enter your password then choose **US**, then **Eastern** since I see you have America/New_York in your setting.
Once that's done, you can resume your update.

---

