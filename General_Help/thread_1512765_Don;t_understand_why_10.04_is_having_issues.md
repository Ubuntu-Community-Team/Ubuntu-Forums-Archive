---
title: "Don;t understand why 10.04 is having issues"
date: 2010-06-18
forum: General Help
---

### Post by jrtroberts2 on 2010-06-18
I have tried to get Ubuntu 10.04 to work on a machine for two weeks now.  The version I have installed is the x86_64 version.  On boot I get
nforce2_SMBUS 0000:00:03.2: error probing SMB1
nforce2_SMBUS 0000:00:03.2: error probing SMB2

When I install 9.04 x86_64 I do not get issue
and when I Upgrade to 9.10 x86_64  I do not get the issue.

When I install 10.04 or Upgrade to 10.04 x86_64 the issue starts immediately on reeboot.
There also an issue with the nvidia graphics drivers not working with this release.

There is a bug report here:  
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296)

People on the ubuntu-bugs chat room do no think it is a bug.
I do not know what to think.  All I know is that it only exists under the new release.

Can anyone offer any help?

Joshua

---

### Post by bobcollard on 2010-06-18
> **jrtroberts2 said:**
> I have tried to get Ubuntu 10.04 to work on a machine for two weeks now.  The version I have installed is the x86_64 version.  On boot I get
nforce2_SMBUS 0000:00:03.2: error probing SMB1
nforce2_SMBUS 0000:00:03.2: error probing SMB2

When I install 9.04 x86_64 I do not get issue
and when I Upgrade to 9.10 x86_64  I do not get the issue.

When I install 10.04 or Upgrade to 10.04 x86_64 the issue starts immediately on reeboot.
There also an issue with the nvidia graphics drivers not working with this release.

There is a bug report here:  
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/575296)

People on the ubuntu-bugs chat room do no think it is a bug.
I do not know what to think.  All I know is that it only exists under the new release.

Can anyone offer any help?

Joshua
It is a problem with the Noveau Drivers that is supposed to support all the video drivers but don't.  They said it was fixed, I doubt it.

---

### Post by oldfred on 2010-06-18
For nvidia:

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

