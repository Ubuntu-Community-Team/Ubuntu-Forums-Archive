---
title: "pmount failed during pam_usb Auth"
date: 2009-08-17
forum: General Help
---

### Post by HuckBerry on 2009-08-17
I hate to start **yet another** pam_usb thread, but I haven't seen any active threads that cover this issue. I installed pam_usb fresh several times and have even gone so far as to remove pmount as well. Here's the issue:

 When I have my USB device inserted, authentication goes as planned: 
> 
me@UbuntuDesktop:~$ pamusb-check me
* Authentication request for user "me" (pamusb-check)
* Device "TimeCapsule" is connected (good).
* Performing one time pad verification...
* Access granted.
But when said device is unmounted (but still inserted) this happens:
> 
me@UbuntuDesktop:~$ pamusb-check me
* Authentication request for user "me" (pamusb-check)
* Device "TimeCapsule" is connected (good).
* Performing one time pad verification...
Error: device /dev/sdc1 is not removable
[COLOR=Red]*[/COLOR] Mount failed
[COLOR=Red]*[/COLOR] Access denied.
Any clue why pmount is failing? The docs for pam_usb states that it can authenticate even when the device isn't mounted. This is important because I cannot login via GDM unless pam_usb can mount the device itself.

Any help is appriciated.

---

### Post by DarkPorpoise on 2009-08-23
Greetings HuckBerry,

I recently had the problem you described. I solved it with help from the comments on this blog post:

[http://highmem.blogspot.com/2008/10/gdm-autologin-when-usb-stick-present.html](http://highmem.blogspot.com/2008/10/gdm-autologin-when-usb-stick-present.html)

Essentially, you can force [FONT="Lucida Console"]**pmount**[/FONT] to allow your device to be automounted by [FONT="Lucida Console"]**pam_usb**[/FONT] by adding the device on a line by itself in [FONT="Lucida Console"]**/etc/pmount.allow**[/FONT]. Since you may attach other removable media before inserting your USB key (e.g. an external hard drive) you can setup a range of device nodes to use:


```
# /etc/pmount.allow
# pmount will allow users to additionally mount all devices that are
# listed here.

/dev/sd[c-h]1
```


This allows the first partition on any device in the range [FONT="Lucida Console"]**dev/sdc**[/FONT] to [FONT="Lucida Console"]**dev/sdh**[/FONT] to be mounted using [FONT="Lucida Console"]**pmount**[/FONT].


Fare thee well!
DarkPorpoise

---

### Post by HuckBerry on 2009-08-23
Thanks, 
  I was aware of a system similar to that (not the range bit though) but I was skeptical of using it because of the fact that I had to allow mounting of all USB drives. I originally had my system set to prompt for a password upon insertion of a USB device, but had to remove it to make pam_usb work. Allowing pmount to mount without permission made the system a even less secure.

**But for anyone who is looking for a solution to the OP, that did the trick**. Worked on the first shot. But does anyone know of any alternatives? 

~Huckle

---

### Post by DarkPorpoise on 2009-08-24
Greetings HuckBerry,

I did some troubleshooting of this problem with an empty [FONT="Lucida Console"]**/etc/pmount.allow**[/FONT] file. Running [FONT="Lucida Console"]**pmount -d**[/FONT] I was able to find the problem (output truncated for brevity):


```
~ $ pmount -d -t ext2 /dev/sdc1
resolved /dev/sdc1 to device /dev/sdc1
mount point to be used: /media/sdc1
no iocharset given, current locale encoding is UTF-8
locale encoding uses UTF-8, setting iocharset to 'utf8'
Cleaning lock directory /var/lock/pmount_dev_sdc1
device_whitelist: checking /etc/pmount.allow...
device_whitlisted(): nothing matched, returning 0
find_sysfs_device: looking for sysfs directory for device 8:145
find_sysfs_device: checking whether /dev/sdc1 is on /sys/block/ram0 (1:0)
...
...
find_sysfs_device: checking whether /dev/sdc1 is on /sys/block/sdc (8:144)
find_sysfs_device: major device numbers match
find_sysfs_device: minor device numbers do not match, checking partitions...
find_sysfs_device: checking whether device /dev/sdc1 matches partition 8:144
[B]find_sysfs_device: checking whether device /dev/sdc1 matches partition 8:145
find_sysfs_device: -> partition matches, belongs to block device /sys/block/sdc
device_removable: could not find a sysfs device for /dev/sdc1[/B]
Error: device /dev/sdc1 is not removable
policy check failed
~ $ 
```


[FONT="Lucida Console"]**pmount**[/FONT] finds a matching block device for [FONT="Lucida Console"]**/dev/sdc1**[/FONT], but there isn't enough information in [FONT="Lucida Console"]**/sys/block/**[/FONT] for it to proceed. Instead of checking the [FONT="Lucida Console"]**removable**[/FONT] flag of the matching hardware block device ([FONT="Lucida Console"]**/sys/block/sdc/removable**[/FONT]) it needs to check the flag of the specific partition ([FONT="Lucida Console"]**/sys/block/sdc1/removable**[/FONT]) which fails because the directory [FONT="Lucida Console"]**/sys/block/sdc1/**[/FONT] does not exist.

This behavior has changed in the latest unstable version ([FONT="Lucida Console"]**0.9.19**[/FONT]). [FONT="Lucida Console"]**pmount**[/FONT] now looks in [FONT="Lucida Console"]**/sys/class/block/**[/FONT] for matching device nodes which, on my system, contains directories for individual partitions on SCSI devices. I don't know how you feel about running testing, but it does seem to fix the problem.

Getting [FONT="Lucida Console"]**pmount**[/FONT] to behave the way it's supposed to and allow mounting of all suitable devices that have [FONT="Lucida Console"]**/sys/class/block/***<device>***/removable**[/FONT] set to [FONT="Lucida Console"]**1**[/FONT] is comparable to having the line [FONT="Lucida Console"]**/dev/sd[a-z][1-99]**[/FONT] set in [FONT="Lucida Console"]**/etc/pmount.allow**[/FONT]. Any removable USB storage media become mountable by the user, which is by design. It's also what allows [FONT="Lucida Console"]**PAM_USB**[/FONT] to authenticate from unmounted media. Run [FONT="Lucida Console"]**pamusb-check --debug me**[/FONT] to see how [FONT="Lucida Console"]**PAM_USB**[/FONT] calls **pmount**. There are some things you can try to help prevent unsafe mounts while still allowing [FONT="Lucida Console"]**PAM_USB**[/FONT] and [FONT="Lucida Console"]**pmount**[/FONT] to work as intended.

You can make sure that no services will automatically mount inserted media insecurely. Essentially, you would have to tell your ssytem that a disk is trusted by manually mounting it or having an authorized service mount it in the background. For instance, [FONT="Lucida Console"]**PAM_USB**[/FONT] matches the UUID of the inserted device with the devices listed in its configuration file, which ensures that it only tries to mount trusted devices.

You can remove other users from the [FONT="Lucida Console"]**plugdev**[/FONT] group, since only members of [FONT="Lucida Console"]**plugdev**[/FONT] can use [FONT="Lucida Console"]**pmount**[/FONT]. Of course, since [FONT="Lucida Console"]**PAM_USB**[/FONT] calls [FONT="Lucida Console"]**pmount**[/FONT] with the credentials of the user trying to authenticate, users of [FONT="Lucida Console"]**PAM_USB**[/FONT] must be in the [FONT="Lucida Console"]**plugdev**[/FONT] group. So, this measure won't work if there are other users on your system whom you want to be able to log in with [FONT="Lucida Console"]**PAM_USB**[/FONT], but you don't trust them to only insert safe media.

Also, it might be possible to use [FONT="Lucida Console"]**pamusb-agent**[/FONT] to turn on your system's password check for inserted USB devices automatically upon unlocking. I'm not sure how that would affect further attempts to authenticate with [FONT="Lucida Console"]**PAM_USB**[/FONT], or if it can even be done, but it might be worth fiddling with the idea.


Fare thee well!
DarkPorpoise


EDIT:
> Of course, since [FONT="Lucida Console"]**PAM_USB**[/FONT] calls [FONT="Lucida Console"]**pmount**[/FONT] with the credentials of the user trying to authenticate, users of [FONT="Lucida Console"]**PAM_USB**[/FONT] must be in the [FONT="Lucida Console"]**plugdev**[/FONT] group.

A quick test revealed that this is only the case *after* the user has been authenticated. When logging in, [FONT="Lucida Console"]**PAM_USB**[/FONT] is able to mount the media regardless of the user's membership in the [FONT="Lucida Console"]**plugdev**[/FONT] group. That makes sense, since [FONT="Lucida Console"]**PAM_USB**[/FONT] cannot run anything as user until that user is authenticated and it must run [FONT="Lucida Console"]**pmount**[/FONT] *before* it can authenticate.

---

### Post by HuckBerry on 2009-08-24
What you say does make sense. I really do need to learn a bit more about how Linux interacts with devices (USB in particular) in order to solve this issue completely. But a as temporary fix I was thinking of turning back on Ubuntu's security feature that prompts for a password in order to mount a device. 

This would require the user to type their password once, but then be free from having to do so for as long as the device is inserted. However this would again disable logging in via device auth, and I could really emulate the same effect by extending the timeout for sudo. So I will instead live wth the lack of security, since I have no real need for it at the moment anyway. It was pure paranoia.

Thanks to everyone in this forum for their great help, this was enither the first nor the last.
~Huckle

---

### Post by Endolith on 2009-10-11
So if I try to pmount a USB device and I get "Error: device /dev/sda1 is not removable", this is a bug?

[https://bugs.launchpad.net/ubuntu/+source/sysfsutils/+bug/281367](https://bugs.launchpad.net/ubuntu/+source/sysfsutils/+bug/281367)

---

